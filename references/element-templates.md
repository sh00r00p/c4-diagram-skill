# C4 Element Templates for draw.io

XML templates for each C4 element type. Copy and modify coordinates, IDs, and labels.

## Person (Stickman)

```xml
<mxCell id="person_1"
  value="&lt;b&gt;User Name&lt;/b&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;[Person]&lt;/font&gt;&lt;br/&gt;&lt;br/&gt;&lt;font style=&quot;font-size:11px&quot;&gt;A user of the system.&lt;/font&gt;"
  style="shape=mxgraph.c4.person2;whiteSpace=wrap;html=1;container=0;image;imageAspect=0;fillColor=#08427B;fontColor=#ffffff;fontSize=14;align=center;"
  vertex="1" parent="1">
  <mxGeometry x="360" y="20" width="200" height="180" as="geometry"/>
</mxCell>
```

- **Fill color:** `#08427B` (dark blue, per C4 standard)
- **Font color:** `#ffffff`
- **Size:** 200 x 180px
- **Shape:** `shape=mxgraph.c4.person2` (draw.io's built-in C4 person)

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

```xml
<mxCell id="conn_1"
  value="Makes API calls [REST/JSON]"
  style="endArrow=blockThin;endFill=1;fontSize=11;fontColor=#404040;strokeColor=#404040;elbow=vertical;"
  edge="1" source="person_1" target="container_1" parent="1">
  <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

- **Line:** solid
- **Arrow:** `endArrow=blockThin;endFill=1`
- **Label format:** `Action [Protocol]`

## Connection (Asynchronous)

```xml
<mxCell id="conn_2"
  value="Publishes events [AMQP]"
  style="endArrow=blockThin;endFill=1;fontSize=11;fontColor=#404040;strokeColor=#404040;dashed=1;dashPattern=5 5;elbow=vertical;"
  edge="1" source="container_1" target="container_2" parent="1">
  <mxGeometry relative="1" as="geometry"/>
</mxCell>
```

- **Line:** dashed (`dashed=1;dashPattern=5 5`)
- Everything else same as synchronous

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
