# Anatomía de una termofijadora

Simulador web en 3D de una prensa térmica de plancha plana de 38 × 38 cm con resistencias intercambiables (modelo de referencia: máquina multifuncional 8 en 1, Freesub Perú, P8038‑RV8). Describe las partes del equipo y reproduce, paso a paso, el estampado por sublimación y el ciclo de transferencia de los productos de la tabla de tiempos y temperaturas del fabricante.

Autor: Mg. Mario Quiroz Martínez · Instituto de Educación Superior “Diseño y Comunicación” (IDC), Lima.

## Archivo

| Archivo | Contenido |
| --- | --- |
| `termofijadora.html` | Página única con HTML, CSS y JavaScript. El logo del IDC está incrustado como imagen PNG en base64. |

## Requisitos

- Navegador con WebGL (Chrome, Edge, Firefox o Safari en versiones actuales).
- Conexión a internet para cargar las bibliotecas y las fuentes:

| Recurso | Versión | Origen |
| --- | --- | --- |
| three.js | 0.186.1 | cdn.jsdelivr.net |
| Anime.js y su adaptador para three.js | 4.5.0 | cdn.jsdelivr.net |
| pdf.js (solo al insertar un arte en PDF) | 3.11.174 | cdnjs.cloudflare.com |
| Barlow Condensed, IBM Plex Sans, IBM Plex Mono, Share Tech Mono | — | Google Fonts |

## Distribución de la pantalla

- Cabecera: logo, título, botón de tema claro u oscuro y datos del modelo de referencia.
- Vista 3D con barra de herramientas: vista general, vista explosionada, ver interior, rótulos, ampliar pantalla, ayuda, recorrido guiado, recursos, sonido, materiales y cámara guiada.
- Paneles sobre la vista 3D (fondo al 15 % de opacidad): lista de partes y lista de materiales.
- Panel lateral con dos pestañas: «Práctica guiada» y «Tabla del fabricante».
- Secciones inferiores: registro de fases, hoja de procedimiento, tabla de tiempos y temperaturas, sustratos textiles, tipos de equipo y fuentes.

## Partes descritas

1. Plancha calefactora
2. Resistencias
3. Plato inferior o base
4. Panel de control
5. Sistema de presión
6. Sensores (termocupla tipo J e interruptor de proximidad)
7. Componentes eléctricos (relé de estado sólido, contactor, disyuntor de 20 A, transformador, conector, filtro)
8. Accesorios y consumibles
9. Resistencias especiales (mug, platos, gorras)

Cada parte se selecciona en la lista o sobre el modelo; la cámara se acerca, la parte se resalta y se muestra su ficha.

## Recursos representados en 3D

| Zona | Objetos |
| --- | --- |
| Estación de diseño e impresión | Computadora con el arte en espejo, impresora de sublimación con tanques CMYK, resma de papel |
| Mesa de materiales | Pieza a estampar, hojas teflonadas, papel impreso, cinta térmica, guantes, regla, rodillo, tijeras |
| Mesa de reposo | Destino del papel impreso y de la pieza estampada |
| Prensa | Plancha, plato, columna, brazo, manija, perilla, caja de control, termocupla |
| Resistencias especiales | Banda cilíndrica para mug, placa para platos, placa curva para gorras |

## Pestaña «Práctica guiada»

### 1 · Preparación

- Material: polo de poliéster SPUM 20/1, polo ranglan para niños, polo polialgodón 30/1, bolso de tela sintética, individual Oxford, pad mouse o mayólica. El material fija SV, P‑1, P‑2, presión, uso de hoja interior, referencia de posición del arte y la secuencia de pasos.
- Talla del polo (catálogo SocoPrint, corte recto, tallas 4 a XL).
- Lista de materiales con casillas obligatorias y opcionales; pantalla «Materiales y costos» con origen (comprar, parte del equipo, disponible en el taller), cantidad, precio unitario en S/ y total.
- Seguridad inicial: seis condiciones del puesto de trabajo.
- Fases 1 y 2: arte en espejo a 300 DPI, impresión en papel de 90–120 g/m² con perfil ICC, secado de 2–5 min. La pantalla «Arte final» simula la impresión y el secado.
- Arte final: PDF (primera página a tamaño real), PNG o JPG (interpretado a 300 DPI) o arte de muestra.

