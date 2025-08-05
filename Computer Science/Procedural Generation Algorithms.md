# Procedural Generation Algorithms

## Map Generation

Many algorithms can be used to generate 2d or 3d grids, most of which can be found on the [Procedural Generation Wiki](http://pcg.wikidot.com/pcg-algorithm%3amap-generation).

For a full generation overview, see [Amit's Polygon Map Generation](http://www-cs-students.stanford.edu/~amitp/game-programming/polygon-map-generation/).

If you would like to see notes and code for [markov chains](https://donjon.bin.sh/code/name/), [pattern and token tables](https://donjon.bin.sh/code/random/), [fractal faulting](https://donjon.bin.sh/code/world/), or [dungeon mapping](https://donjon.bin.sh/code/dungeon/), check out donjon's [Code Library](https://donjon.bin.sh/code/) and his list of [RPG Generators](https://donjon.bin.sh/).

In procedural generation, especially for map creation, there are several key algorithms used to generate maps that are both varied and functional. Below are some useful algorithms, grouped by their primary function:

### 1. **Perlin Noise & Simplex Noise**

- **Purpose**: Used to create natural-looking terrain, such as mountains, valleys, and oceans.
- **Description**: Perlin Noise and Simplex Noise are gradient-based noise functions that produce smooth, continuous randomness. These are ideal for generating terrain features, as they avoid the blocky, unnatural look that can come from purely random values.
- **Use Case**: Elevation maps, biomes, and smooth terrain generation.
- **Example**: Generating a heightmap for terrain, where darker values represent lower elevations (oceans) and lighter values represent higher elevations (mountains).

``` Python
import noise
import numpy as np

# Generate a 2D Perlin Noise map
width, height = 512, 512
scale = 100.0
octaves = 6
persistence = 0.5
lacunarity = 2.0

noise_map = np.zeros((width, height))
for i in range(width):
    for j in range(height):
        noise_map[i][j] = noise.pnoise2(i/scale, j/scale, octaves=octaves, persistence=persistence, lacunarity=lacunarity)
```

### 2. **Cellular Automata**

- **Purpose**: Used for creating cave systems or other organic, intricate structures.
- **Description**: Cellular automata algorithms work by initializing a grid with random values and then applying a set of rules iteratively to each cell. The algorithm evolves over multiple iterations, and the result is a pattern that can resemble natural caves, dungeon layouts, or cellular structures.
- **Use Case**: Generating cave-like structures or natural, irregular patterns in maps.
- **Example**: Creating a dungeon-like layout with rooms and corridors, where walls are represented by cells and the algorithm iterates to form the cave structure.

``` Python
import numpy as np

# Initialize random map
width, height = 50, 50
grid = np.random.choice([0, 1], size=(width, height), p=[0.45, 0.55])

def cellular_automata(grid):
    for _ in range(5):  # Number of iterations
        new_grid = grid.copy()
        for i in range(1, width-1):
            for j in range(1, height-1):
                # Count neighbors
                neighbors = np.sum(grid[i-1:i+2, j-1:j+2]) - grid[i, j]
                if neighbors > 4:
                    new_grid[i, j] = 1  # Wall
                elif neighbors < 3:
                    new_grid[i, j] = 0  # Empty space
        grid = new_grid
    return grid

final_map = cellular_automata(grid)

```

### 3. **Diamond-Square Algorithm**

- **Purpose**: Used for terrain heightmap generation.
- **Description**: This algorithm starts with a grid of four points and subdivides them into smaller squares. The algorithm then applies random values to the midpoint of each square, and iteratively applies this process to the smaller squares, creating a more detailed surface with each iteration.
- **Use Case**: Elevation maps with mountains, valleys, and varied terrain features.
- **Example**: Generating a 2D array where the values represent elevations that form mountains and valleys.

``` Python
import numpy as np

def diamond_square(size, roughness):
    # Initialize grid
    grid = np.zeros((size, size))
    step_size = size - 1
    
    # Diamond step
    def diamond(x, y, size, value):
        avg = np.mean([grid[x, y], grid[x + size, y], grid[x, y + size], grid[x + size, y + size]])
        grid[x + size//2, y + size//2] = avg + np.random.uniform(-value, value)
    
    # Square step
    def square(x, y, size, value):
        avg = np.mean([grid[x, y], grid[x + size, y], grid[x, y + size], grid[x + size, y + size]])
        grid[x + size//2, y + size//2] = avg + np.random.uniform(-value, value)
    
    return grid

terrain_map = diamond_square(33, 2.0)
```

### 4. **Voronoi Diagrams**

- **Purpose**: Used for creating organic, cell-based map layouts such as biomes, cities, or regions.
- **Description**: Voronoi diagrams partition a plane into regions based on the distance to a specific set of points. This algorithm creates naturally uneven, non-grid-based areas, ideal for representing distinct areas like different biomes or territories.
- **Use Case**: Region-based maps, creating natural "territories" such as continents, forests, or biomes.
- **Example**: Dividing a map into distinct regions where each region has a central point, like dividing a map into territories controlled by different factions.

``` Python
import numpy as np
import random

def voronoi(width, height, points):
    grid = np.zeros((width, height))
    for i in range(width):
        for j in range(height):
            min_dist = float('inf')
            for px, py in points:
                dist = np.sqrt((px - i) ** 2 + (py - j) ** 2)
                if dist < min_dist:
                    min_dist = dist
                    grid[i, j] = points.index((px, py))
    return grid

points = [(random.randint(0, 100), random.randint(0, 100)) for _ in range(5)]
voronoi_map = voronoi(200, 200, points)
```

### 5. **Delaunay Triangulation**

- **Purpose**: Used for generating maps that require connectivity, such as road systems, bridges, or cities.
- **Description**: Delaunay triangulation is a geometric algorithm that creates a set of triangles from a set of points such that no point is inside the circumcircle of any triangle. It’s often used to create a well-connected graph structure from a set of random points.
- **Use Case**: Creating connected cities, road networks, or any system requiring structured connectivity.
- **Example**: Connecting points (cities) in a way that forms a triangulated map with paths between cities.

``` Python
import numpy as np
import scipy.spatial as spatial

# Random points
points = np.random.rand(10, 2)

# Delaunay triangulation
delaunay = spatial.Delaunay(points)
```

### 6. __A_ Pathfinding_*

- **Purpose**: Used for determining the most efficient paths across a map, such as for NPC navigation or route planning.
- **Description**: A* (A-star) is a graph traversal and pathfinding algorithm that finds the shortest path between two points while considering obstacles and terrain costs. It’s often used in game maps for AI to find efficient travel routes.
- **Use Case**: Pathfinding for characters, AI movement, or network traversal in generated maps.
- **Example**: Finding the shortest path between two points in a grid, avoiding obstacles.

``` Python
from heapq import heappop, heappush

def astar(start, goal, grid):
    open_list = []
    heappush(open_list, (0, start))
    came_from = {}
    g_score = {start: 0}
    f_score = {start: heuristic(start, goal)}
    
    while open_list:
        _, current = heappop(open_list)
        
        if current == goal:
            return reconstruct_path(came_from, current)
        
        for neighbor in neighbors(current, grid):
            tentative_g_score = g_score[current] + 1
            if tentative_g_score < g_score.get(neighbor, float('inf')):
                came_from[neighbor] = current
                g_score[neighbor] = tentative_g_score
                f_score[neighbor] = g_score[neighbor] + heuristic(neighbor, goal)
                heappush(open_list, (f_score[neighbor], neighbor))
    
    return None

def heuristic(a, b):
    return abs(a[0] - b[0]) + abs(a[1] - b[1])
```

### 7. **Fractal Brownian Motion (FBM)**

- **Purpose**: Used to create natural, multi-level terrain features such as mountains and valleys.
- **Description**: FBM is a method of combining multiple layers of Perlin noise or Simplex noise at different scales (octaves) to create more complex, fractal-like terrain. Each layer contributes more detail, simulating natural, noisy patterns like those found in terrain elevation.
- **Use Case**: Creating highly detailed and realistic terrain landscapes, such as mountains, valleys, and rolling hills.
- **Example**: Layering different levels of Perlin noise to generate a more detailed and fractal-like heightmap.

``` Python
import noise
import numpy as np

def fbm_noise(width, height, octaves, persistence, lacunarity):
    noise_map = np.zeros((width, height))
    for i in range(width):
        for j in range(height):
            noise_map[i][j] = noise.pnoise2(i / 100.0, j / 100.0, octaves=octaves, persistence=persistence, lacunarity=lacunarity)
    return noise_map

fbm_map = fbm_noise(512, 512, 6, 0.5, 2.0)
```

### 8. **L-systems (Lindenmayer Systems)**

- **Purpose**: Used for generating plant-like structures or branching networks.
- **Description**: L-systems are a set of recursive rules used to model the growth of plants and other organic structures. By applying production rules iteratively, an L-system can generate complex branching patterns.
- **Use Case**: Generating trees, plants, or even more complex organic structures like cave systems and underground environments.
- **Example**: Generating tree-like structures based on a set of recursive rules.

``` Python
import matplotlib.pyplot as plt
import numpy as np

def lsystem(axiom, rules, iterations):
    result = axiom
    for _ in range(iterations):
        result = ''.join([rules.get(c, c) for c in result])
    return result

axiom = "F"
rules = {'F': "F+F-F-F+F"}
result = lsystem(axiom, rules, 4)

print(result)
```

### 9. **Random Walk**

- **Purpose**: Used for generating random, yet constrained structures such as caves or maze-like systems.
- **Description**: A random walk is an algorithm that starts at a random point and moves in random directions (up, down, left, right, etc.), leaving a trail of generated content. Constraints can be applied to prevent it from wandering too far or creating disconnected paths.
- **Use Case**: Generating cave systems, maze-like dungeons, or even underground lairs.
- **Example**: Walking in random directions to form a maze or tunnel.

``` Python
import numpy as np

def random_walk(width, height, steps):
    grid = np.zeros((width, height))
    x, y = width // 2, height // 2
    for _ in range(steps):
        grid[x, y] = 1  # Mark the path
        x, y = x + np.random.choice([-1, 1]), y + np.random.choice([-1, 1])
    return grid

walk_map = random_walk(50, 50, 1000)
```

### 10. **Marching Squares**

- **Purpose**: Used for creating smooth, organic maps from grid data.
- **Description**: Marching Squares is a technique used to create smooth boundaries or contours based on grid-based data. It works by analyzing each cell in the grid and determining how to "march" between the cells, creating a smooth curve or boundary.
- **Use Case**: Generating smooth borders, coastlines, or natural features in maps (especially for 2D maps).
- **Example**: Generating a smooth coast or boundary line based on grid data.

``` Python

```

### 11. **World-Generation by Graph Theory (Graph-based generation)**

- **Purpose**: Used for creating complex networks such as cities, roads, or territories.
- **Description**: This approach uses graph-based algorithms to generate interconnected systems of nodes (cities, regions) and edges (roads, paths). Graph generation can produce efficient, well-connected layouts.
- **Use Case**: City generation, road networks, interconnected world-building.

### 12. **Dungeon Generation Algorithms (e.g., BSP, Hunt and Kill)**

- **Purpose**: Used for generating indoor layouts like dungeons or mazes.
- **Description**: Algorithms like Binary Space Partitioning (BSP) divide a space into smaller rooms and corridors. Hunt and Kill algorithms are used for creating maze-like layouts by generating rooms and then connecting them with paths.
- **Use Case**: Generating dungeon layouts, caves, or indoor environments with rooms and paths.

### 13. **Poisson Disk Sampling**

- **Purpose**: Used for generating scattered objects (e.g., trees, rocks) with a minimum distance between them.
- **Description**: Poisson Disk Sampling is used to place points or objects in a space such that no two points are too close to each other. This algorithm ensures a natural-looking distribution of objects while avoiding overcrowding.
- **Use Case**: Placing trees, rocks, or other objects in a natural, scattered way across a terrain or environment.

### 14. **Hexagonal Grid Systems**

- **Purpose**: Used for creating hex-based maps, commonly used in strategy games.
- **Description**: Hexagonal grids provide a more efficient and organic layout compared to square grids. The algorithm generates hexagonal cells and allows for more accurate distance measurements and movement.
- **Use Case**: Creating strategic map layouts, for example, for board games, or hex-based simulations.

### Conclusion:

Each of these algorithms has its strengths and is suited for different aspects of map generation. Depending on the style of map you're aiming for, you can combine several of these techniques to create complex and dynamic procedurally generated worlds.