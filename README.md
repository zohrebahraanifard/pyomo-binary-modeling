# Binary Grid Optimization with Pyomo ♟️

This repository contains a discrete optimization model built using **Pyomo**, solved via **GAMS/CPLEX**.  
The model places binary decision variables on an **8×8 grid** with constraints that restrict adjacency using rules similar to *knight moves* on a chessboard.

---

## 📂 Contents
- **Modeling-HW.ipynb** – Main notebook implementing:
  - Pyomo modeling framework
  - Binary decision variables on a 2D grid
  - Max-imization objective
  - Multiple sets of constraints (Parts A, B, C)
  - Solver runs via GAMS/CPLEX
  - Printing chosen grid positions

---

## 🔍 Problem Overview

We define:

- **Index sets**
  - `I = {1…8}`
  - `J = {1…8}`
- **Decision variable**  
  `delta[i,j] ∈ {0,1}` for all grid positions `(i,j)`

- **Objective**  
  Maximize the number of selected grid cells:

  \[
  \max \sum_{i \in I} \sum_{j \in J} \delta_{i,j}
  \]

- **Constraints**
  - **Part A:** Row restrictions  
    \[
    \sum_{j} \delta_{i,j} \le 1
    \]
  - **Part B:** Column restrictions  
    \[
    \sum_{i} \delta_{i,j} \le 1
    \]
  - **Part C:** “Knight-move” conflict constraints  
    For example:  
    \[
    \delta_{i,j} + \delta_{i+2, j+1} \le 1
    \]
    and similar variations.

Each part can be activated/deactivated cleanly within the notebook.

---

## 🧠 Purpose of the Model
- Demonstrate **binary programming**
- Build intuition for **grid-based combinatorial problems**
- Practice constructing **conditional constraints** using `Constraint.Skip`
- Apply solver options with **GAMS/CPLEX**
- Analyze optimal placements and constraint interaction

---

## 🛠 Technologies Used
- Python 3  
- Pyomo  
- GAMS & CPLEX (via Pyomo solver interface)  
- Jupyter Notebook  

---

## ▶️ Running the Model

Install Python packages:

```bash
pip install pyomo
