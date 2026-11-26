# AtelierCV — help

[Français](README.md) · **English** · [Español](README.es.md)

AtelierCV is for drawing a kite (frame, sail, bridle) and calculating its shape: at rest, flying
in the wind or gliding. It is **a single file**: open `AtelierCV_v623.html` in a recent
browser (Chrome or Edge recommended), nothing to install.

The **`Modeles/`** folder holds a library of kites ready to open (Eddy, Edo, Flare, Sled,
Eclipse, Mouette…): **Open** button, then the `.json` file. It is the easiest way to discover the
tool, and a good starting point for a new design.

> **A tool under development.** AtelierCV is still evolving and its results are **not reliable
> as they stand**: they give **leads** (trends, comparisons between variants, which way to
> correct), to be confirmed for real. Its main limits:
> - **the air flow is simulated only as a trial**: wind flight uses a simplified lifting-surface
>   model, without real stall, boundary layer, turbulence or wake; the built-in wind tunnel
>   simulates the flow, but is still a trial (see "State of each part");
> - **fully soft structures are not handled yet** (parafoils, cells): the internal pressure of
>   cells exists, but has not been validated;
> - fabric, frame and wind remain models: friction, seams, hems, connectors and real fabrics are
>   approximated.

Everywhere, the small **ⓘ** explains a setting; most values are set with a slider, and clicking
the value lets you type one (beyond the slider range if needed).

The interface is available in French, English and Spanish (choice in the header).

## State of each part

**Solid** — use with confidence, within the limits above:
- drawing by planes, symmetry, "Vérifier" and "Symétriser", panels and seams, cutting rods and joints;
- rest shape: frame, fabric, cables and bridles;
- flat patterns (.dxf), calculation report, materials library.

**Delicate** — works on most models, look at the results closely:
- wind flight: on a soft kite, shape and orientation may keep oscillating ("équilibre oscillant":
  the verdict is on the average), or the coupling may give up ("tours alternés": approximate result);
- stability probes (pitch, roll, yaw);
- gliding flight and its optimisation;
- GPU calculation: faster, but some models (long tail, Dazzle) are safer on the CPU.

**Experimental** — a lead, not a measurement:
- built-in wind tunnel: well tested for the force of a tail (Dazzle, Kiteman); pressure exchanges
  for a kite without a tail are still a trial;
- tail approximated by ribbons (without a compatible graphics card): within ± 25 % of the wind tunnel;
- internal pressure of cells; export to FluidX3D;
- exchanges with PanelSearch (not much tested yet).

## The screen

- **Left — Drawing**: layers, tools, settings of what is selected.
- **Centre — Calculation**: calculation conditions, the **Calculate** button, then the results
  (tensions, forces in tubes and cables, masses, wind, advice).
- **Right — the views**: the flat drawing (Top, Front, Side) and the 3D view, which shows the
  result (colours = fabric tension; tubes blue in compression, red in tension).

At the top: New, Open, Save (.json), exports (flat patterns as DXF, calculation report as HTML,
bill of materials), the library, the language, the theme, Undo (Ctrl+Z).

## Drawing

You work on one layer at a time; the others stay visible and can be snapped to.

| Layer | Tools |
|---|---|
| **Frame** | Rod (tube, solid rod or flat batten), Cable, Construction line |
| **Bridling** | Bridle / line, Tail, Ballast |
| **Sails** | Shape (one click per vertex), Circle, Seam (cut into panels), Link (sail ↔ frame), Mount |

- **Planes**: Top = XY plane, sail seen from the bridle side, front of the kite at the top;
  Front = seen from the front; Side = profile. Z is vertical.
- **Points**: a point shared by several elements becomes a **node** (connector). Select it to
  choose its type: **rigid** (welded), **ball joint**, **sliding** (the element passing through
  slides in it, like in a sleeve) or **free**. A node can also be a **Fixed point** (anchored to
  the ground) or the **Ring** (where the line is attached).
- **Sail edges**: hem, sleeve on a rod, or edge tied to a cable.
- **Symmetry**: you draw the left side (negative X), the right side follows. The **Symmetrize**
  button rebuilds the right side of an existing drawing.
