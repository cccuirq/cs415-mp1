# Infinite Matrix

An endless top-down arcade dodge game built in Unreal Engine from Epic's
"Infinite Matrix" tutorial. You control a player pawn gliding across an
infinite grid, dodging the holes in the floor. Fall through a hole and it's
game over — see how long you can survive.

## Gameplay

- Move the player around the matrix to avoid the holes.
- The tunnel keeps spawning new segments endlessly, so there is no finish line.
- Fall through a hole and a restart screen appears.

## Controls

| Input      | Action              |
| ---------- | ------------------- |
| Mouse move | Move player (2D)    |

Movement is mapped in `Config/DefaultInput.ini`:
- `MoveRight` → `Mouse X`
- `MoveUp` → `Mouse Y`

## Requirements

- **Unreal Engine 5.8** (recommended; the project was originally authored in
  UE 4.17 and will prompt to convert on first open).
- **Git LFS** — the binary assets (`.uasset` / `.umap`) are stored via
  [Git Large File Storage](https://git-lfs.com/).

## Getting Started

1. **Clone the repo (with LFS):**
   ```bash
   git clone https://github.com/cccuirq/cs415-mp1.git
   cd cs415-mp1
   git lfs install
   git lfs pull
   ```
   If you cloned without LFS, run `git lfs pull` to download the real asset
   files (otherwise the `.uasset` files will be tiny pointer files).

2. **Open the project** in Unreal Engine 5.8:
   - Launch UE 5.8 and open `InfiniteMatrix.uproject`, or
   - double-click `InfiniteMatrix.uproject` in the project folder.

3. On first open, UE will warn that the project was made with an older engine
   version. Choose to convert it (UE will make a copy or upgrade in place).

4. Press **Play** in the editor. The default map is
   `Content/InfiniteMatrix/Maps/TutorialMap`.

> **Tip:** This is a Blueprint-only project (there is no `Source/` folder), so
> no C++ compilation or "Generate Project Files" step is required.

## Project Structure

```
InfiniteMatrixStarter/
├── InfiniteMatrix.uproject      # Project descriptor
├── Config/                      # Engine/game/input settings
└── Content/InfiniteMatrix/
    ├── Blueprints/
    │   ├── BP_Player            # Player pawn (mouse-controlled)
    │   ├── BP_Tunnel            # Single tunnel segment
    │   ├── BP_TunnelSpawner     # Spawns endless tunnel segments
    │   └── GM_Tutorial          # Game mode
    ├── Maps/
    │   └── TutorialMap          # The only level
    ├── Materials/
    │   ├── M_TunnelBase / MI_Tunnel   # Tunnel surface
    │   └── M_HoleBase / MI_Hole       # Hole surface
    ├── Meshes/
    │   ├── SM_Tunnel            # Tunnel floor mesh
    │   └── SM_Hole_01..04       # Hole meshes
    ├── Textures/
    │   ├── T_Binary             # Binary-style texture
    │   └── T_Noise              # Noise texture
    └── UI/
        ├── WBP_Restart          # Restart screen widget
        └── T_Restart            # Restart button texture
```

## Git & Large Files

- `.gitignore` excludes Unreal-generated folders (`Binaries/`, `DerivedDataCache/`,
  `Intermediate/`, `Saved/`, `Build/`) and macOS `.DS_Store` files.
- `.gitattributes` routes binary assets (`.uasset`, `.umap`, textures, meshes,
  audio, etc.) through Git LFS to keep the repository small.

## Credits

Based on Epic Games' "Infinite Matrix" tutorial project.
