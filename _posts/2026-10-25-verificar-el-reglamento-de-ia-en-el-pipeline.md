---
title: "Verificar el Reglamento europeo de IA en el pipeline de despliegue: mi trabajo final de grado"
date: 2026-10-25
author: "Nicolas Cozzarin"
lang: es
ref: ai-act-validator
description: "Un validador que verifica cinco controles del Reglamento europeo de IA en cada versión nueva de un modelo de crédito, mide la equidad y frena el despliegue si una regla no se cumple."
glance:
  - label: "Contexto"
    text: "Trabajo final de grado (prototipado tecnológico), Licenciatura en Inteligencia Artificial y Robótica, Universidad Siglo XXI, 2026. Trabajé solo y cumplí los tres roles de Scrum."
  - label: "Problema"
    text: "El cumplimiento de los modelos de IA se verifica a mano, al final del desarrollo, y cada versión nueva repite toda la revisión."
  - label: "Qué construí"
    text: "Un validador que corre como una etapa del pipeline de GitLab CI del cliente. Arma la ficha de cada versión del modelo como un grafo RDF, mide la equidad con Fairlearn, verifica cinco controles del Reglamento con reglas SHACL en GraphDB y frena el despliegue si alguno no se cumple."
  - label: "Estado"
    text: "Prototipo funcionando. En una primera ejecución, la versión 1 de un modelo de crédito de prueba cumplió las cinco reglas y la versión 2 quedó bloqueada por la regla de equidad. La evaluación frente a la revisión manual se hace en noviembre de 2026."
  - label: "Prototipo"
    text: "Ver las tres pantallas con los datos de una ejecución real"
    url: "https://nicolas-cozzarin.github.io/validador-prototipo/"
---

### 1. El problema

El Reglamento europeo de IA les pide a los proveedores de sistemas de alto riesgo que documenten sus modelos, guarden registros de eventos, prevean supervisión humana y examinen sus datos para detectar sesgos. Un modelo que decide si una persona puede acceder a un crédito es de alto riesgo (Anexo III, punto 5, letra b). Para los modelos de crédito, estas obligaciones se aplican desde diciembre de 2027.

Los modelos cambian rápido. Un equipo puede poner una versión nueva en producción en pocas horas. Los controles de cumplimiento no siguen ese ritmo: alguien revisa la documentación con una checklist al final del desarrollo, y toda la revisión empieza de nuevo con cada versión. Dos auditores pueden leer el mismo criterio de forma distinta, y después cuesta saber por qué se aprobó una versión.

Hay herramientas que ayudan. Las Tarjetas de Modelo, las Hojas de Datos y las plantillas de TechOps ordenan la documentación, pero las completan personas y nada las verifica. Las plataformas de gobernanza como Credo AI u OneTrust conocen el Reglamento, pero trabajan con cuestionarios y revisión humana. Open Policy Agent puede frenar un despliegue, pero no trae reglas del Reglamento. Quise juntar las dos cosas: controles del Reglamento que corren solos en el pipeline y pueden frenar un despliegue.

El caso es modelado. ComplianceTech Europa es una consultora ficticia de París que audita modelos de IA para bancos, y el Banco Aurora es un cliente ficticio con un modelo de crédito. Sus detalles son supuestos míos, y lo digo en el trabajo.

---

### 2. Qué hace el validador

Cuando el banco publica una versión nueva de su modelo de crédito, su pipeline de GitLab CI corre dos jobs antes del despliegue:

1. **fairness-measure** calcula con Fairlearn la diferencia entre la tasa de aprobación de hombres y de mujeres (diferencia de paridad demográfica).
2. **compliance-check** manda la ficha de la versión y el resultado de equidad a GraphDB, que los verifica con cinco reglas SHACL.

Si las cinco reglas se cumplen, el despliegue sigue. Si una falla, el job falla, el despliegue no corre, y el reporte dice qué regla falló, el valor obtenido, el valor esperado y el artículo del Reglamento. Si GraphDB no responde, el job también falla, para que ninguna versión salga sin validar.

Cada ejecución queda guardada en un historial, también las bloqueadas, con su fecha, el resultado de cada regla y la decisión de despliegue.

---

### 3. Las cinco reglas

| Regla | Reglamento de IA | Qué verifica en la ficha |
|---|---|---|
| R1 | Art. 6, apartado 2, y Anexo III, punto 5, letra b | Que la categoría de riesgo declarada coincida con la finalidad. Un modelo de solvencia es de alto riesgo. |
| R2 | Art. 11 y Anexo IV | Que estén cuatro campos: finalidad prevista, datos de entrenamiento, métricas de precisión y limitaciones conocidas. |
| R3 | Art. 12 | Que se declare el registro automático de eventos y dónde se guarda. |
| R4 | Art. 14 | Que se declare una medida de supervisión humana y una persona responsable. |
| R5 | Art. 10, apartado 2, letras f y g | Que la diferencia de paridad demográfica por sexo sea menor o igual a 0,10. |

Estas reglas cubren solo una parte de cada obligación, y quiero ser claro sobre dónde terminan:

- R2, R3 y R4 controlan lo que la ficha **declara**. No controlan que la documentación sea buena, que los registros existan ni que alguien supervise de verdad el modelo. Esa evidencia sigue a cargo de los auditores.
- El Reglamento pide examinar y corregir los sesgos, pero no dice cómo medirlos. La métrica y el umbral de 0,10 son una decisión mía para el caso, para que todos los auditores midan igual. Un valor bajo no prueba que el modelo sea justo: Hardt et al. (2016) mostraron, con puntajes de crédito, que exigir la misma tasa de aprobación puede llevar a aprobar en un grupo a personas que no van a pagar y a rechazar en otro a personas que sí pagarían. Por eso R5 funciona como una señal de alerta.

