# Parallel Machine Scheduling with Dispatching Rules and Gurobi Model

This repository implements a **parallel machine scheduling problem** using two approaches:

1. **Heuristic / Dispatching Rule Simulation**: a Python-based scheduler that simulates equipment allocation under capacity and holiday constraints.  
2. **Gurobi Optimization Model**: an exact MILP formulation to find the optimal schedule.

The objective is to minimize **order tardiness** while accounting for:
- Multiple production lines and equipment types  
- Weekends and Taiwan national holidays  
- Two-stage order processing (Stage 1 = fixed time, Stage 2 = quantity-dependent)  
- Parallel production with limited machine capacity  

---

## Features

- **Calendar & Holidays**
  - Automatically detects weekends and Taiwan public holidays  
  - Maps valid working days and skips non-working days  

- **Equipment Allocation**
  - Each equipment (`E`) contains multiple bearings (`P`)  
  - Ensures no overlap in time or capacity  

- **Order Production Time (Two-Stage Process)**
  - **Stage 1:** Fixed-time processing  
  - **Stage 2:** Quantity-dependent processing  

- **Heuristic Scheduling**
  - Employs a priority queue (heapq) to determine dispatch order
  - Follows the Largest Processing Time (LPT) rule, giving precedence to orders with higher quantities

- **Excel Visualization**
  - Exports results to Excel (`xlsxwriter`)  
  - Each cell shows assigned *Order / Side / Stage*  
  - Color-coded by order for easy visualization  

---

## Project Structure
```
main/
├── data/
│   └── order/
│       └── {order_num}/
│           ├── quantity.txt
│           ├── value.txt
|           ├── order_num.txt
│           └── due_date.txt
├── Scheduling.ipynb # Gurobi optimization formulation
├── Dispatching_Rule.ipynb # Heuristic scheduling algorithm
├── results/
│   └── result/{order_num}/
|       ├── scheduling_gurobi_order_{order_num}.xlsx
│       └── scheduling_algorithm_order_{order_num}.xlsx
└── README.md
```


---


## Dispatching Rule Flowchart

![Dispatching Rule Flowchart](images/dispatching_rule_flowchart.png)

---

## Gurobi Optimization Model 

- Objective function

- Constraints

- Variables

The details please refer ... 

---

## How to Run 

---

## Excel Output Example

![Excel Output](images/scheduling_results.png)