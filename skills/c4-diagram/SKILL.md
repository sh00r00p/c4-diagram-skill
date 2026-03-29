---
name: c4-diagram
description: Generate C4 Container diagrams (Simon Brown standard) as editable .drawio XML files. Use when the user asks for architecture diagrams, system diagrams, C4 diagrams, container diagrams, or wants to visualize system architecture. Also use proactively when explaining systems with 3+ components where a visual would clarify the architecture.
---

# C4 Container Diagram Generator

Generate C4 Container diagrams following Simon Brown's C4 model standard, exported as editable .drawio XML files that open directly in draw.io (desktop or web).

## When to Use

**Explicit triggers:**
- User asks for a C4 diagram, container diagram, or architecture diagram
- User says "draw the architecture", "system diagram", "show me the components"
- User needs to visualize system architecture for documentation or a presentation
- User mentions draw.io, drawio, or wants an editable diagram

**Proactive triggers:**
- Explaining a system with 3+ interacting components
- Discussing microservices, APIs, databases, and their relationships
- Reviewing or designing system architecture

**Skip when:**
- User wants a simple flowchart (use Mermaid instead)
- User wants UI wireframes or mockups
- The system has fewer than 3 components

## Process

### Step 1: Gather Requirements

Identify from the conversation or ask the user:
- What system are we diagramming?
- Who are the users/actors (Person)?
- What containers exist (apps, services, databases, queues, file storage)?
- What external systems does it interact with?
- What are the key data flows and protocols?

If the user provides a spec, codebase description, or architecture overview, extract elements automatically and confirm before generating.

### Step 2: Classify Elements

Map every element to a C4 category:

| Category | Color | Shape | Description |
|----------|-------|-------|-------------|
| Person | `#08427B` (dark blue) | Stickman | Users, actors, roles |
| Container | `#438DD5` (blue) | Rounded rectangle | Applications, services, APIs |
| Database | `#438DD5` (blue) | Cylinder | Any data store (SQL, NoSQL, files) |
| Queue/Broker | `#438DD5` (blue) | Rounded rectangle with label | Message queues, event buses |
| External System | `#999999` (grey) | Rounded rectangle | Third-party services, APIs |
| System Boundary | none (transparent) | Dashed rectangle | Groups internal containers |

Reference: `references/element-templates.md` for exact draw.io XML templates.

### Step 3: Plan Layout

Apply **strict layered layout** (top to bottom):

```
Layer 1 (y ≈ 20):      Person elements (actors)
Layer 2 (y ≈ 250):     System Boundary containing internal Containers
Layer 3 (y ≈ 700+):    External Systems
```

**Layout rules:**
- Every element gets explicit x, y coordinates (no auto-layout)
- Minimum **200px horizontal gap** between elements in the same layer
- Minimum **200px vertical gap** between layers
- System boundary = dashed rectangle enclosing all internal containers with 40px padding
- Order elements left-to-right following the primary data flow direction
- Group related containers within sub-boundaries if the system has distinct subsystems
- Keep the diagram width under 1600px for readability
- Center elements horizontally within their layer

**Minimizing line crossings:**
- Place elements that communicate frequently adjacent to each other
- Route connections vertically when possible
- Avoid diagonal lines crossing other elements

### Step 4: Define Connections

For each connection, specify:
- Source and target element
- Label: action + protocol (e.g., "Reads/writes [SQL/TCP]", "Sends events [AMQP]")
- Style: **solid line** = synchronous call, **dashed line** = asynchronous (events, queues, webhooks)
- Direction: always source → target (follow data flow)

**Connection rules:**
- Every arrow must have a label (no unlabeled connections)
- Use `[Protocol]` suffix: `[REST/JSON]`, `[gRPC]`, `[SQL]`, `[AMQP]`, `[WebSocket]`
- Bidirectional flows: use two separate arrows with distinct labels
- Self-referencing: avoid (restructure the diagram instead)

### Step 5: Generate .drawio XML

Use the XML structure from `references/drawio-template.md` as the base.

Build the XML following these rules:
1. Start with the `<mxfile>` wrapper and `<mxGraphModel>` with proper dimensions
2. Add the root cells (id="0" and id="1")
3. Add system boundary rectangles first (they are parents for contained elements)
4. Add all elements with explicit geometry (x, y, width, height)
5. Add all connections with source/target references
6. Add the legend in the bottom-right corner

**Element sizing:**
- Person: 200 × 180px
- Container: 240 × 120px
- Database (cylinder): 240 × 120px
- External System: 240 × 120px
- System Boundary: calculated to enclose children + 40px padding on each side

### Step 6: Add Legend

**Every diagram must include a legend.** Place it in the bottom-right corner.

The legend must show:
- Person = dark blue stickman (#08427B)
- Container = blue rounded rect (#438DD5)
- Database = blue cylinder (#438DD5)
- External System = grey rounded rect (#999999)
- Solid arrow = synchronous flow
- Dashed arrow = asynchronous flow

Reference: `references/legend-template.md` for the exact XML.

### Step 7: Save and Validate

Save to the path requested by the user, or default to `./c4_[system_name].drawio`.

**Validation checklist:**
- [ ] All elements have explicit x, y coordinates
- [ ] Layers are top-to-bottom: Person → System Boundary → External
- [ ] System boundary encloses all internal containers
- [ ] Legend is present in bottom-right
- [ ] No overlapping elements (check coordinates + dimensions)
- [ ] Minimal line crossings
- [ ] Every connection has a label with protocol
- [ ] Solid lines = synchronous, dashed lines = asynchronous
- [ ] Font colors are white (#ffffff) on colored backgrounds
- [ ] File opens correctly in draw.io (valid XML structure)

## C4 Model Rules

Follow Simon Brown's C4 model constraints:
- **Container diagram** shows the high-level technology choices and how containers communicate
- Each container is a separately deployable/runnable unit (not a class or module)
- Do not mix C4 levels: this skill generates Container level only
- For Component-level detail inside a container, create a separate diagram
- Person elements represent roles, not individual people
- External systems are anything outside the system boundary that the team does not own

## Anti-patterns

- **NO auto-layout** — always use explicit x, y coordinates for predictable results
- **NO unlabeled arrows** — every connection needs an action and protocol
- **NO missing legend** — legend is mandatory on every diagram
- **NO cramped layout** — maintain minimum gaps between elements
- **NO mixed C4 levels** — Container level only (no classes, no infrastructure)
- **NO invisible text** — ensure font color contrasts with background
- **NO hardcoded dimensions** — calculate system boundary size from children
