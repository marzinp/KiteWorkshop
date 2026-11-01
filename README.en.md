# AtelierCV — help

[Français](README.md) · **English** · [Español](README.es.md)

AtelierCV is for drawing a kite (frame, sail, bridle) and calculating its shape: at rest, flying
in the wind or gliding. It is **a single file**: open `AtelierCV_v306.html` in a recent
browser (Chrome or Edge recommended), nothing to install.

The **`Modeles/`** folder holds a library of kites ready to open (Eddy, Edo, Flare, Sled,
Eclipse, Mouette…): **Open** button, then the `.json` file. It is the easiest way to discover the
tool, and a good starting point for a new design.

> **A tool under development.** AtelierCV is still evolving and its results are **not reliable
> as they stand**: they give **leads** (trends, comparisons between variants, which way to
> correct), to be confirmed for real. Its main limits:
> - **no simulation of the air flow**: the wind is computed with a simplified lifting-surface
>   model, without real stall, boundary layer, turbulence or wake;
> - **fully soft structures are not handled yet** (parafoils, cells): the internal pressure of
>   cells exists, but has not been validated;
> - fabric, frame and wind remain models: friction, seams, hems, connectors and real fabrics are
>   approximated.

Everywhere, the small **ⓘ** explains a setting; most values are set with a slider, and clicking
the value lets you type one (beyond the slider range if needed).

The interface is available in French, English and Spanish (choice in the header).

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
| **Frame** | Tube, Batten (in a sail pocket), Cable, Whisker (spreader), Construction line |
| **Bridling** | Bridle / line, Tail, Ballast |
| **Sails** | Shape (one click per vertex), Circle, Seam (cut into panels), Link (sail ↔ frame), Mount |

- **Planes**: Top = XY plane, sail seen from the bridle side, front of the kite at the top;
  Front = seen from the front; Side = profile. Z is vertical.
- **Points**: a point shared by several elements becomes a **node** (connector). Select it to
  choose its type: **rigid** (welded), **ball joint**, **sliding** (the element passing through
  slides in it, like in a sleeve) or **free**. A node can also be a **Fixed point** (anchored to
  the ground) or the **Ring** (where the line is attached).
- **Sail edges**: hem, sleeve on a tube, or edge tied to a cable.
- **Symmetry**: you draw the left side (negative X), the right side follows. The **Symmetrize**
  button rebuilds the right side of an existing drawing.
- **Isolate**: show only one shape to edit it, in its own plane if it is tilted.
- **Tubes and battens**: material and section from the library, **over-length** (pre-stress),
  **Straight at rest** (unticked: the drawn curve is their free shape).
- **Sails**: fabric (library), pattern, holes and reinforcements; **Keel** box (left out of the
  rest calculation) and **Cell** box (parafoil: skin inflated by the internal pressure).

## Mouse and keyboard

The same gestures work in the drawing view and in the 3D view.

| Gesture | Effect |
|---|---|
| **Click** | select; with a tool, place a point (it snaps to nearby points, midpoints and curves) |
| **Drag** a point or a handle | move it |
| **Drag on the background** | selection window: left to right = shapes fully inside, right to left = shapes touched |
| **Ctrl+click** (Cmd on Mac) | add to or remove from the selection; on the points of a selected shape: select several points |
| **Shift+click** or **right click** (without dragging) | on a curve: add a point; on a point: remove it; while drawing: cancel |
| Hold **Alt** | no snapping (point placed freely) |
| **Right drag** | rotate (3D view and perspective) or move the view (flat views) |
| **Shift+right drag**, **middle button** or **Space+drag** | move the view |
| **Wheel** | zoom (towards the cursor; in 3D towards the orange cross, the pivot) |
| **Double click** | reframe on the kite (while drawing a shape: close it) |
| **F** | put the pivot on the selection or on the point under the mouse |
| **Shift** while dragging a move handle | fine movement (÷ 10) |

| Key | Effect |
|---|---|
| **Ctrl+Z** / **Ctrl+Y** | undo / redo |
| **Delete** | delete the selection |
| **Esc** | cancel the current drawing, clear the selection, leave Isolate |
| **Enter** | close the shape being drawn (at least 3 vertices) |
| **Digits** while drawing | type an exact length, then Enter |
| **Arrows** | move the selected points (Shift: ×10) |
| **D** | duplicate the selection |
| **V** selection · **U** tube · **A** batten · **B** cable · **W** whisker · **L** line · **R** bridle · **T** shape · **O** circle · **C** seam · **K** link · **M** mount | choose the tool |

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

**Calculation profile**: Estimate (fast, coarse mesh), Standard, Precise. If in doubt about a
result, calculate again in Standard or Precise.

The calculation is a model: fabric and frame are computed properly; the air is simplified (no
stall, no boundary layer). It is mainly for **comparing variants** and finding **which way to
correct** (tension, bridle, balance).

## How it calculates

- **The model.** Each sail is cut into small triangles (the *mesh*; the higher the fineness, the
  smaller they are). The fabric has its own stiffness along the warp, the weft and the bias, and
  does not resist compression (it wrinkles). Tubes and battens are beams (tension, compression,
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

## Library

Materials, tubes and rods, cables, fabrics and calculation profiles. A **reference** chosen on an
element can be modified afterwards; **Apply the library to the project** updates the elements
that follow it. Personal entries are never overwritten by new factory entries.
