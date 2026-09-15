# UNISEFE-WEB-CAD-2D
A lightweight, direct 2D CAD application that runs entirely in the browser.

UNISEFE WEB CAD 2D was created with a simple goal: provide a technical drawing environment that is immediate, precise, easy to understand, and free from unnecessary installation steps or overly complex interfaces.






🚀 Online Demo

👉 Open UNISEFE WEB CAD 2D

No installation is required.

Open the link and start drawing.

What It Is

UNISEFE WEB CAD 2D is a technical 2D CAD application designed to run directly in the browser.

The project focuses on:

fast interaction between command and result;

geometric precision;

natural mouse-based drafting;

clear snap and reference behavior;

keyboard-based numeric input;

a minimal and readable interface;

simple distribution;

no unnecessary dependencies.

The CAD application is contained mainly inside a single self-contained HTML file.

✨ Features

browser-based 2D CAD;

clean and minimal interface;

direct technical drawing workflow;

lines;

dashed lines;

dash-dot lines;

rectangles;

circles;

arcs;

text;

linear dimensions;

aligned dimensions;

angular dimensions;

object selection;

move;

copy;

rotate;

mirror;

fillet;

trim;

extend;

erase;

undo;

geometric snaps;

endpoints;

midpoints;

centers;

quadrants;

intersections;

perpendicular references;

tangent references;

temporary geometric references;

multi-reference tracking;

magnetic guides;

keyboard input for distances, coordinates and angles;

zoom and viewport navigation;

no installation required;

self-contained HTML.

⌨️ Keyboard Input

UNISEFE WEB CAD 2D supports a keyboard-driven workflow inspired by traditional CAD systems.

Examples:

L

starts the LINE command.

100

sets a distance.

<45

locks the direction to 45° while keeping the distance controlled by the mouse.

100<45

sets a distance of 100 at an angle of 45°.

@100,50

uses relative coordinates.

@100<45

uses relative distance and angle from the previous point.

Command aliases are also available for tools such as LINE, CIRCLE, ARC, MOVE, COPY, TRIM, EXTEND, FILLET, MIRROR, ROTATE and ERASE.

🧲 Snaps and Geometric References

One of the main goals of the project is to make technical drawing feel natural even when using almost only the mouse.

The reference system allows you to:

approach a geometric snap;

temporarily acquire a reference;

move away while keeping its direction;

acquire multiple references;

combine those references to construct new points;

keep real geometric snaps distinct from temporary guide lines.

Tangent and perpendicular technical references are activated when a valid command base point already exists.

🟢 Simplified Arc Workflow

The ARC command uses a deliberately simple workflow.

define the first point;

create the chord using the same interaction model as a line;

confirm the chord;

enter the radius;

use the mouse to choose the side of the arc.

The chord can also be defined using keyboard-entered distances and angles.

Usage

Online Version

Use the application directly here:

https://riccardobasti.github.io/UNISEFE-WEB-CAD-2D/

Local Version

Download or clone the repository and open:

index.html

with a modern browser.

No libraries, runtimes or local servers are required.

📁 Project Structure

UNISEFE-WEB-CAD-2D/
├── index.html
└── README.md

The project is intentionally kept simple.

Most of the CAD application lives directly inside index.html.

🧠 Philosophy

UNISEFE WEB CAD 2D is based on a few simple principles:

Fewer steps between command and result.

An interface that stays understandable while you work.

Precision without making the workflow heavy.

No unnecessary dependencies.

No mandatory installation.

Code that is easy to distribute.

Direct browser execution.

The goal is not to fill the interface with features, but to build a small, coherent and enjoyable CAD environment.

⚙️ Technical Structure

The project is organized as a small CAD framework inside a single HTML document.

Its main logical areas include:

Canonical State
Geometry
Delta-Zero Point Closure
Snap Engine
Multi-Reference Tracking
Technical Guides
Entity Model
SVG Projection
CAD Commands
Keyboard Input
Pointer Input
Persistence
Integrity Tests
Public API

The interface remains static HTML, while JavaScript handles the CAD runtime, input, geometry, SVG projection and required operations.

🧪 Project Status

Current version: v0.0.4 Alpha