- **Isolate**: show only one shape to edit it, in its own plane if it is tilted.
- **Rods**: material and section from the library, **over-length** (pre-stress), **Straight at
  rest** (unticked: the drawn curve is its free shape), and **how the sail holds it**: at the ends
  only (with or without ball joints: spreader, whisker), at intermediate nodes, bearing (upper or
  lower side, sail attached or not), open sleeve (at one end or both), closed sleeve (batten: the
  over-length tensions the sail).
- **Sails**: fabric (library), pattern, holes and reinforcements; **Keel** box (left out of the
  rest calculation) and **Cell** box (parafoil: skin inflated by the internal pressure).

## Mouse and keyboard

The same gestures work in the drawing view and in the 3D view.

| Gesture | Effect |
|---|---|
| **Click** | select a whole shape, whatever its layer (the active layer comes first, then switches to the shape's layer); with a tool, place a point (it snaps to nearby points, midpoints and curves) |
| **Drag** a selected shape | move it (shapes attached at its nodes follow; if their family is hidden, they stay visible as dashed lines while the shape is selected) |
| **Handles** of the selection frame | squares: scale (corner: proportional, side: one direction, from the opposite corner or side); **click again** on the shape: rotation at the corners (Shift: by 15°), skew at the sides, movable rotation centre (snaps to points). Flat views only; a shape on the axis only rotates in the Side view |
| **Click** a node (small grey square) | select it to set it (joint, fixed point, ring, junction); click again: next shape. To move it: double-click one of its shapes, then drag it (the shapes sharing it follow) |
| **Gizmo X, Y arrows** (bottom left of the frame) | move the selection along a single axis; dashed arrow: in depth |
| **Drag on the background** or on an unselected shape | move the view |
| **Ctrl+drag** (Cmd on Mac) | selection window: left to right = shapes fully inside, right to left = shapes touched |
| **Ctrl+click** | add to or remove from the selection; when editing points: select several points |
| **Double click** a shape | edit its points (curve handles included); **Esc** or a click on the background to finish (dragging on the background pans without leaving). Nodes (shared points) are squares, control points are circles. Drag the curve: it bends to pass through the mouse. A point can be corner (Casser), smooth or symmetric (handles of equal length) |
| **Double click**, when editing points | on a point: remove it from this shape (a node stays on the others); on the curve: add a point (on a crossing: node shared by both curves). Quick double click only: a slower second click picks the point up |
| **Right click** (without dragging) | on a sail edge: its menu (hem, sleeve, cable, seam); while drawing: cancel |
| Hold **Alt** | no snapping (point placed freely); **Alt+click**: the shape underneath |
| **Right drag** | rotate (3D view and perspective) or move the view (flat views) |
| **Shift+right drag**, **middle button** or **Space+drag** | move the view |
| **Wheel** | zoom (towards the cursor; in 3D towards the orange cross, the pivot) |
| **Double click on the background** | reframe on the kite (while drawing a shape: close it) |
| **F** | put the pivot on the selection or on the point under the mouse |
| **Shift** while dragging the depth arrow | fine movement (÷ 10) |

| Key | Effect |
|---|---|
| **Ctrl+Z** / **Ctrl+Y** | undo / redo |
| **Delete** | delete the selection |
| **Esc** | finish editing points, cancel the current drawing, clear the selection, leave Isolate |
| **Enter** | close the shape being drawn (at least 3 vertices) |
| **Digits** while drawing | type an exact length, then Enter |
| **Arrows** | move the selected shape, or when editing points the selected point (1 mm, Shift: 10 mm, no snapping) |
| **D** | duplicate the selection |
| **V** selection · **U** rod · **B** cable · **L** line · **R** bridle · **T** shape · **O** circle · **C** seam | choose the tool |

## Check before calculating

**Check the drawing** lists what would prevent a sound calculation: points not joined, cables
passing through a loose point, inconsistent patterns, kinked battens, duplicate names… Most lines
have a button that fixes it (Join, Recut on the frame, Align, Rename…).

## Calculating

Choose the conditions in the centre, then **Calculate**:

- **At rest (on the ground)**: the shape under pre-stress alone (over-lengths, cable tension).
  Keels are left out. A kite without a frame (parafoil) has no rest shape.
  The rest shape found is kept in the file: the next calculation starts from it.
- **Held by the line (pull)**: a pull spread over the fabric, opposite to the line.
- **In flight, horizontal head wind**: the real wind (speed in km/h); the kite finds its
  orientation at the end of its line, then its shape under the wind, round after round. The
  results give the flight quality, bridle advice and stability (yaw, roll, pitch). Options:
  weight, tails, bridle drag.
- **Glide (no line)**: the attitude at which the kite glides stably, its speed, slope and
  glide ratio (adjustable fabric friction), the polar, the best glide and the **balance**: how far
  to move the centre of gravity, and how much ballast to put at the nose or at the rear.
  The **Optimise the glide** button adjusts the mass of the ballast (the only one, or the one ticked "To optimise") through
  real glide calculations, try after try, up to the best glide ratio in a stable glide; the other
  ballasts (for instance the weight of the line at the ring) stay fixed. If the ballast hangs at the ring,
  a second pass slides the ring along the bridle, mass fixed. The drawing only changes
  with "Apply".

**Calculation profile**: Estimate (fast, coarse mesh), Standard, Precise. If in doubt about a
result, calculate again in Standard or Precise.

The calculation is a model: fabric and frame are computed properly; the air is simplified (no
stall, no boundary layer). It is mainly for **comparing variants** and finding **which way to
correct** (tension, bridle, balance).

## How it calculates

- **The model.** Each sail is cut into small triangles (the *mesh*; the higher the fineness, the
  smaller they are). The fabric has its own stiffness along the warp, the weft and the bias, and
  does not resist compression (it wrinkles); it also has a small bending stiffness, like a sheet of
  paper (set per fabric, measurable by the cantilever test), which matters mostly for light,
  barely tensioned gliders. Tubes and battens are beams (tension, compression,
  bending, torsion); cables, bridles and hems only work in tension. Connectors join all this
  according to their type.
- **Finding the equilibrium (dynamic relaxation).** The calculation moves all the nodes step by
  step, like an object let go that settles, until the forces cancel out everywhere. Each step is
  an **iteration**.
  - **Tolerance**: the force imbalance accepted at the end, relative to the kite's loads
    (0.001 = 0.1 %). Smaller = more accurate, but longer.
  - **Max iterations**: the calculation stops there if it has not finished ("not converged").
  - **Buckling trigger**: a tiny initial defect, so that an over-compressed tube buckles on the
    right side instead of staying straight in unstable equilibrium; a probe then checks that no
    tube stayed straight beyond its buckling load.
  - **Lightened masses**: a solver setting that speeds up convergence; it does not change the
    result.
- **The wind (vortex ring method).** The surface is cut into panels, each carrying a vortex;
  from them come the pressure on each panel, hence lift, induced drag and centre of pressure.
  The pressure follows the fabric as it deforms and is updated regularly (*coupling frequency*).
  Stall is approximated panel by panel. Wind flight alternates: orientation of the kite at the end
  of its line, then shape under the wind, until nothing moves any more from one round to the next.
- **Gliding.** For each attitude, the moment of the air about the centre of gravity; stable
  gliding is where it vanishes while bringing the kite back. The speed is the one at which the air
  carries the weight; the slope comes from the drag (induced + estimated friction).
- **Processor or graphics card.** The calculation normally runs on the processor, separately, so
  the page stays usable. **GPU calculation** hands it to the graphics card (WebGPU-capable
  browser): same equations, faster on large models. From one machine to another, the number of
  iterations and the last digit of the results may vary slightly.
- **Saved rest shape.** The rest result is kept in the file; as long as the kite has not changed
  (bridles excepted), the next calculation starts from it and finishes quickly.

## After the calculation

- **Tension the cables**: shortens slack cables until they reach the target tension.
- **Flat patterns (.dxf)**: the cut of each panel, ready for cutting.
- **Calculation report (.html)**: all the results and the 3D view, with the kite file included
  (it can be retrieved from the report).
- **PanelSearch**: sends a sail to the companion tool PanelSearch, to search for its panelling.

## Built-in wind tunnel (trial)

AtelierCV has its own wind tunnel (built into the AtelierCV file): it computes the
air around the sail on the graphics card (WebGPU-capable browser) and opens next to the drawing.
- **Kite with a tail** (tail setting on "soufflerie"): "Calculer" sends the kite, the wind tunnel measures the force
  of the flapping tail, then AtelierCV applies it at the tail attachments in wind flight. This is the best-tested use
  (Dazzle, Kiteman). Without a compatible graphics card, the tail is approximated by ribbons.
- **Kite without a tail**: "Envoyer à la soufflerie", or "Échanges de pression avec la soufflerie" to redo the wind
  flight with the measured pressure until the forces settle. Still experimental.
- Resolution follows the calculation profile: 32 cells in Estimation, 48 in Standard, 64 in Précis.

## FluidX3D virtual wind tunnel

FluidX3D is an airflow simulator running on the graphics card, written by Moritz Lehmann
(https://github.com/ProjectPhysX/FluidX3D). It is free for personal, educational or public research use;
commercial or military use is not allowed (see LICENSE.md in FluidX3D). AtelierCV does not include it: you install
and compile it once. After that, every kite goes into the tunnel without recompiling.

### What you need

- An OpenCL-capable graphics card (NVIDIA, AMD or Intel) with an up-to-date driver; 4 GB of video memory or more recommended.
- Windows: Visual Studio Community (free), with the "Desktop development with C++" workload.
- Linux: g++, make and the card's OpenCL driver (package ocl-icd-opencl-dev, plus the vendor driver).

### Installation (once)

1. Download FluidX3D: on its GitHub page, "Code" button then "Download ZIP", and unzip it.
2. In AtelierCV: **Alt + click** on Export → "Wind tunnel FluidX3D (.stl)". Besides the kite files,
   you get the setup `atelier_fluidx3d.cpp` and this guide.
3. Open `FluidX3D/src/setup.cpp`. It holds a series of example `void main_setup()` functions, all between `/*` and `*/`
   except one: comment that one out too, then paste the whole content of `atelier_fluidx3d.cpp` at the end of the file.
4. Open `FluidX3D/src/defines.hpp`:
   - comment out (add `//` in front): `#define BENCHMARK`
   - enable (remove the `//` in front): `#define FP16S`, `#define EQUILIBRIUM_BOUNDARIES`, `#define SUBGRID`,
     `#define FORCE_FIELD`, `#define INTERACTIVE_GRAPHICS`
5. Compile:
   - Windows: open `FluidX3D.sln` in Visual Studio, choose "Release", then Debug → Start Without Debugging (Ctrl + F5).
   - Linux: in `make.sh`, choose the compile line "with X11" (interactive window), then run `./make.sh`.

On the very first run, FluidX3D does not find a kite yet: that is normal.

### For each kite

1. In AtelierCV, compute the shape, preferably in wind flight, then Export → "Wind tunnel FluidX3D (.stl)" (plain click).
2. Copy `atelier_soufflerie.txt` into `FluidX3D/stl/` (create the folder if missing), replacing the old one. This single file holds the settings, then the sail and the frame.
3. Run FluidX3D again (`FluidX3D.exe` in `FluidX3D/bin/`, or Ctrl + F5 in Visual Studio). No need to recompile.

In the window: P starts or pauses, H shows the key help, keys 1 to 7 change the display
(streamlines, vortices…). The console regularly prints drag, lift and their coefficients.

### Settings at the top of atelier_soufflerie.txt (no recompiling)

- `n`: resolution, in cells along the kite's length (75 by default). Memory grows like n³, computing time roughly like n⁴.
- `amont`, `aval`, `largeur`, `hauteur`: tunnel size in kite lengths — upstream, downstream, width, height (1, 2.5, 2.5, 2.5).
  Keep at least 1 upstream.
- `d`: number of domains, to force how the grid is split (otherwise worked out from the graphics card).

### Reading the results

- Compare mostly in relative terms (two settings of the same kite): at these sizes, absolute values stay approximate.
- Tubes are thickened so the grid can see them: their drag is overestimated.
- Bridles are not in the tunnel: add their drag, given by AtelierCV ("Bridle drag and weight").

## Library

Materials, tubes and rods, cables, fabrics and calculation profiles. A **reference** chosen on an
element can be modified afterwards; **Apply the library to the project** updates the elements
that follow it. Personal entries are never overwritten by new factory entries.
