# Anatomía de una termofijadora

Simulador web en 3D de una prensa térmica de plancha plana de 38 × 38 cm con resistencias intercambiables (modelo de referencia: máquina multifuncional 8 en 1, Freesub Perú, P8038‑RV8). Describe las partes del equipo y reproduce, paso a paso, el estampado por sublimación, la transferencia DTF y el ciclo de prensado de los productos de la tabla de tiempos y temperaturas del fabricante. Al terminar, el estudiante registra sus datos, firma en pantalla y genera un PDF con el repaso del ejercicio virtual y el acta de compromiso para la práctica con la prensa del instituto.

Autor: Mg. Mario Quiroz Martínez · Instituto de Educación Superior “Diseño y Comunicación” (IDC), Lima.

## Contenido

1. [Archivo y requisitos](#archivo-y-requisitos)
2. [Distribución de la página](#distribución-de-la-página)
3. [Vista 3D](#vista-3d)
4. [Pestaña «Práctica guiada»](#pestaña-práctica-guiada)
5. [Pestaña «Tabla del fabricante»](#pestaña-tabla-del-fabricante)
6. [Controlador digital](#controlador-digital)
7. [Ayudas de uso](#ayudas-de-uso)
8. [Alarmas](#alarmas)
9. [Seguridad industrial](#seguridad-industrial)
10. [Registro y evaluación](#registro-y-evaluación)
11. [Registro del estudiante, repaso y acta de compromiso](#registro-del-estudiante-repaso-y-acta-de-compromiso)
12. [Secciones de referencia](#secciones-de-referencia)
13. [Modelo térmico](#modelo-térmico)
14. [Otras funciones y atajos](#otras-funciones-y-atajos)
15. [Limitaciones y valores sin fuente](#limitaciones-y-valores-sin-fuente)
16. [Fuentes](#fuentes)

## Archivo y requisitos

| Archivo | Contenido |
| --- | --- |
| `termofijadora.html` | Página única con HTML, CSS y JavaScript (módulo ES). El logo del IDC está incrustado como imagen PNG en base64. |

Requisitos: navegador con WebGL (Chrome, Edge, Firefox o Safari en versiones actuales) y conexión a internet para las bibliotecas y las fuentes.

| Recurso | Versión | Origen | Carga |
| --- | --- | --- | --- |
| three.js, `OrbitControls`, `CSS2DRenderer` | 0.186.1 | cdn.jsdelivr.net | Al abrir la página |
| Anime.js y `animejs/adapters/three` | 4.5.0 | cdn.jsdelivr.net | Al abrir la página |
| pdf.js | 3.11.174 | cdnjs.cloudflare.com | Al insertar un arte en PDF |
| jsPDF | 2.5.1 | cdnjs.cloudflare.com | Al generar el PDF del acta |
| jspdf‑autotable | 3.8.2 | cdnjs.cloudflare.com | Al generar el PDF del acta |
| Barlow Condensed, IBM Plex Sans, IBM Plex Mono, Share Tech Mono | — | Google Fonts | Al abrir la página |

La página publicada en claude.ai declara la capacidad `downloads` para entregar el PDF del acta.

## Distribución de la página

1. Cabecera: logo, título, botón de tema claro u oscuro, botón «Registro del estudiante y acta» y datos del modelo de referencia.
2. Zona del simulador: vista 3D a la izquierda y panel lateral con las pestañas «Práctica guiada» y «Tabla del fabricante».
3. Registro de fases.
4. Hoja de procedimiento.
5. Seguridad industrial.
6. Tiempos y temperaturas (tabla Freesub).
7. Sustratos textiles (catálogo SocoPrint).
8. Transferencia DTF.
9. Tipos de equipo.
10. Glosario.
11. Fuentes.
12. Registro del estudiante y acta de compromiso.
13. Pie: «Mg. Mario Quiroz Martínez · Instituto de Educación Superior “Diseño y Comunicación”».

## Vista 3D

### Barra de herramientas

Vista general, Vista explosionada, Ver interior, Rótulos, Ampliar pantalla, Ayuda, Recorrido guiado, Recursos, Sonido, Materiales, Registro y acta, y la casilla «Cámara guiada». Sobre la vista hay dos paneles con fondo al 15 % de opacidad: lista de partes y lista de materiales.

### Partes descritas

| N.º | Parte | Contenido de la ficha |
| --- | --- | --- |
| 01 | Plancha calefactora | Placa de aluminio con cara de PTFE; 38 × 38 cm; rango de la tabla 170–200 °C |
| 02 | Resistencias | Elemento tubular en serpentín, conmutado por el relé de estado sólido |
| 03 | Plato inferior o base | Goma térmica de silicona sobre placa metálica; funda Nomex® opcional |
| 04 | Panel de control | PV, SV, P‑1, P‑2, SP, ST; alarma acústica |
| 05 | Sistema de presión | Brazo, tornillo central, perilla y manija; cierre tipo caimán; amortiguador de 500 N o 700 N |
| 06 | Sensores | Termocupla tipo J (≈50–55 µV/°C) e interruptor de proximidad |
| 07 | Componentes eléctricos | Relé de estado sólido, contactor, disyuntor de 20 A, transformador, conector, filtro |
| 08 | Accesorios y consumibles | Hojas teflonadas, cinta térmica, guantes, funda |
| 09 | Resistencias especiales | Banda cilíndrica para mug, placa para platos, placa curva para gorras |

Al seleccionar una parte, la cámara se acerca, la parte se resalta y se muestra su ficha.

### Recursos del proceso

| Zona | Objetos |
| --- | --- |
| Estación de diseño e impresión | Computadora con el arte en espejo, impresora de sublimación con tanques CMYK, resma de papel |
| Mesa de materiales | Pieza, hojas teflonadas, papel o transfer impreso, cinta térmica, guantes, regla, rodillo, tijeras; ✓ en el rótulo al marcar cada material |
| Mesa de reposo | Destino del papel usado y de la pieza estampada |
| Tablero de señales | Superficie caliente, atrapamiento de manos, riesgo eléctrico, use guantes térmicos, no tocar la plancha, extintor |
| Prensa | Adhesivo W017 (superficie caliente) sobre la cubierta de la plancha |

### Cámara guiada y pantalla ampliada

- Con «Cámara guiada» activa, cada paso lleva la cámara a la sección que corresponde, resalta la parte y muestra un rótulo «PASO NN · acción».
- «Ampliar pantalla» ocupa toda la ventana mediante una clase CSS. En pantallas de más de 900 px, el panel «Práctica guiada / Tabla del fabricante» se superpone a la vista 3D con fondo al 15 % y desenfoque de 6 px, y la cámara desplaza el centro de la escena hacia el área libre. Esc o «Reducir pantalla» la cierran.
- Al colocar el arte, el reverso del papel muestra el diseño al 60 % de opacidad.

## Pestaña «Práctica guiada»

### 1 · Preparación

- **Material a estampar.** Fija SV, P‑1, P‑2, presión, uso de hoja interior, referencia de posición del arte, lista de materiales y secuencia de pasos.

| Material | Proceso | SV (rango · sugerido) | P‑1 | P‑2 | Presión | Hoja interior |
| --- | --- | --- | --- | --- | --- | --- |
| Polo de poliéster 100 % · SPUM 20/1 | Sublimación | 185–205 · 200 °C | 5–12 · 8 s | 40–60 · 50 s | Media | Sí |
| Polo ranglan para niños · área blanca | Sublimación | 185–205 · 200 °C | 5–12 · 8 s | 40–60 · 50 s | Media | Sí |
| Polo polialgodón 30/1 color | Sublimación | 185–205 · 200 °C | 5–12 · 8 s | 40–60 · 50 s | Media | Sí |
| Bolso de tela sintética 35 × 40 cm | Sublimación | 195–205 · 200 °C | 5–12 · 8 s | 55–65 · 60 s | Media | Sí |
| Individual Oxford 28 × 30 cm | Sublimación | 185–205 · 200 °C | 5–12 · 6 s | 40–60 · 50 s | Media | No |
| Pad mouse | Sublimación | 195–205 · 200 °C | No aplica | 55–65 · 60 s | Media | No |
| Mayólica o fotoroca 20 × 20 cm | Sublimación | 195–205 · 200 °C | No aplica | 380–420 · 400 s | Media | No |
| Polo de algodón 100 % · transfer DTF | DTF | 150–170 · 160 °C | 3–5 · 4 s | 15–30 · 15 s | Media o alta | No |
| Polo de poliéster o mezcla >50 % sintético · transfer DTF | DTF | 135–145 · 140 °C | 3–5 · 4 s | 40–50 · 45 s | Media o alta | No |

- **Talla del polo** (ancho × largo en cm): 4 (35 × 45), 6 (37 × 48), 8 (38 × 51), 10 (40 × 54), 12 (42 × 58), 14 (44 × 60), 16 (50 × 68), S (50 × 70), M (52 × 70), L (54 × 72), XL (56 × 74).
- **Lista de materiales** con casillas obligatorias y opcionales. La pantalla «Materiales y costos» registra origen (comprar, parte del equipo, disponible en el taller), cantidad, precio unitario en S/ y total.
- **Seguridad inicial:** diálogo con seis condiciones; «Confirmar y continuar» se habilita con todas marcadas.
- **Fases 1 y 2** (casillas): en sublimación, arte en espejo a 300 DPI, impresión en papel de 90–120 g/m² con perfil ICC y secado de 2–5 min (la pantalla «Arte final» simula la impresión y el secado); en DTF, transfer impreso en espejo sobre film PET con capa de blanco, polvo TPU aplicado y polvo TPU curado.
- **Arte final:** PDF (primera página a tamaño real), PNG o JPG (interpretado a 300 DPI) o arte de muestra; ancho del arte y distancia cuello–arte editables.

### 2 · Procedimiento

Secuencia para el polo de poliéster (sublimación). Los pasos marcados con * dependen del material.

| N.º | Paso | Grupo |
| --- | --- | --- |
| 1 | Verificar la lista de materiales | Inicio |
| 2 | Confirmar la seguridad inicial | Inicio |
| 3 | Encender la prensa | Prensa |
| 4 | Configurar temperatura y tiempos | Prensa |
| 5 | Precalentar hasta SV | Prensa |
| 6 | Colocar el polo | Fase 3 |
| 7 | Insertar la hoja teflonada interior* | Fase 3 |
| 8 | Bajar la prensa · pre‑planchado* | Fase 3 |
| 9 | Subir la prensa · pre‑planchado* | Fase 3 |
| 10 | Colocar el arte final | Fase 4 |
| 11 | Fijar con cinta térmica (cuatro esquinas) | Fase 4 |
| 12 | Colocar el teflón superior | Fase 4 |
| 13 | Bajar la prensa · sublimado | Fase 5 |
| 14 | Subir la prensa al sonar la alarma | Fase 5 |
| 15 | Retirar el teflón superior | Fase 6 |
| 16 | Retirar el papel | Fase 6 |
| 17 | Visualizar el estampado sublimado | Fase 6 |
| 18 | Retirar el polo de la prensa con el estampado | Fase 6 |
| 19 | Retirar la hoja teflonada interior en frío* | Fase 6 |
| 20 | Apagar y desconectar | Cierre |
| 21 | Verificar enfriamiento y ordenar | Cierre |

- Piezas rígidas: sin pre‑planchado ni hoja interior.
- Materiales DTF: 19 pasos, sin hoja interior. Cambian los textos: «Colocar el transfer DTF» (adhesivo hacia la tela, película PET hacia arriba), «Bajar la prensa · transferencia DTF», «Retirar el film PET» (en caliente o en frío según la película) y «Visualizar el estampado DTF». El planchado de sellado de 3–5 s figura como paso opcional fuera del simulador.
- Paso 17: ventana con la silueta de la pieza y el arte transferido, cotas, datos de SV, tiempo y presión, y revisión visual ✓/✗.
- Paso 18: trayectoria en tres tramos (levantar, deslizar al frente, llevar a la mesa de reposo).

Rangos de la guía para el polo de poliéster:

| Fase | Rango | Medición en el simulador |
| --- | --- | --- |
| 1 · Diseño e impresión | 2–5 min | Casillas |
| 2 · Secado | 2–5 min | Casillas |
| 3 · Pre‑planchado | 5–12 s | Cierre → apertura de la prensa |
| 4 · Montaje | 10–20 s | Arte colocado → teflón superior |
| 5 · Sublimado | 40–60 s a 185–205 °C, presión media | Cierre → apertura de la prensa |
| 6 · Desmoldeo | 5–10 s | (Apertura → papel retirado) + (visualización → retiro de la pieza) |

Botones de la barra: Insertar arte final, Demo (secuencia completa a ×3), Automatizado (la prensa se abre al cumplirse P‑1 y P‑2), Seguimiento, Ampliar pantalla, Reiniciar, Guía de uso y selector °C/°F.

## Pestaña «Tabla del fabricante»

El selector de producto tiene dos grupos:

- **Tabla Freesub · sublimación, transfer y vinil:** 21 productos de la máquina 8 en 1 de 38 × 38 cm, de 170 a 200 °C y de 8 a 900 s (por ejemplo, polo sintético 200 °C · 60 s; taza de cerámica 180 °C · 180 s; platos de cerámica 200 °C · 900 s; gorras 190 °C · 45 s).
- **Transferencia DTF · guía del curso:** polo de algodón (160 °C · 15 s) y polo de poliéster o mezcla (140 °C · 45 s). No figuran en la tabla de referencia «Tiempos y temperaturas».

La secuencia tiene 11 pasos con texto según el tipo de producto (textil, papel transfer, vinil, DTF, rígido, mug, plato, gorra):

1. Verificar materiales
2. Confirmar la seguridad inicial
3. Encender y fijar SP y ST
4. Esperar el precalentado (avanza al alcanzar SP)
5. Preparar la pieza y el papel (o el polo y el transfer DTF)
6. Colocar en la prensa
7. Cerrar y prensar
8. Esperar la alarma de tiempo (avanza al cumplirse ST)
9. Abrir y retirar el papel (o el film PET)
10. Enfriar y revisar
11. Apagar y desconectar

El botón «Informe de la práctica» genera un informe con logo, docente, nombre del estudiante, fecha, producto, SP y ST, rango de PV, materiales, hora de cada paso, observaciones y líneas de firma, para copiar con formato.

## Controlador digital

| Elemento | Función |
| --- | --- |
| Interruptor I/O | Enciende (I) y apaga (O) la prensa |
| Pantalla roja | PV (temperatura medida); en modo SET, SV parpadeando; con la prensa apagada y la plancha sobre 50 °C, «HOT» |
| Pantalla verde | P‑1 o P‑2; cuenta regresiva con la prensa cerrada |
| Indicadores | HEAT (relé alimentando la resistencia), P‑1, P‑2, ALARMA (tiempo cumplido) |
| SET | Avanza PV → SV → P‑1 → P‑2 → PV; al volver a PV guarda los valores; bloqueada con la prensa cerrada |
| ▲ ▼ | Ajustan ±1 °C o ±1 s; mantenidas, aceleran |
| °C/°F | Cambia la unidad en todo el simulador |
| Verificación en vivo | Chips ✓/✗ de SV, P‑1 y P‑2 frente al rango del material |

Límites: SV 50–230 °C, P‑1 0–99 s, P‑2 0–999 s. Cada control muestra una ventana emergente con su función; «¿Cómo se usa?» los recorre en orden. Bajo el controlador hay un enlace al glosario.

## Ayudas de uso

| Ayuda | Función |
| --- | --- |
| «▶ Ejecutar paso» | Botón en la tarjeta del paso y sobre la vista 3D. Ejecuta el paso o indica qué falta. Tecla N. |
| «Para completar este paso» | Condiciones con ✓ u ○ y su valor actual. |
| «Mostrar dónde» | Cambia de pestaña, desplaza el panel y resalta el control pendiente. |
| «Ir al valor que falta» | Pone el controlador en el valor fuera de rango y resalta ▼ o ▲. |
| «Usar valores sugeridos» | Fija SV, P‑1 y P‑2 del material; queda registrado como configuración asistida. |
| Aviso automático | Aparece tras 40 s sin avanzar en un paso. |
| Guía de uso | Inicio en cinco pasos, tabla de bloqueos frecuentes y atajos. |
| Recorrido guiado | 14 puntos de la interfaz. Esc o «Salir» lo cierran. |
| Glosario | Sección con buscador; enlace desde el controlador. |

## Alarmas

| Tipo | Uso | Sonido (WebAudio) |
| --- | --- | --- |
| Completado (verde) | Paso terminado e indicación del siguiente | Dos tonos ascendentes |
| Advertencia (naranja) | Paso rechazado, fuera de orden o valor a corregir | Dos tonos graves |
| Fin de tiempo (azul) | P‑1, P‑2 o ST cumplido | Tres pitidos |
| Crítica (rojo) | Prensa cerrada después de la alarma | Pitido alterno |

El botón «Sonido» activa o silencia los tonos. El navegador habilita el audio después del primer clic en la página.

## Seguridad industrial

Cada norma de la práctica lleva color, forma y pictograma de su categoría. Colores y formas según la NTP 399.010-1 (INACAL); códigos según ISO 7010.

| Categoría | Color · forma | Códigos usados |
| --- | --- | --- |
| Prohibición | Rojo · círculo con banda diagonal | P001, P010 |
| Advertencia | Amarillo · triángulo | W001, W012, W017, W021, W024 |
| Obligación | Azul · círculo | M001, M006, M009 |
| Condición segura | Verde · cuadrado | — |
| Equipo contra incendios | Rojo · cuadrado | F001 |

La codificación aparece en los diálogos de seguridad inicial y de cierre, en el recuadro de seguridad de cada paso, en el aviso sobre la vista 3D, en la sección «Seguridad industrial» (cinco tarjetas con todas las normas) y en los anexos del PDF.

- Seguridad inicial: área ventilada y superficie estable; cable y enchufe sin daños, tomacorriente con tierra; guantes térmicos al alcance; cabello recogido, sin pulseras ni mangas sueltas; zona libre de papeles, solventes e inflamables; ubicación del interruptor general y del extintor.
- Seguridad de cierre: interruptor en O; enchufe desconectado tomándolo por el cuerpo; plancha caliente a la vista y señalizada; no cubrir ni guardar hasta que esté fría; restos de cinta y papel retirados.

## Registro y evaluación

- **Registro de fases:** seis tarjetas con estado, tiempo medido y rango.
- **Hoja de procedimiento:** por paso, hora, duración, medición del estudiante, valor del simulador y comparación con tolerancias de ±3 °C, ±0,5 cm, ±1 s y ±10 %.
- **Seguimiento:** parámetros, observaciones, mediciones y registro de cada acción; botón «Copiar registro».
- **Resultado del ciclo:** tiempo de práctica, pasos realizados, intentos rechazados, fases en rango, rango de PV durante el prensado e intensidad estimada.

## Registro del estudiante, repaso y acta de compromiso

Accesos: «Registro del estudiante y acta» (cabecera), «Registro y acta» (barra de la vista 3D), «Registrar mis datos y firmar el acta» (Preparación) y botón en la tarjeta «Procedimiento terminado».

El formulario pide:

1. Apellidos y nombres, código, programa de estudios, ciclo y turno, docente y fecha.
2. Equipo de trabajo, un compañero por línea.
3. Tipo de cada material (común, individual o del instituto) y responsable.
4. Firma en el recuadro de firma (mouse, dedo o lápiz), con botón «Borrar firma».
5. Casilla de declaración.

La sección muestra el avance del ejercicio en vivo. El PDF solo se genera con nombre, firma y declaración. Contenido del PDF (A4):

| Parte | Contenido |
| --- | --- |
| Datos | Estudiante, material, talla y parámetros de la prensa |
| Parte I · Repaso del ejercicio virtual | Estado (completo o incompleto), tiempo, pasos realizados, intentos rechazados, fases en rango, PV durante el prensado, intensidad, configuración (manual o asistida), modo (manual, automatizado o demo), arte final, tabla de fases, mediciones del estudiante frente al simulador y observaciones |
| Parte II · Acta de compromiso | Seis cláusulas (objeto, conocimiento del procedimiento, seguridad industrial, materiales, uso del equipo del instituto, presentación), cuadro de materiales con responsable, costo referencial y casilla «Listo», y firmas (la del estudiante, tomada del recuadro) |
| Anexo 1 | Lista de verificación de los pasos del material elegido: medición a anotar, hora registrada en el simulador, espacio para la anotación manual y casilla |
| Anexos 2 y 3 | Seguridad inicial y de cierre con el código de colores y casilla |

Si el ejercicio no está completo, el PDF lo indica como «Incompleto» con el número de pasos realizados. En claude.ai el archivo se entrega mediante la capacidad `downloads` (el visor pide confirmación); fuera del visor se descarga directamente.

## Secciones de referencia

- **Tiempos y temperaturas:** tabla Freesub de 21 productos; cada fila carga el producto en la pestaña «Tabla del fabricante».
- **Sustratos textiles:** artículos del catálogo SocoPrint con tela, método indicado y precio unitario.
- **Transferencia DTF:** parámetros de la termofijadora (algodón 150–170 °C · 15–30 s, valor frecuente 160 °C · 15 s; poliéster o mezcla >50 % sintético 140 °C · 45 s; presión media a alta; preplanchado y sellado de 3–5 s; despegue en caliente o en frío), características del polo (composición, color, sin pretratamiento, estampado resultante) y comparación con la sublimación.
- **Tipos de equipo:** plana, portátil, 8 en 1, de gorras, de lápices.
- **Glosario:** 32 términos en cuatro grupos (controlador digital; equipo y control térmico; procesos de estampado; arte e impresión), con buscador. Incluye SV, PV, P‑1, P‑2, SP, ST, SET, HEAT, ALARMA, HOT, SSR, termocupla tipo J, histéresis, PTFE, sublimación, DTF, TPU, PET, *hot peel* y *cold peel*, *white underbase*, DTG, DPI, modo espejo, ICC, CMYK y g/m².

## Modelo térmico

- Integración en subpasos de 0,5 s simulados: PV aumenta 0,42 °C/s con el relé cerrado y pierde 0,0016 × (PV − 25) por segundo. La plancha llega a 200 °C en unos 11 min de tiempo simulado.
- Control todo o nada con histéresis de 1 °C sobre SV.
- Al cerrar la prensa, PV baja 7 °C en el pre‑planchado y 9 °C en el prensado principal.
- Velocidad del calentamiento y del enfriamiento: ×1, ×10, ×20 o ×60; no altera P‑1 ni P‑2.
- La intensidad estimada se calcula con la temperatura durante el prensado, el tiempo y la presión.

## Otras funciones y atajos

- Unidades °C y °F en todo el simulador.
- Tema claro u oscuro; la elección se guarda en el navegador.

| Tecla | Acción |
| --- | --- |
| N | Ejecutar el paso en curso |
| Esc | Salir del recorrido guiado, cerrar diálogos o salir de la pantalla ampliada |

## Limitaciones y valores sin fuente

- El visor de artefactos bloquea el cuadro de impresión: el informe de la tabla del fabricante se copia con formato para pegarlo en Word o Google Docs.
- El PDF usa las fuentes estándar de jsPDF: «→» se escribe «->», «▲ ▼» como «(subir)» y «(bajar)», y «≈» como «~».
- La intensidad de transferencia es un indicador del simulador; no reemplaza una prueba de estampado.
- El retiro en frío del film DTF y el planchado de sellado no se simulan con espera ni con un prensado adicional.
- Dimensiones de la plancha según la ficha del fabricante; las demás piezas están en proporción aproximada (1 unidad = 10 cm).
- Valores de taller sin fuente documental: base del cuello a 2,5 cm del borde posterior del plato; distancia cuello–arte de 7–10 cm; hoja interior con 2 cm de margen; tiras de cinta de 3–4 cm.
- Rangos de ±5 alrededor del valor único de la fuente: bolso, pad mouse y mayólica (tabla Freesub); polo de poliéster DTF (guía del curso). Individual Oxford: rangos de la guía de poliéster.
- Los tiempos DTF de la guía (15–30 s en algodón, 45 s en poliéster) son mayores que los de los proveedores consultados (10–15 s y 8–10 s); la página lo indica en la sección «Transferencia DTF» y en la nota de cada material.
- La NTP 399.010-1 se cita sin año de edición.

## Fuentes

1. Freesub Perú. *Temperaturas y tiempos para sublimar. Máquina 8 en 1 multifuncional 38 × 38 cm* (PDF).
2. SocoPrint. *Catálogo textil* (PDF). Av. Santa Rosa 2001, San Juan de Lurigancho, Lima.
3. Guía de estampado por sublimación textil en polos de poliéster (tabla de fases, tiempos y parámetros proporcionada por el docente).
4. Guía de características técnicas de la termofijadora para transferencia DTF (proporcionada por el docente).
5. Servicolombia DC. Manuales de termofijadoras.
6. Importasia. Piezas y repuestos para termofijadoras.
7. Laser Textil. Repuestos para termofijadora.
8. Termofijadoras.com. Repuestos y consumibles.
9. JMS. Folleto NL‑27 (fundas Nomex®).
10. DTF Transfers Now. *DTF Heat Press Settings: Temperature Guide by Fabric*.
11. Ninja Transfers. *Instrucciones de prensa de calor para transferencias DTF*.
12. INACAL. NTP 399.010-1, *Señales de seguridad. Colores, símbolos, formas y dimensiones de señales de seguridad*. ISO 7010, *Símbolos gráficos. Colores y señales de seguridad*.
