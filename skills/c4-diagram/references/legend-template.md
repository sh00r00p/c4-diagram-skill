# Legend Template

Place the legend in the bottom-right corner of the diagram. Adjust x/y based on diagram dimensions.

## Legend XML

```xml
<!-- Legend background -->
<mxCell id="legend_bg"
  value=""
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=#F5F5F5;strokeColor=#CCCCCC;fontSize=12;"
  vertex="1" parent="1">
  <mxGeometry x="1300" y="720" width="280" height="160" as="geometry"/>
</mxCell>

<!-- Legend title -->
<mxCell id="legend_title"
  value="&lt;b&gt;Legend&lt;/b&gt;"
  style="text;html=1;fontSize=13;fontColor=#333333;align=left;verticalAlign=top;"
  vertex="1" parent="1">
  <mxGeometry x="1310" y="725" width="100" height="20" as="geometry"/>
</mxCell>

<!-- Person -->
<mxCell id="legend_person_box"
  value=""
  style="rounded=0;whiteSpace=wrap;html=1;fillColor=#08427B;strokeColor=none;"
  vertex="1" parent="1">
  <mxGeometry x="1310" y="750" width="16" height="16" as="geometry"/>
</mxCell>
<mxCell id="legend_person_label"
  value="Person"
  style="text;html=1;fontSize=11;fontColor=#333333;align=left;verticalAlign=middle;"
  vertex="1" parent="1">
  <mxGeometry x="1334" y="748" width="100" height="20" as="geometry"/>
</mxCell>

<!-- Container -->
<mxCell id="legend_container_box"
  value=""
  style="rounded=0;whiteSpace=wrap;html=1;fillColor=#438DD5;strokeColor=none;"
  vertex="1" parent="1">
  <mxGeometry x="1310" y="774" width="16" height="16" as="geometry"/>
</mxCell>
<mxCell id="legend_container_label"
  value="Container"
  style="text;html=1;fontSize=11;fontColor=#333333;align=left;verticalAlign=middle;"
  vertex="1" parent="1">
  <mxGeometry x="1334" y="772" width="100" height="20" as="geometry"/>
</mxCell>

<!-- Database -->
<mxCell id="legend_db_box"
  value=""
  style="shape=cylinder3;whiteSpace=wrap;html=1;size=4;fillColor=#438DD5;strokeColor=none;"
  vertex="1" parent="1">
  <mxGeometry x="1310" y="798" width="16" height="16" as="geometry"/>
</mxCell>
<mxCell id="legend_db_label"
  value="Database"
  style="text;html=1;fontSize=11;fontColor=#333333;align=left;verticalAlign=middle;"
  vertex="1" parent="1">
  <mxGeometry x="1334" y="796" width="100" height="20" as="geometry"/>
</mxCell>

<!-- External System -->
<mxCell id="legend_ext_box"
  value=""
  style="rounded=0;whiteSpace=wrap;html=1;fillColor=#999999;strokeColor=none;"
  vertex="1" parent="1">
  <mxGeometry x="1310" y="822" width="16" height="16" as="geometry"/>
</mxCell>
<mxCell id="legend_ext_label"
  value="External System"
  style="text;html=1;fontSize=11;fontColor=#333333;align=left;verticalAlign=middle;"
  vertex="1" parent="1">
  <mxGeometry x="1334" y="820" width="120" height="20" as="geometry"/>
</mxCell>

<!-- Sync arrow -->
<mxCell id="legend_sync_line"
  value=""
  style="endArrow=blockThin;endFill=1;strokeColor=#404040;"
  edge="1" parent="1">
  <mxGeometry relative="1" as="geometry">
    <mxPoint x="1470" y="758" as="sourcePoint"/>
    <mxPoint x="1520" y="758" as="targetPoint"/>
  </mxGeometry>
</mxCell>
<mxCell id="legend_sync_label"
  value="Synchronous"
  style="text;html=1;fontSize=11;fontColor=#333333;align=left;verticalAlign=middle;"
  vertex="1" parent="1">
  <mxGeometry x="1524" y="748" width="90" height="20" as="geometry"/>
</mxCell>

<!-- Async arrow -->
<mxCell id="legend_async_line"
  value=""
  style="endArrow=blockThin;endFill=1;strokeColor=#404040;dashed=1;dashPattern=5 5;"
  edge="1" parent="1">
  <mxGeometry relative="1" as="geometry">
    <mxPoint x="1470" y="782" as="sourcePoint"/>
    <mxPoint x="1520" y="782" as="targetPoint"/>
  </mxGeometry>
</mxCell>
<mxCell id="legend_async_label"
  value="Asynchronous"
  style="text;html=1;fontSize=11;fontColor=#333333;align=left;verticalAlign=middle;"
  vertex="1" parent="1">
  <mxGeometry x="1524" y="772" width="90" height="20" as="geometry"/>
</mxCell>
```

## Positioning

Calculate legend position based on diagram dimensions:
- **x** = pageWidth - 300
- **y** = pageHeight - 180
- Adjust if it overlaps with elements
