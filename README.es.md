# AtelierCV — ayuda

[Français](README.md) · [English](README.en.md) · **Español**

AtelierCV sirve para dibujar una cometa (armazón, vela, embridado) y calcular su forma: en
reposo, en vuelo con viento o en planeo. Es **un solo archivo**: abrir `AtelierCV_v370.html`
en un navegador reciente (se recomiendan Chrome o Edge), sin instalar nada.

La carpeta **`Modeles/`** contiene una biblioteca de cometas listas para abrir (Eddy, Edo, Flare,
Sled, Eclipse, Mouette…): botón **Abrir**, luego el archivo `.json`. Es lo más sencillo
para descubrir la herramienta, y una buena base para un diseño nuevo.

> **Una herramienta en desarrollo.** AtelierCV sigue evolucionando y sus resultados **no son
> fiables tal cual**: dan **pistas** (tendencias, comparaciones entre variantes, sentido de una
> corrección), que hay que confirmar en la realidad. Sus principales límites:
> - **sin simulación del flujo de aire**: el viento se calcula con un modelo simplificado de
>   superficie sustentadora, sin entrada en pérdida real, capa límite, turbulencia ni estela;
> - **todavía no gestiona las estructuras totalmente flexibles** (parafoils, cajones): la presión
>   interior de los cajones existe, pero no está validada;
> - la tela, el armazón y el viento siguen siendo modelos: rozamiento, costuras, dobladillos,
>   conectores y tejidos reales son aproximados.

En todas partes, el pequeño **ⓘ** explica un ajuste; la mayoría de los valores se ajustan con un
cursor, y un clic en el valor permite escribirlo (más allá de los límites del cursor si hace falta).

La interfaz existe en francés, inglés y español (elección en la cabecera).

## La pantalla

- **A la izquierda — Dibujo**: las capas, las herramientas, los ajustes de lo seleccionado.
- **En el centro — Cálculo**: las condiciones de cálculo, el botón **Calcular**, y luego los
  resultados (tensiones, esfuerzos en tubos y cables, masas, viento, consejos).
- **A la derecha — las vistas**: el dibujo plano (Superior, Frontal, Lateral) y la vista 3D, que
  muestra el resultado (colores = tensión de la tela; tubos azules en compresión, rojos en tracción).

Arriba: Nuevo, Abrir, Guardar (.json), exportaciones (patrones planos en DXF, informe de cálculo
en HTML, lista de materiales), la biblioteca, el idioma, el tema, Deshacer (Ctrl+Z).

## Dibujar

Se trabaja en una capa a la vez; las demás siguen visibles y sirven de enganche.

| Capa | Herramientas |
|---|---|
| **Armazón** | Tubo, Sable (en un bolsillo de la vela), Cable, Whisker (separador), Línea de construcción |
| **Embridado** | Brida / línea, Cola, Lastre |
| **Velamen** | Forma (un clic por vértice), Círculo, Costura (corte en paneles), Unión (vela ↔ armazón), Montar |

- **Planos**: Superior = plano XY, vela vista desde el lado de las bridas, frente de la cometa
  arriba; Frontal = vista desde delante; Lateral = perfil. Z es vertical.
- **Puntos**: un punto compartido por varios elementos se convierte en un **nodo** (conector).
  Seleccionarlo para elegir su tipo: **rígido** (soldado), **rótula**, **corredera** (el elemento
  que lo atraviesa se desliza en él, como en un manguito) o **libre**. Un nodo también puede ser
  **Punto fijo** (anclaje al suelo) o la **Anilla** (donde se ata la línea).
- **Bordes de vela**: dobladillo, funda sobre un tubo, o borde unido a un cable.
- **Simetría**: se dibuja el lado izquierdo (X negativa) y el lado derecho lo sigue. El botón
  **Simetrizar** reconstruye el lado derecho de un dibujo existente.
- **Aislar**: mostrar una sola forma para retocarla, en su propio plano si está inclinada.
- **Tubos y sables**: material y sección de la biblioteca, **sobrelongitud** (pretensado),
  **Recto en reposo** (desmarcado: la curva dibujada es su forma libre).
- **Velas**: tejido (biblioteca), patrón, agujeros y refuerzos; casilla **Quilla** (fuera del
  cálculo en reposo) y casilla **Cajón** (parafoil: piel inflada por la presión interior).

