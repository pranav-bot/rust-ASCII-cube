# 3D Rotating Cube in ASCII Art

This Rust program demonstrates a simple 3D rotating cube rendered in ASCII art. It uses basic linear algebra to transform and project 3D coordinates into a 2D screen space and renders the cube frame by frame, creating an animation effect.

## Features

- **3D to 2D Projection**: Converts 3D coordinates to 2D screen space using matrix transformations.
- **Backface Culling**: Ensures that only the visible faces of the cube are drawn.
- **Line Drawing**: Draws lines between vertices to form the edges of the cube.
- **Continuous Rotation**: Continuously rotates the cube around the Y-axis.

## Code Structure

### Data Structures

- **Matrix**: Represents a 4x4 transformation matrix.
- **Vector**: Represents a 4D vector.

```rust
#[derive(Debug, Clone, Copy)]
struct Matrix([[f32; 4]; 4]);

#[derive(Debug, Clone, Copy)]
struct Vector([f32; 4]);
```

### Constants

- **VERTICES**: Defines the 8 vertices of a cube.
- **FACES**: Defines the 6 faces of the cube, each face represented by 4 vertex indices.
- **Screen Parameters**: Defines screen dimensions, offsets, and scales for projection.

### Functions

- **matrix_times_vector**: Multiplies a matrix by a vector.
- **draw_line**: Draws a line between two points on the screen.
- **cull**: Determines if a face should be culled based on its orientation to the camera.

### Main Loop

The `main` function contains the rendering loop which:

1. Sets up the transformation matrix for rotation.
2. Transforms cube vertices to world coordinates.
3. Projects the world coordinates to screen coordinates.
4. Draws the visible faces of the cube.
5. Outputs the frame to the terminal.

## Usage

### Prerequisites

- Rust installation (https://www.rust-lang.org/tools/install)

### Running the Program

1. Clone the repository or copy the source code into a file named `main.rs`.
2. Open a terminal and navigate to the directory containing `main.rs`.
3. Run the program using the following command:

```sh
cargo run
```

### Output

The program will display a rotating cube in ASCII art within the terminal. It will continuously update the terminal to animate the rotation.

## Explanation of Key Parts

### Transformation Matrix

The transformation matrix is defined to rotate the cube around the Y-axis:

```rust
let cube_to_world = Matrix([
    [c, 0.0, s, 0.0],
    [0.0, 1.0, 0.0, 0.0],
    [-s, 0.0, c, 0.0],
    [0.0, 0.0, -2.5, 1.0]
]);
```

### Drawing Function

The `draw_line` function handles drawing lines on the 2D screen by interpolating between the start and end points:

```rust
fn draw_line(frame: &mut [[u8; SCREEN_WIDTH]; SCREEN_HEIGHT], start: [f32; 2], end: [f32; 2]) {
    // Implementation
}
```

### Backface Culling

The `cull` function prevents drawing faces that are not visible to the camera:

```rust
fn cull(p0: [f32; 2], p1: [f32; 2], p2: [f32; 2]) -> bool {
    // Implementation
}
```

## Customization

You can customize various aspects of the program, such as:

- **Rotation Speed**: Adjust the rotation speed by changing the value of `t`.
- **Screen Size**: Modify `SCREEN_WIDTH` and `SCREEN_HEIGHT` to change the terminal size.
- **Cube Size and Position**: Alter the vertices in the `VERTICES` array to change the size and position of the cube.

## License

This project is open source and available under the MIT License.

Enjoy experimenting with 3D graphics in ASCII art!