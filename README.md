# Slint Memory Game - Technical Reference

## Quick Start

### System Requirements
- Rust 1.60+
- Cargo

### Build & Run
```bash
git clone https://github.com/benitoanagua/Slint-Memory-Game.git
cd Slint-Memory-Game
cargo run --release
```

## Key Components

### 1. UI Definition (`ui/memory.slint`)
- Declares 4×4 game grid
- Implements tile animations
- Defines game state properties:
  ```slint
  in property <[TileData]> memory_tiles
  in property <bool> disable_tiles
  ```

### 2. Game Engine (`src/main.rs`)
- Manages game logic:
  ```rust
  let tiles_model = Rc::new(VecModel::from(tiles));
  main_window.set_memory_tiles(tiles_model.clone().into());
  ```
- Handles tile matching:
  ```rust
  main_window.on_check_if_pair_solved(move || {
    // Matching logic
  });
  ```

## Technical Highlights
- **Rust Backend**:
  - `rand` for tile shuffling
  - `Rc<VecModel>` for shared state
  - Weak references for UI callbacks

- **Slint Frontend**:
  - Declarative UI syntax
  - Property bindings
  - Built-in animations

## Build Options
| Command | Description |
|---------|-------------|
| `cargo build` | Debug build |
| `cargo run --release` | Optimized build |
| `cargo test` | Run unit tests |

## Project Structure
```
.
├── Cargo.toml        # Rust manifest
├── src/main.rs       # Game logic
├── ui/memory.slint   # UI definition
└── icons/            # Game assets
```

## License
MIT © 2023
