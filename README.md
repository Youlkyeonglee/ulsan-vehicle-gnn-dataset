# Vehicle Graph Data Structure Analysis

## 1. Node Data

### Node Feature Composition (8 dimensions)
| Feature Category | Dimensions | Description |
|------------------|------------|-------------|
| Bounding Box | 4 | center_x, center_y, width, height |
| Speed | 1 | Object's velocity information |
| Direction | 2 | dx, dy (direction vector) |
| Acceleration | 1 | Object's acceleration information |

### Node Identification
- Unique identifier: (object_id, frame) pair
- Same object in different frames is treated as separate nodes

### Node Labels (Classes)
| Class Name | Label Value |
|------------|-------------|
| stop | 0 |
| lane_change | 1 |
| normal_driving | 2 |

---

## 2. Edge Data

### Edge Feature Composition (5 or 9 dimensions)
| Feature Category | Dimensions | Description | optional |
|------------------|:------------:|-------------|:---:  |
| Distance | 1 | Distance between two objects |  |
| Speed | 1 | Neighboring object's velocity |  |
| Direction | 2 | Neighboring object's dx, dy direction vectors |  |
| Acceleration | 1 | Neighboring object's acceleration |  |
| Neighbor Bounding Box | 4 | Neighboring object's center_x, center_y, width, height | 5 or 9 dims |

### Edge Creation Rules
- Each object is connected to a maximum of 4 neighboring objects
- Edges are created only within the same frame (using the neighbors_ids field)
- Directed graph (source node → target node)

---

## 3. Data Summary
| Item | Value | Notes |
|------|-------|-------|
| Node Features | 8 dimensions | Represents vehicle's physical status |
| Edge Features | 5 or 9 dimensions | Represents inter-vehicle relationships |
| Number of Classes | 3 | Vehicle status classification |