### 2 · Procedimiento

Caja de control simulada: interruptor I/O, pantalla de temperatura (PV/SV), pantalla de tiempo (P‑1/P‑2), indicadores HEAT, P‑1, P‑2 y ALARMA, teclas SET, ▼, ▲ y °C/°F, y verificación en vivo de los valores. SET recorre PV → SV → P‑1 → P‑2 → PV; el último SET guarda los valores.

Secuencia para el polo de poliéster:

| N.º | Paso | Fase |
| --- | --- | --- |
| 1 | Verificar la lista de materiales | Inicio |
| 2 | Confirmar la seguridad inicial | Inicio |
| 3 | Encender la prensa | Prensa |
| 4 | Configurar temperatura y tiempos | Prensa |
| 5 | Precalentar hasta SV | Prensa |
| 6 | Colocar el polo | 3 |
| 7 | Insertar la hoja teflonada interior | 3 |
| 8 | Bajar la prensa · pre‑planchado | 3 |
| 9 | Subir la prensa · pre‑planchado | 3 |
| 10 | Colocar el arte final | 4 |
| 11 | Fijar con cinta térmica (cuatro esquinas) | 4 |
| 12 | Colocar el teflón superior | 4 |
| 13 | Bajar la prensa · sublimado | 5 |
| 14 | Subir la prensa al sonar la alarma | 5 |
| 15 | Retirar el teflón superior | 6 |
| 16 | Retirar el papel | 6 |
| 17 | Visualizar el estampado sublimado | 6 |
| 18 | Retirar el polo de la prensa con el estampado | 6 |
| 19 | Retirar la hoja teflonada interior en frío | 6 |
| 20 | Apagar y desconectar | Cierre |
| 21 | Verificar enfriamiento y ordenar | Cierre |

En piezas rígidas no se incluyen el pre‑planchado ni la hoja interior. Al colocar el arte, el reverso del papel muestra el diseño al 60 % de opacidad.

Rangos de la guía para el polo de poliéster:

| Fase | Rango | Medición en el simulador |
| --- | --- | --- |
| 1 · Diseño e impresión | 2–5 min | Casillas |
| 2 · Secado | 2–5 min | Casillas |
| 3 · Pre‑planchado | 5–12 s | Desde el cierre de la prensa hasta su apertura |
| 4 · Montaje | 10–20 s | Desde la colocación del arte hasta el teflón superior |
| 5 · Sublimado | 40–60 s a 185–205 °C, presión media | Desde el cierre de la prensa hasta su apertura |
| 6 · Desmoldeo | 5–10 s | Apertura → papel retirado, más visualización → retiro de la pieza |

## Pestaña «Tabla del fabricante»

Contiene los 21 productos de la tabla Freesub para la máquina 8 en 1 de 38 × 38 cm (temperaturas de 170 a 200 °C y tiempos de 8 a 900 s). La secuencia de 11 pasos cambia según el tipo de producto: textil, papel transfer, vinil textil, rígido, mug, plato o gorra.

1. Verificar materiales
2. Confirmar la seguridad inicial
3. Encender y fijar SP y ST
4. Esperar el precalentado (avanza al alcanzar SP)
5. Preparar la pieza y el papel
6. Colocar en la prensa
7. Cerrar y prensar
8. Esperar la alarma de tiempo (avanza al cumplirse ST)
9. Abrir y retirar el papel
10. Enfriar y revisar
11. Apagar y desconectar

El botón «Informe de la práctica» genera un informe con logo, docente, nombre del estudiante, fecha, producto, parámetros, rango de PV, materiales, hora de cada paso, observaciones y líneas de firma.

