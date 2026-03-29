# draw.io XML Template

Base XML structure for C4 Container diagrams.

## Complete File Template

```xml
<mxfile host="app.diagrams.net" agent="C4 Diagram Skill" version="24.0.0" type="device">
  <diagram id="c4-container" name="C4 Container Diagram">
    <mxGraphModel dx="1422" dy="900" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1600" pageHeight="900" math="0" shadow="0">
      <root>
        <mxCell id="0"/>
        <mxCell id="1" parent="0"/>

        <!-- ======================================== -->
        <!-- LAYER 1: Persons (top, y ≈ 20)           -->
        <!-- ======================================== -->

        <!-- Person elements go here -->

        <!-- ======================================== -->
        <!-- LAYER 2: System Boundary (y ≈ 250)       -->
        <!-- ======================================== -->

        <!-- System boundary rectangle first -->
        <!-- Then container elements inside -->

        <!-- ======================================== -->
        <!-- LAYER 3: External Systems (y ≈ 700+)     -->
        <!-- ======================================== -->

        <!-- External system elements go here -->

        <!-- ======================================== -->
        <!-- CONNECTIONS                               -->
        <!-- ======================================== -->

        <!-- All connections go here -->

        <!-- ======================================== -->
        <!-- LEGEND (bottom-right corner)              -->
        <!-- ======================================== -->

        <!-- Legend goes here (see legend-template.md) -->

      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

## Page Dimensions

| Diagram Size | pageWidth | pageHeight | dx | dy |
|-------------|-----------|------------|-----|-----|
| Small (3-5 elements) | 1200 | 800 | 1200 | 800 |
| Medium (6-12 elements) | 1600 | 900 | 1422 | 900 |
| Large (13+ elements) | 2000 | 1200 | 2000 | 1200 |

Adjust `pageWidth`, `pageHeight`, `dx`, and `dy` based on the number of elements.

## ID Convention

Use meaningful prefixes for element IDs:
- `person_1`, `person_2` for Person elements
- `container_1`, `container_2` for Container elements
- `db_1`, `db_2` for Database elements
- `ext_1`, `ext_2` for External Systems
- `boundary_1` for System Boundary
- `conn_1`, `conn_2` for Connections
- `legend` for the Legend group

## Coordinate System

- Origin (0, 0) is top-left
- X increases to the right
- Y increases downward
- All values in pixels
- Use grid-aligned values (multiples of 10) for clean layout