## Ratón y teclado

Los mismos gestos valen en la vista de dibujo y en la vista 3D.

| Gesto | Efecto |
|---|---|
| **Clic** | seleccionar; con una herramienta, colocar un punto (se engancha a los puntos, puntos medios y trazados cercanos) |
| **Arrastrar** un punto o un tirador | moverlo |
| **Arrastrar sobre el fondo** | ventana de selección: de izquierda a derecha = formas completamente dentro, de derecha a izquierda = formas tocadas |
| **Ctrl+clic** (Cmd en Mac) | añadir o quitar de la selección; sobre los puntos de una forma seleccionada: seleccionar varios puntos |
| **Mayús+clic** o **clic derecho** (sin arrastrar) | sobre un trazado: añadir un punto; sobre un punto: quitarlo; durante un trazado: cancelarlo |
| **Alt** pulsado | sin imán (punto colocado libremente) |
| **Arrastrar con clic derecho** | girar (vista 3D y perspectiva) o desplazar la vista (vistas planas) |
| **Mayús+clic derecho**, **botón central** o **Espacio+arrastrar** | desplazar la vista |
| **Rueda** | zoom (hacia el cursor; en 3D hacia la cruz naranja, el pivote) |
| **Doble clic** | reencuadrar la cometa (durante el trazado de una forma: cerrarla) |
| **F** | colocar el pivote en la selección o en el punto bajo el ratón |
| **Mayús** al arrastrar un tirador de desplazamiento | movimiento fino (÷ 10) |

| Tecla | Efecto |
|---|---|
| **Ctrl+Z** / **Ctrl+Y** | deshacer / rehacer |
| **Supr** | borrar la selección |
| **Esc** | cancelar el trazado en curso, vaciar la selección, salir de Aislar |
| **Intro** | cerrar la forma en curso (3 vértices como mínimo) |
| **Cifras** durante un trazado | escribir una longitud exacta, luego Intro |
| **Flechas** | mover los puntos seleccionados (Mayús: ×10) |
| **D** | duplicar la selección |
| **V** selección · **U** tubo · **A** sable · **B** cable · **W** whisker · **L** línea · **R** brida · **T** forma · **O** círculo · **C** costura · **K** unión · **M** montar | elegir la herramienta |

## Verificar antes de calcular

**Verificar el dibujo** enumera lo que impediría un cálculo correcto: puntos sin unir, cables que
pasan por un punto suelto, patrones incoherentes, sables acodados, nombres repetidos… La mayoría
de las líneas tienen un botón que lo corrige (Unir, Recortar sobre el armazón, Alinear, Renombrar…).

## Calcular

Elegir las condiciones en el centro, luego **Calcular**:

- **En reposo (en el suelo)**: la forma bajo el solo pretensado (sobrelongitudes, tensión de los
  cables). Las quillas quedan excluidas. Una cometa sin armazón (parafoil) no tiene forma en reposo.
  La forma en reposo obtenida se guarda en el archivo: el cálculo siguiente parte de ella.
- **Sujeta por la línea (tiro)**: un tiro repartido sobre la tela, opuesto a la línea.
- **En vuelo, viento de frente horizontal**: el viento real (velocidad en km/h); la cometa
  encuentra su orientación al extremo de su línea, luego su forma bajo el viento, vuelta tras
  vuelta. Los resultados dan la calidad del vuelo, un consejo de embridado y la estabilidad
  (guiñada, alabeo, cabeceo). Opciones: peso, colas, resistencia de las bridas.
- **Planeo (sin línea)**: la actitud en la que la cometa planea estable, su velocidad, su
  pendiente y su fineza (rozamiento de la tela ajustable), la polar, el mejor planeo y el
  **centrado**: cuánto desplazar el centro de gravedad, y qué masa de lastre poner en el morro o
  atrás. El botón **Optimizar el planeo** ajusta la masa del lastre (el único, o el marcado «A optimizar») con
  cálculos de planeo reales, intento tras intento, hasta la mejor fineza en planeo estable; los
  demás lastres (por ejemplo el peso de la línea en la anilla) quedan fijos. Si el lastre cuelga de la anilla,
  una segunda pasada desliza la anilla a lo largo de la brida, con la masa fija. El dibujo solo cambia
  con «Aplicar».