## Ayudas de uso

| Ayuda | Función |
| --- | --- |
| «▶ Ejecutar paso» | Botón en la tarjeta del paso y sobre la vista 3D. Ejecuta el paso o indica qué falta. Tecla N. |
| «Para completar este paso» | Condiciones con ✓ u ○ y su valor actual. |
| «Mostrar dónde» | Cambia de pestaña, desplaza el panel y resalta el control pendiente. |
| «Ir al valor que falta» | Pone el controlador en el valor fuera de rango y resalta ▼ o ▲. |
| «Usar valores sugeridos» | Fija SV, P‑1 y P‑2 del material; queda registrado como configuración asistida. |
| Aviso automático | Aparece tras 40 s sin avanzar en un paso. |
| Cámara guiada | Lleva la cámara a la parte de cada paso, la resalta y muestra un rótulo. |
| Guía de uso | Inicio en cinco pasos, tabla de bloqueos frecuentes y atajos. |
| Recorrido guiado | Catorce puntos de la interfaz. Esc o «Salir» lo cierran. |
| «¿Cómo se usa?» | Recorrido por los controles de la caja de control; también aparecen al pasar el cursor. |

## Señalización de seguridad

Cada norma de seguridad de la práctica lleva el color, la forma y el pictograma de su categoría. Colores y formas según la NTP 399.010-1 (INACAL); códigos según ISO 7010.

| Categoría | Color · forma | Códigos usados |
| --- | --- | --- |
| Prohibición | Rojo · círculo con banda diagonal | P001, P010 |
| Advertencia | Amarillo · triángulo | W001, W012, W017, W021, W024 |
| Obligación | Azul · círculo | M001, M006, M009 |
| Condición segura | Verde · cuadrado | — |
| Equipo contra incendios | Rojo · cuadrado | F001 |

La codificación aparece en las listas de seguridad inicial y de cierre, en el recuadro de seguridad de cada paso, en el aviso sobre la vista 3D y en la sección «Seguridad industrial». La escena 3D incluye un tablero de señales del puesto y un adhesivo W017 en la plancha.

## Registro del estudiante, repaso y acta de compromiso (PDF)

Sección al final de la página. Accesos: botón «Registro del estudiante y acta» en la cabecera, «Registro y acta» en la barra de la vista 3D, «Registrar mis datos y firmar el acta» en «Preparación» y botón en la tarjeta final del procedimiento.

El estudiante completa sus datos, su equipo de trabajo y el tipo de cada material (común, individual o del instituto) con su responsable, firma en el recuadro de firma (mouse, dedo o lápiz), marca la declaración y pulsa «Generar PDF: repaso del ejercicio y acta de compromiso». El PDF (A4, jsPDF 2.5.1 y jspdf‑autotable 3.8.2, cargados al pulsar el botón) contiene:

1. Datos del estudiante, material, talla y parámetros de la prensa.
2. Parte I · Repaso del ejercicio virtual: estado (completo o incompleto), tiempo, pasos realizados, intentos rechazados, fases en rango, PV durante el sublimado, intensidad estimada, configuración, arte final, tabla de fases, mediciones del estudiante frente al simulador y observaciones.
3. Parte II · Acta de compromiso: seis cláusulas (objeto, conocimiento del procedimiento, seguridad industrial, materiales, uso del equipo del instituto y presentación), cuadro de materiales con responsable, costo referencial y casilla «Listo», y firmas (la del estudiante, tomada del recuadro de firma).
4. Anexo 1: lista de verificación de los pasos del material elegido, con medición a anotar, hora registrada en el simulador, espacio para la anotación y casilla.
5. Anexos 2 y 3: seguridad inicial y de cierre con el código de colores.

En la pantalla ampliada, el panel «Práctica guiada / Tabla del fabricante» se superpone a la vista 3D con fondo al 15 % de opacidad y desenfoque; la cámara desplaza el centro de la escena hacia el área libre.

