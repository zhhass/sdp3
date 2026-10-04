# Assignment 3 | Bridge Pattern

- **Name:** Tolegen Zhassulan
- **Group:** SE-2526
- **Topic:** A (Drawing)
- **Repository:** <GitHub repository URL>
- **Base commit (working I1/I2 version):** `d6b745f73098c7814d2cf81aba94c061d7473001`

## Role map

| Role | Class | Source path |
|---|---|---|
| Abstraction | `Shape` | src/bridge/Shape.java |
| A1 | `Circle` (radius 2) | src/bridge/Circle.java |
| A2 | `Square` (side 3) | src/bridge/Square.java |
| Implementor | `Renderer` | src/bridge/Renderer.java |
| I1 | `VectorRenderer` | src/bridge/VectorRenderer.java |
| I2 | `RasterRenderer` | src/bridge/RasterRenderer.java |
| I3 (extension) | `AsciiRenderer` | src/bridge/AsciiRenderer.java |
| Client | `Main` | src/Main.java |

Where to look in the code:

- Bridge field: `private Renderer renderer` in `Shape`
- `execute()`: abstract in `Shape`, implemented in `Circle` and `Square`; both call `draw(...)`, which calls `renderer.render(...)`
- `setImplementation(Renderer)`: in `Shape`
- T5 check: `checkRuntimeSwitch` in `Main`

## Run

```
javac --release 17 -encoding UTF-8 -d out "@sources.txt"
java -cp out Main --demo
```

## Expected results

| Check | Expected result |
|---|---|
| T1 | `VECTOR circle radius=2` |
| T2 | `RASTER circle radius=2 bitmap=4x4` |
| T3 | `VECTOR square side=3` |
| T4 | `RASTER square side=3 bitmap=6x6` |
| T5 | sameObject=true, stateUnchanged=true, before=`VECTOR circle radius=2`, after=`RASTER circle radius=2 bitmap=4x4` |
| T6 | `ASCII circle radius=2 art=##` |
| T7 | `ASCII square side=3 art=###` |

Last line: `SUMMARY: 7/7 PASS`

## Extension

`extension.diff` was created with `git diff d6b745f73098c7814d2cf81aba94c061d7473001 HEAD -- src`. Only `src/Main.java` and the new `src/bridge/AsciiRenderer.java` changed.