**Perfil de cálculo**: Estimación (rápido, malla gruesa), Estándar, Preciso. En caso de duda
sobre un resultado, repetir el cálculo en Estándar o Preciso.

El cálculo es un modelo: la tela y el armazón se calculan bien; el aire, de forma simplificada
(sin entrada en pérdida ni capa límite). Sirve sobre todo para **comparar variantes** y para
encontrar **en qué sentido corregir** (tensión, embridado, centrado).

## Cómo calcula

- **El modelo.** Cada vela se corta en pequeños triángulos (la *malla*; cuanto mayor es la
  finura, más pequeños son). La tela tiene su propia rigidez en urdimbre, en trama y al bies, y no
  resiste la compresión (forma pliegues); tiene además una pequeña rigidez a la flexión, como una
  hoja de papel (ajustable por tejido, medible con el ensayo del voladizo), que cuenta sobre todo en
  los planeadores ligeros poco tensos. Tubos y sables son vigas (tracción, compresión, flexión,
  torsión); cables, bridas y dobladillos solo trabajan a tracción. Los conectores lo unen todo según
  su tipo.
- **La búsqueda del equilibrio (relajación dinámica).** El cálculo mueve todos los nodos paso a
  paso, como un objeto que se suelta y se amortigua, hasta que las fuerzas se anulan en todas
  partes. Cada paso es una **iteración**.
  - **Tolerancia**: el desequilibrio de fuerza aceptado al final, referido a los esfuerzos de la
    cometa (0,001 = 0,1 %). Más pequeña = más exacto, pero más largo.
  - **Iteraciones máx.**: el cálculo se detiene ahí si no ha terminado («no convergido»).
  - **Inicio de pandeo**: un defecto inicial mínimo, para que un tubo demasiado comprimido pandee
    del lado correcto en vez de quedarse recto en equilibrio inestable; una sonda comprueba luego
    que ningún tubo se ha quedado recto por encima de su carga de pandeo.
  - **Masas aligeradas**: un ajuste del cálculo que acelera la convergencia; no cambia el resultado.
- **El viento (método de anillos de vórtice).** La superficie se corta en paneles, cada uno con
  un vórtice; de ellos se deduce la presión en cada panel, y así la sustentación, la resistencia
  inducida y el centro de presión. La presión sigue a la tela cuando se deforma y se actualiza con
  regularidad (*frecuencia del acoplamiento*). La entrada en pérdida se aproxima panel por panel.
  El vuelo con viento alterna: orientación de la cometa al extremo de su línea, luego forma bajo
  el viento, hasta que nada se mueve de una vuelta a la siguiente.
- **El planeo.** Para cada actitud, el momento del aire respecto al centro de gravedad; el planeo
  estable está donde se anula devolviendo la cometa. La velocidad es aquella en la que el aire
  sostiene el peso; la pendiente viene de la resistencia (inducida + rozamiento estimado).
- **Procesador o tarjeta gráfica.** El cálculo funciona normalmente en el procesador, aparte,
  para que la página siga utilizable. **Cálculo en GPU** lo confía a la tarjeta gráfica (navegador
  compatible con WebGPU): mismas ecuaciones, más rápido en modelos grandes. De una máquina a otra,
  el número de iteraciones y la última cifra de los resultados pueden variar un poco.
- **Forma en reposo guardada.** El resultado en reposo se guarda en el archivo; mientras la cometa
  no cambie (salvo las bridas), el cálculo siguiente parte de él y termina rápido.

## Después del cálculo

- **Tensar los cables**: acorta los cables flojos hasta la tensión deseada.
- **Patrones planos (.dxf)**: el corte de cada panel, listo para cortar.
- **Informe de cálculo (.html)**: todos los resultados y la vista 3D, con el archivo de la cometa
  incluido (se puede recuperar desde el informe).
- **PanelSearch**: envía una vela a la herramienta compañera PanelSearch, para buscar su panelado.

## Biblioteca

Materiales, tubos y varillas, cables, tejidos y perfiles de cálculo. Una **referencia** elegida
en un elemento puede modificarse después; **Aplicar la biblioteca al proyecto** actualiza los
elementos que la siguen. Las fichas personales nunca son sobrescritas por las nuevas fichas de
fábrica.
