# Parallel Machine Scheduling with Dispatching Rules and Gurobi Model

This repository implements a **parallel machine scheduling problem** using two approaches:

1. **Heuristic / Dispatching Rule Simulation**: a Python-based scheduler that simulates equipment allocation under capacity and holiday constraints.  
2. **Gurobi Optimization Model**: an exact MILP formulation to find the optimal schedule.

The objective is to minimize **order tardiness** while accounting for:
- Multiple production lines and equipment types  
- Equipment–bearing mappings  
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
  - Uses Python `heapq` for priority scheduling  
  - Tracks available bearings and updates usage in real time  

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
├── scheduling.ipynb # Gurobi optimization formulation
├── Dispatching_Rule.ipynb # Heuristic scheduling algorithm
├── results/
│   └── result/{order_num}/
|       ├── scheduling_gurobi_order_{order_num}.xlsx
│       └── scheduling_algorithm_order_{order_num}.xlsx
└── README.md
```


---


## Dispatching Rule Workflow

1. **Calendar Initialization**
   - Builds working-day index excluding holidays/weekends  

2. **Data Loading**
   - Reads order quantities, values, and due dates  

3. **Equipment Setup**
   - Defines machine and bearing structure per production line  

4. **Scheduling Loop**
   - Iterates over orders in a heap queue  
   - Finds earliest feasible slot and updates usage tables  

5. **Tardiness Calculation**
   - `tard[k] = max(end_time − due_date[k], 0)`  

6. **Excel Output**
   - Creates a pandas DataFrame indexed by working day  
   - Exports formatted schedule with color highlights  

---

## How to Run 

---

## Excel Output Example