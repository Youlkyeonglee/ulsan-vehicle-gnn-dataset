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
| Edge Feature Dimension | 5 or 9 |

### 데이터셋 분포

| Category | Train | Validation | Test | Total |
|------|:-------:|:-------:|:-------:|:-------:|
| Total Nodes | 489,428 | 104,877 | 104,879 | 699,184 |
| Stop (Class 0) | 254,066 (51.91%) | 54,674 (52.13%) | 54,456 (51.92%) | 363,196 (51.95%) |
| Lane Change (Class 1) | 98,401 (20.11%) | 21,050 (20.07%) | 21,063 (20.08%) | 140,514 (20.10%) |
| Normal Driving (Class 2) | 136,961 (27.98%) | 29,153 (27.80%) | 29,360 (27.99%) | 195,474 (27.96%) |
