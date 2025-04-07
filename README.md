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
| Feature Category | Dimensions | Description | Optional |
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
|------|:-------:|-------|
| Node Features | 8 dimensions | Represents vehicle's physical status |
| Edge Features | 5 or 9 dimensions | Represents inter-vehicle relationships |
| Number of Classes | 3 | Vehicle status classification |

---

## 4. Dataset Statistics

### Overall Statistics
| Item | Count |
|------|:-------:|
| Total Nodes | 699,184 |
| Total Edges | 2,679,788 |
| Node Feature Dimension | 8 |
| Edge Feature Dimension | 9 |

### Class Distribution
| Class | Count | Percentage |
|------|:-------:|:-------:|
| 0 (stop) | 363,196 | 51.95% |
| 1 (lane_change) | 140,514 | 20.10% |
| 2 (normal_driving) | 195,474 | 27.96% |

### Dataset Splits

#### Training Dataset
- Total graphs: 1
- Total nodes: 489,428
- Class distribution:
  - Class 0: 254,066 nodes (51.91%)
  - Class 1: 98,401 nodes (20.11%)
  - Class 2: 136,961 nodes (27.98%)

#### Validation Dataset
- Total graphs: 1
- Total nodes: 104,877
- Class distribution:
  - Class 0: 54,674 nodes (52.13%)
  - Class 1: 21,050 nodes (20.07%)
  - Class 2: 29,153 nodes (27.80%)

#### Test Dataset
- Total graphs: 1
- Total nodes: 104,879
- Class distribution:
  - Class 0: 54,456 nodes (51.92%)
  - Class 1: 21,063 nodes (20.08%)
  - Class 2: 29,360 nodes (27.99%)

