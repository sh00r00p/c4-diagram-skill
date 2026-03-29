# C4 Element Templates for draw.io

XML templates for each C4 element type. Copy and modify coordinates, IDs, and labels.

## Person (Actor + Label)

**IMPORTANT:** Do NOT use `shape=mxgraph.c4.person2` — it requires the C4 shape library which is NOT loaded by default in draw.io desktop or web. Use the built-in `shape=actor` (stickman) with a separate text label below.

```xml
<!-- Actor figure (built-in stickman, always renders without plugins) -->
<mxCell id="person_1"
  value=""
  style="shape=actor;whiteSpace=wrap;html=1;fillColor=#08427B;strokeColor=#052E56;"
  vertex="1" parent="1">
  <mxGeometry x="380" y="20" width="40" height="60" as="geometry"/>
</mxCell>
<!-- Label below the actor -->
<mxCell id="person_1_label"
  value="&lt;b&gt;User Name&lt;/b&gt;&lt;br/&gt;&lt;font style=&quot;font-size:10px;color:#666666&quot;&gt;[Person]&lt;/font&gt;&lt;br/&gt;&lt;font style=&quot;font-size:10px;color:#666666&quot;&gt;A user of the system.&lt;/font&gt;"
  style="text;html=1;fontSize=12;align=center;verticalAlign=top;"
  vertex="1" parent="1">
  <mxGeometry x="290" y="85" width="220" height="60" as="geometry"/>
</mxCell>
```

- **Fill color:** `#08427B` (dark blue, per C4 standard)
- **Actor size:** 40 x 60px (compact stickman)
- **Label:** separate text cell, centered below actor, 220px wide
- **Shape:** `shape=actor` (built-in, always available)

## Container (Application / Service)

```xml
<mxCell id="container_1"
  value="&lt;b&gt;API Application&lt;/b&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;[Container: Python/FastAPI]&lt;/font&gt;&lt;br/&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;Provides routing optimization via REST API.&lt;/font&gt;"
  style="rounded=1;whiteSpace=wrap;html=1;container=0;fillColor=#438DD5;fontColor=#ffffff;strokeColor=none;fontSize=14;align=center;"
  vertex="1" parent="1">
  <mxGeometry x="100" y="300" width="240" height="120" as="geometry"/>
</mxCell>
```

- **Fill color:** `#438DD5` (blue, per C4 standard)
- **Font color:** `#ffffff`
- **Size:** 240 x 120px
- **Style:** `rounded=1` for rounded corners

## Container (Database / Data Store)

```xml
<mxCell id="db_1"
  value="&lt;b&gt;Database&lt;/b&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;[Container: PostgreSQL]&lt;/font&gt;&lt;br/&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;Stores orders, routes, and user data.&lt;/font&gt;"
  style="shape=cylinder3;whiteSpace=wrap;html=1;boundedLbl=1;backgroundOutline=1;size=15;fillColor=#438DD5;fontColor=#ffffff;strokeColor=none;fontSize=14;align=center;"
  vertex="1" parent="1">
  <mxGeometry x="400" y="300" width="240" height="120" as="geometry"/>
</mxCell>
```

- **Shape:** `shape=cylinder3` for the classic database cylinder
- **Size:** 240 x 120px (same as containers for visual consistency)

## External System

```xml
<mxCell id="ext_1"
  value="&lt;b&gt;External System&lt;/b&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;[External System]&lt;/font&gt;&lt;br/&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;Third-party payment processor.&lt;/font&gt;"
  style="rounded=1;whiteSpace=wrap;html=1;container=0;fillColor=#999999;fontColor=#ffffff;strokeColor=none;fontSize=14;align=center;"
  vertex="1" parent="1">
  <mxGeometry x="100" y="700" width="240" height="120" as="geometry"/>
</mxCell>
```

- **Fill color:** `#999999` (grey, per C4 standard)
- **Font color:** `#ffffff`

## System Boundary (Dashed Rectangle)

```xml
<mxCell id="boundary_1"
  value="System Name [Software System]"
  style="rounded=1;whiteSpace=wrap;html=1;fillColor=none;strokeColor=#444444;strokeWidth=2;dashed=1;fontSize=16;fontStyle=1;verticalAlign=top;align=left;spacingLeft=10;spacingTop=10;fontColor=#444444;"
  vertex="1" parent="1">
  <mxGeometry x="60" y="250" width="800" height="400" as="geometry"/>
</mxCell>
```

- **Fill:** none (transparent)
- **Stroke:** `#444444`, dashed, width 2
- **Label:** top-left, bold
- **Size:** calculated to enclose all children with 40px padding

## Connection (Synchronous)

**IMPORTANT:** Always include `labelBackgroundColor=#ffffff` so labels remain readable when crossing other elements. Use explicit `exitX/exitY` and `entryX/entryY` to control attachment points and prevent arrows from crossing unrelated containers. Use `y` offset in mxGeometry to push labels away from the arrow center (negative = above, positive = below for horizontal arrows).

```xml
<mxCell id="conn_1"
  value="Makes API calls [REST/JSON]"
  style="endArrow=blockThin;endFill=1;fontSize=10;fontColor=#404040;strokeColor=#404040;labelBackgroundColor=#ffffff;exitX=1;exitY=0.5;exitDx=0;exitDy=0;entryX=0;entryY=0.5;entryDx=0;entryDy=0;"
  edge="1" source="person_1" target="container_1" parent="1">
  <mxGeometry y="-15" relative="1" as="geometry">
    <mxPoint as="offset"/>
  </mxGeometry>
</mxCell>
```

- **Line:** solid
- **Arrow:** `endArrow=blockThin;endFill=1`
- **Label format:** `Action [Protocol]`
- **Label background:** `labelBackgroundColor=#ffffff` (mandatory)
- **Offset:** `y="-15"` pushes label above the line; `y="15"` pushes below

## Connection (Asynchronous)

```xml
<mxCell id="conn_2"
  value="Publishes events [AMQP]"
  style="endArrow=blockThin;endFill=1;fontSize=10;fontColor=#404040;strokeColor=#404040;dashed=1;dashPattern=5 5;labelBackgroundColor=#ffffff;exitX=0.5;exitY=1;exitDx=0;exitDy=0;entryX=0.5;entryY=0;entryDx=0;entryDy=0;"
  edge="1" source="container_1" target="container_2" parent="1">
  <mxGeometry y="15" relative="1" as="geometry">
    <mxPoint as="offset"/>
  </mxGeometry>
</mxCell>
```

- **Line:** dashed (`dashed=1;dashPattern=5 5`)
- Everything else same as synchronous (including `labelBackgroundColor`)

## Label Format

All C4 elements follow this label structure:

```
<b>Element Name</b>
[Type: Technology]

Short description of responsibility.
```

In HTML encoding for draw.io:
```
&lt;b&gt;Name&lt;/b&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;[Type: Tech]&lt;/font&gt;&lt;br/&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;Description.&lt;/font&gt;
```