The project is under active development.

The objective is to progressively improve:

precision;

ease of use;

geometric reference quality;

CAD tools;

performance;

browser compatibility;

while keeping the application lightweight.

🤝 Contributing

Contributions, testing, bug reports and proposals are welcome.

You can:

open an Issue;

suggest an improvement;

Fork the repository;

submit a Pull Request.

Contributions are especially useful in areas such as:

2D drawing tools;

snapping and precision;

geometric references;

dimensions and measurements;

selection;

import/export;

usability;

performance;

browser compatibility.

🐞 Bug Reports

When reporting a problem, please include, when possible:

Browser:
Command used:
Steps to reproduce:
Expected result:
Actual result:

Screenshots and small geometric examples are especially useful.

Author

ITALFABER / UNISEFE

Repository:

https://github.com/riccardobasti/UNISEFE-WEB-CAD-2D

Demo:

https://riccardobasti.github.io/UNISEFE-WEB-CAD-2D/

## Technical Comparison

The table below compares the current **UNISEFE CAD 2D Alpha**
with established 2D CAD systems.

This is not intended as a claim of overall superiority.
It compares architectural characteristics and currently available capabilities.

| Area | UNISEFE CAD 2D | AutoCAD Web | QCAD | LibreCAD | DraftSight |
|---|---|---|---|---|---|
| Runs directly in browser | **Yes** | **Yes** | No | No | No |
| Single static HTML possible | **Yes** | No | No | No | No |
| Backend required for core CAD | **No** | Yes | No | No | No |
| Line / Arc / Circle | **Yes** | Yes | Yes | Yes | Yes |
| Dashed / dash-dot lines | **Yes** | Yes | Yes | Yes | Yes |
| Object snap | **Yes** | Yes | Yes | Yes | Yes |
| Midpoint / intersection snap | **Yes** | Yes | Yes | Yes | Yes |
| Perpendicular / tangent snap | **Yes** | Yes | Yes | Yes | Yes |
| Move / Copy | **Yes** | Yes | Yes | Yes | Yes |
| Rotate / Mirror | **Yes** | Yes | Yes | Yes | Yes |
| Trim / Extend | **Yes** | Yes | Yes | Yes | Yes |
| Fillet | **Yes** | Yes | Yes | Yes | Yes |
| Linear dimensions | **Yes** | Yes | Yes | Yes | Yes |
| Angular dimensions | **Yes** | Yes | Yes | Yes | Yes |
| Progressive / aligned dimensions | **Yes** | Yes | Yes | Yes | Yes |
| Text | **Yes** | Yes | Yes | Yes | Yes |
| Undo | **Yes** | Yes | Yes | Yes | Yes |
| Save / Open | **Yes** | Yes | Yes | Yes | Yes |
| Native browser printing / PDF | **Yes** | Yes | Yes | Yes | Yes |
| Automatic `Δ = 0` coincidence logic | **Yes** | Constraint workflow | No native equivalent | No native equivalent | Constraint workflow |
| CAD state inspectable as web markup | **Yes** | No | No | No | No |
| Geometry/state in same document | **Yes** | No | No | No | No |
| No installation required | **Yes** | **Yes** | No | No | No |
| Offline standalone file | **Yes** | No* | Yes | Yes | Yes |
| External CAD engine required | **No** | Autodesk platform | QCAD engine | LibreCAD engine | DraftSight engine |
| Current maturity | **Alpha** | Production | Production | Production | Production |

\* AutoCAD Web itself is cloud-based; Autodesk documents offline work for the mobile application.

### Architectural Difference

UNISEFE CAD 2D is intentionally much smaller than mature CAD platforms.

Its distinctive characteristic is that the CAD does not live behind a separate application or geometric service.

Geometry, state, relationships and interface can coexist inside one standalone HTML document.

The same file can therefore act as:

- the application;
- the drawing environment;
- the geometric state;
- the runtime;
- and the portable document.

The current Alpha should not be interpreted as feature-complete compared with mature CAD products.
Its focus is on minimizing the number of architectural layers required to obtain a functional CAD environment.

UNISEFE WEB CAD 2D — Technical drawing, directly in the browser.