En claude.ai el archivo se entrega mediante la capacidad `downloads` (el visor pide confirmación); fuera del visor se descarga directamente.

## Alarmas

| Tipo | Uso | Sonido |
| --- | --- | --- |
| Completado (verde) | Paso terminado e indicación del siguiente | Dos tonos ascendentes |
| Advertencia (naranja) | Paso rechazado, fuera de orden o valor a corregir | Dos tonos graves |
| Fin de tiempo (azul) | P‑1, P‑2 o ST cumplido | Tres pitidos |
| Crítica (rojo) | Prensa cerrada después de la alarma | Pitido alterno |

El botón «Sonido» activa o silencia los tonos. El navegador habilita el audio después del primer clic en la página.

## Registro y evaluación

- Registro de fases: estado y tiempo medido de cada fase frente a su rango.
- Hoja de procedimiento: hora, duración, medición anotada por el estudiante, valor del simulador y comparación con tolerancia de ±3 °C, ±0,5 cm, ±1 s y ±10 %.
- Seguimiento: parámetros, observaciones, mediciones y registro de cada acción con su resultado; botón «Copiar registro».
- Resultado del ciclo: tiempo de práctica, pasos realizados, intentos rechazados, fases en rango, rango de PV durante el sublimado e intensidad estimada de la transferencia.

## Modelo térmico

- Calentamiento de 0,42 °C/s con el relé cerrado y pérdida proporcional a la diferencia entre PV y 25 °C. La plancha llega a 200 °C en unos 11 min de tiempo simulado.
- Control todo o nada con histéresis de 1 °C.
- Velocidad del calentamiento y del enfriamiento ajustable: ×1, ×10, ×20 o ×60.
- Al cerrar la prensa, PV desciende 7 °C en el pre‑planchado y 9 °C en el sublimado.

## Otras funciones

- Unidades °C y °F en todo el simulador.
- Tema claro u oscuro; la elección se guarda en el navegador.
- Pantalla ampliada con la vista 3D y el panel de procedimiento.
- Modo automatizado: la prensa se abre al cumplirse P‑1 y P‑2.
- Demo: ejecuta la secuencia completa a velocidad ×3.

## Atajos de teclado

| Tecla | Acción |
| --- | --- |
| N | Ejecutar el paso en curso |
| Esc | Salir del recorrido guiado, cerrar ventanas o salir de la pantalla ampliada |

## Limitaciones

- El visor de artefactos bloquea el cuadro de impresión. El informe se copia con formato para pegarlo en Word o Google Docs e imprimirlo desde ahí.
- La intensidad de transferencia es un indicador calculado con la temperatura medida, el tiempo de prensado y la presión; no reemplaza una prueba de estampado.
- Dimensiones de la plancha según la ficha del fabricante; las demás piezas están en proporción aproximada (escala 1 u = 10 cm).
- Valores de taller sin fuente documental: base del cuello a 2,5 cm del borde posterior del plato, distancia cuello–arte de 7–10 cm (editable), hoja interior con 2 cm de margen y tiras de cinta de 3–4 cm.
- Rangos de bolso, pad mouse y mayólica: ±5 alrededor del valor único de la tabla Freesub. Individual Oxford: rangos de la guía de poliéster, por falta de dato en las fuentes.

## Fuentes

1. Freesub Perú. Temperaturas y tiempos para sublimar. Máquina 8 en 1 multifuncional 38 × 38 cm (PDF).
2. SocoPrint. Catálogo textil (PDF). Av. Santa Rosa 2001, San Juan de Lurigancho, Lima.
3. Guía de estampado por sublimación textil en polos de poliéster (tabla de fases, tiempos y parámetros proporcionada por el docente).
4. Servicolombia DC. Manuales de termofijadoras.
5. Importasia. Piezas y repuestos para termofijadoras.
6. Laser Textil. Repuestos para termofijadora.
7. Termofijadoras.com. Repuestos y consumibles.
8. JMS. Folleto NL‑27 (fundas Nomex®).
