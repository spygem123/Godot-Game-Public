# Godot-Game-Public

A 3D first-person shooter in early prototype stage, built in Godot 4 using GDScript. Inspired by the fast, skill-expressive combat of **ULTRAKILL** and the roguelike structure of **Slay the Spire**.

**Gameplay previews:** [Weapons showcase](https://youtu.be/d5RYwSu9-pE) · [Combat clip](https://youtu.be/jgDfrQjyzJQ)

## Current State — Early Prototype

| System | Status |
|---|---|
| Player movement | ~90% complete |
| Weapons | 3 functional weapons |
| Enemies | 2 placeholder enemies |
| Level | 1 test map |
| Graphics | Dithering (needs some tweaks)|

## Tech Stack

| Area | Technology |
|---|---|
| Engine | Godot 4 |
| Language | GDScript |
| Version control | Git (Gitea, self-hosted) + Tailscale for remote access |
| 3D models | Blender, TrenchBroom |
| Textures | Aseprite |

## Development

Built as a 3-person team project. Key engineering focus areas:
- OOP architecture using decoupled, reusable nodes
- Modular code structure designed for multi-person collaboration
- Branch management and Git workflow across a team
- Clean code and documentation standards for shared codebases

## Architecture Highlight — Weapon System

The weapon system is a practical example of inheritance and polymorphism applied to game development.

A `BaseRevolver` abstract scene defines all shared behaviour: cooldown logic, animations, mesh, and the primary (left-click) attack — since every revolver fires the same way. Concrete revolver variants inherit from `BaseRevolver` and only override the secondary (right-click) attack, which is unique per weapon.

```
BaseRevolver  (abstract)
├── primary attack    — shared, defined once
├── cooldown logic    — shared, defined once
├── animations/mesh   — shared, defined once
└── secondary attack  — abstract, overridden per variant

RevolverA extends BaseRevolver  →  overrides secondary attack
RevolverB extends BaseRevolver  →  overrides secondary attack
RevolverC extends BaseRevolver  →  overrides secondary attack
```

This structure means adding a new revolver variant requires writing only the unique secondary attack — everything else is inherited. It also maps closely to patterns used in Java (abstract classes, method overriding), which was a deliberate design choice to reinforce OOP fundamentals across languages.

## Notes

Self-hosted on a private Gitea instance. No public repository available — this GitHub page exists to showcase the project.

This being a first game dev project for me and my team means development is rather slow (we're about 400–500 hours in), and most of that time was spent learning how to do things properly. The codebase has been rewritten three times as a result — but the upside is that in its current state, the code is largely bug-free, decently optimised, and follows OOP principles strictly throughout.

Textures and models are subpar, but they are placeholders — we have little to no experience in that side of game development.
