---
title: "Vender Bitcoin en ventanilla: el lanzamiento de un producto cripto regulado en sucursales suizas"
date: 2026-09-28
author: "Nicolas Cozzarin"
lang: es
ref: crypto-branch-launch
description: "Cómo lideré el lanzamiento de la venta de criptomonedas en las sucursales de una empresa suiza de envío de dinero: el socio, el producto, el cumplimiento normativo y lo que haría distinto."
glance:
  - label: "Rol"
    text: "Product Owner, Union of Financial Corners SA, Ginebra"
  - label: "Producto"
    text: "Los clientes compran Bitcoin o Ethereum en efectivo en la ventanilla y lo reciben en su propia wallet. También pueden vender."
  - label: "Lo que hice"
    text: "Requerimientos, elección del proveedor cripto, backlog con los desarrolladores externos, pruebas, procedimientos de sucursal y capacitación del personal."
  - label: "Lo más difícil"
    text: "Reconocer a cada cliente en todas las sucursales y tener cada control de identidad y cada documento listos para una auditoría."
  - label: "Resultados"
    text: "Funciona en todas las sucursales de Ginebra, Lausana, Berna y Zúrich. Los clientes vuelven seguido a comprar y a vender, en las auditorías estaban los documentos pedidos, y el servicio se está extendiendo a quioscos de socios en toda Suiza."
---

### 1. Contexto

Union of Financial Corners es una empresa de envío de dinero y cambio de divisas en Suiza. La mayor parte de su actividad pasa por las sucursales: la gente viene a la ventanilla para enviar dinero al exterior con Western Union o para cambiar divisas. Es una actividad regulada, que funciona bajo las reglas de la FINMA y la ley suiza de prevención de lavado de dinero.

Se juntaron tres cosas que hicieron de la cripto el siguiente producto lógico. La ley suiza sobre cripto había cambiado, y eso permitía ofrecerla dentro de un marco legal claro. Los clientes la pedían en la ventanilla. Y la empresa buscaba una nueva fuente de ingresos, además de los envíos y el cambio.

Mi trabajo era convertir eso en un producto que el personal pudiera vender todos los días, en cada sucursal, sin generar un riesgo de cumplimiento.

---

### 2. Cómo funciona para el cliente

Del lado del cliente es simple:

1. El cliente viene a la ventanilla y paga en efectivo.
2. Muestra el código QR de su propia wallet y demuestra que la wallet es suya.
3. El personal escanea el código QR y el Bitcoin o el Ethereum se envía a esa wallet.

Los clientes también pueden hacer lo contrario y vender cripto a cambio de efectivo.

Detrás de esos tres pasos hay mucho más: identificar al cliente, controlar el monto contra los límites, decidir qué nivel de KYC corresponde, guardar los documentos y enviar la orden al proveedor cripto. La idea del diseño era que el paso por la ventanilla fuera corto, pero sin que se pudiera saltear ninguno de esos controles.

---

### 3. Mi rol

Fui el Product Owner de este lanzamiento. En la práctica eso significó:

- redactar los requerimientos, desde el flujo del cliente en la ventanilla hasta las reglas de cumplimiento;
- elegir al socio, un proveedor cripto suizo, y ser su contacto desde las primeras reuniones hasta el lanzamiento;
- llevar el backlog con los desarrolladores externos que construyeron la integración;
- probar el flujo completo antes del lanzamiento;
- redactar los procedimientos para las sucursales;
- capacitar al personal de las sucursales.

El proyecto llevó unos diez meses desde el inicio hasta el lanzamiento.

---

### 4. Trabajar con el socio y los desarrolladores

La cripto la ponía un socio, un proveedor cripto suizo, y nuestro sistema tenía que funcionar con el suyo. Elegir ese socio fue una de mis primeras tareas. Después seguí siendo su contacto durante todo el proyecto y acompañé con ellos la integración y las pruebas.

Los desarrolladores también eran externos. Escribí las user stories, mantuve el backlog en orden y probé cada entrega según cómo funciona de verdad una sucursal, con un cliente esperando en la ventanilla.

---

### 5. El cumplimiento normativo dentro del producto

Esto fue el centro del proyecto. Antes del lanzamiento, el producto tenía que demostrar que se respetaban las reglas de la FINMA y los requisitos de prevención de lavado de dinero, y necesitábamos la aprobación de la FINMA.

En la práctica, el producto tenía que resolver:

- la identificación del cliente, con un nivel de KYC que depende del monto;
- los límites de monto;
- el guardado de cada control de identidad y de cada documento;
- los procedimientos de prevención de lavado de dinero para el personal;
- el seguimiento de cada cliente en todas las sucursales.

Lo más difícil fue esto último, junto con los documentos. Un cliente puede comprar en Ginebra un día y en Lausana al siguiente. Si cada sucursal solo ve sus propias operaciones, los límites y los niveles de KYC pierden sentido. Por eso teníamos que reconocer al mismo cliente en cualquier sucursal y tener todos sus documentos guardados de forma que pudiéramos mostrarlos en cualquier momento si había una auditoría.

Yo era el responsable de ese seguimiento y de controlar que se hiciera bien, también fuera del caso normal, por ejemplo con un cliente que vuelve en otra ciudad.

---

### 6. El despliegue en las sucursales

Lanzamos el servicio en todas nuestras sucursales de Ginebra, Lausana, Berna y Zúrich. En cada sucursal, el personal tenía que conocer el nuevo flujo, los nuevos procedimientos y, sobre todo, por qué importaban los pasos de cumplimiento.

La capacitación es lo que cambiaría. Expliqué el producto como yo lo entendía, con todos los detalles de las reglas. Para muchos agentes fue demasiado de una vez. La próxima vez empezaría por lo básico y explicaría con palabras muy simples las pocas cosas que de verdad importan: quién es el cliente, si la wallet es suya, qué límite corresponde y qué documento hay que guardar. El resto puede venir después.

---

### 7. Resultados

No tengo cifras exactas para compartir, pero las señales fueron claras:

- Los clientes volvían seguido a comprar cripto, y también a venderla.
- En las auditorías teníamos los documentos que nos pidieron.
- El servicio sigue funcionando hoy.
- Se está extendiendo a quioscos de socios en toda Suiza.

En un producto regulado, la auditoría importa tanto como las ventas. Un producto que vende bien pero no puede mostrar sus documentos es un riesgo para toda la empresa.

---

### 8. Lo que aprendí

- En una actividad regulada, el cumplimiento es parte del producto. El seguimiento entre sucursales no fue una función agregada al final; definió cómo funcionaba todo el sistema.
- La capacitación tiene que empezar simple. Explicar menos, pero bien, nos habría ahorrado tiempo al personal y a mí.