---

### 4. Decisiones de diseño

**Un grafo en lugar de tablas.** Las reglas prueban relaciones entre los datos. Por ejemplo, la finalidad del modelo implica una categoría de riesgo, y R1 la compara con la que declara la ficha. En RDF eso es un camino en el grafo, y las reglas SHACL se aplican directo sobre él. La estructura de la ficha la adapté de las plantillas de TechOps.

**Guardar las versiones bloqueadas.** GraphDB puede validar SHACL por su cuenta, pero entonces rechaza los datos que no cumplen. Las versiones no conformes no quedarían en el historial, y son justamente las que un auditor más necesita ver. Por eso la validación se hace en un paso aparte y el historial se guarda en un repositorio sin SHACL activado. Ahí se cruzaron mis roles de Product Owner y de desarrollador: el diseño pedía algo que la herramienta no hacía por defecto.

**Sin datos personales en el grafo.** La medición de equidad corre en el pipeline del cliente. Al grafo solo llega el resultado: las tasas por grupo y la diferencia.

**Reglas con versión.** Cada reporte indica qué versión de las reglas se usó. La idea es que la consultora publique reglas nuevas cuando cambie la ley, sin que el cliente toque su pipeline.

---

### 5. Las pantallas

Diseñé las pantallas en Figma y las programé con Streamlit. Son tres:

- **Ejecuciones**, con dos pestañas. *Resultado* muestra el modelo, la versión, una tabla con cada regla (valor obtenido, esperado, base legal y resultado), la tasa de aprobación de hombres y de mujeres, y un botón para descargar el reporte SHACL. *Historial* muestra una fila por validación, con la paridad frente al umbral, el origen (pipeline o manual) y la consulta SPARQL que arma la tabla.
- **Validación manual**, donde un auditor puede validar una ficha sin desplegar nada.
- **Integración**, con los cuatro pasos que sigue un cliente para conectar su pipeline.

**[Ver las pantallas del prototipo](https://nicolas-cozzarin.github.io/validador-prototipo/)**. Es una vista estática con los datos de una ejecución real. El prototipo completo, con validación en vivo, corre en Docker: GraphDB, Streamlit y Caddy para HTTPS.

---

### 6. Primera ejecución

El 25 de octubre de 2026 corrí en mi computadora los mismos pasos que el pipeline del banco, contra GraphDB 10.8, con dos versiones de un modelo de crédito de prueba entrenadas con scikit-learn:

- **Versión 1**: aprueba al 91 % de los hombres y al 93 % de las mujeres. Diferencia: 0,01. Las cinco reglas se cumplen y el despliegue se autoriza.
- **Versión 2**: entrenada con sesgo a propósito. Aprueba al 96 % de los hombres y al 82 % de las mujeres. Diferencia: 0,15. R5 falla, el despliegue se bloquea y el reporte cita el artículo 10.

Los datos vienen del dataset público *Default of Credit Card Clients* (30.000 clientes de un banco de Taiwán, de 2005). Sirve para probar el mecanismo, no para sacar conclusiones sobre el crédito en Europa.

---

### 7. Cómo lo voy a evaluar

Esta primera ejecución muestra que el mecanismo funciona. No muestra que el validador sea confiable. Para eso preparé una prueba, que se hace en noviembre de 2026:

- 20 fichas armadas a propósito: 10 que cumplen las cinco reglas y 10 que violan al menos una. Cada regla se viola en al menos dos fichas. Hay casos límite, como paridades de 0,09, 0,10 y 0,12, y una ficha con dos incumplimientos.
- El resultado esperado de cada ficha se anota en un archivo aparte antes de correr el validador.
- Metas: cero fichas que incumplen autorizadas entre las 10 que violan una regla (el error grave, porque deja pasar un incumplimiento), y como máximo un bloqueo equivocado entre las 10 que cumplen.
- Tiempo: también reviso las mismas 20 fichas a mano con una checklist y comparo la mediana de minutos por ficha. La meta es al menos un 50 % menos de tiempo, solo para estos cinco controles, no para una auditoría completa.

Hay límites. La organización es modelada, y yo armo las fichas, escribo las reglas y tomo el tiempo de las dos revisiones, lo que puede sesgar el resultado.

---

### 8. Lo que me llevo

Lo más difícil fue separar lo que dice la ley de mi interpretación técnica. Para cada regla anoté el artículo, qué verifica en la ficha y un ejemplo de incumplimiento, para que cualquiera pueda rastrear un despliegue bloqueado hasta el texto.

Próximos pasos después de la carrera: una versión que corra en los servidores del cliente, publicar reglas nuevas sin tocar el pipeline del cliente y un reporte descargable que sirva como evidencia. Las reglas también pueden crecer. Empecé por los sesgos que protege la ley, porque un error ahí puede terminar en una sanción, pero otros sesgos, como el especismo en los sistemas de IA (Hagendorff et al., 2023), se podrían sumar de la misma forma.

**Tecnologías:** Python 3.12, RDF y Turtle, SHACL, rdflib, pySHACL, GraphDB 10.8, Fairlearn, scikit-learn, GitLab CI, Streamlit, Docker, Caddy, Figma.
