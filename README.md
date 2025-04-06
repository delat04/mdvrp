# README: MDVRP Simulation with Genetic Algorithm (GA)

This documentation explains the process and components of the Vue.js project simulating the **Multi-Depot Vehicle Routing Problem (MDVRP)** using a **Genetic Algorithm (GA)**. The algorithm is designed to demonstrate the step-by-step execution of GA in solving MDVRP.

---

## **Overview**

The Multi-Depot Vehicle Routing Problem (MDVRP) involves assigning customers to multiple depots while respecting constraints like vehicle capacity and minimizing travel distance. A Genetic Algorithm (GA) is used to find solutions iteratively by applying selection, crossover, and mutation operations.

This project simulates GA with visualizations to:
- Randomly assign customers to depots.
- Evaluate and optimize routes.
- Apply genetic operators like crossover and mutation.
- Show an interactive execution of the GA process.

---

## **Algorithm Steps**

### **Step 1: Initialization**
1. **Random Assignment:**
   Customers are randomly assigned to depots while respecting their capacity constraints.
2. **Route Creation:**
   Initial routes are created between depots and customers.
3. **Fitness Calculation:**
   The fitness score is calculated based on total route distances and load balance among depots.

### **Step 2: Selection**
1. **Evaluating Routes:**
   Routes are evaluated based on their distances and load distribution.
2. **Highlighting Best Routes:**
   The most efficient routes are visually highlighted.

### **Step 3: Crossover**
1. **Parent Selection:**
   Routes between depots are selected as parents for crossover.
2. **Exchanging Customers:**
   Customer assignments between depots are swapped to create new solutions.
3. **Validation:**
   The new routes are validated against capacity constraints.

### **Step 4: Mutation**
1. **Random Selection:**
   Routes are randomly selected for mutation.
2. **Small Modifications:**
   Customers are reassigned between depots to introduce variation.
3. **Recalculation:**
   Fitness scores are updated after mutation.

---

## **Code Components**

### **1. Initialization (`initializeRoutes`)**
Randomly assigns customers to depots based on proximity and capacity.
- Filters depots with available capacity.
- Assigns customers to the closest eligible depot.
- Visualizes the assignment with animated links.

### **2. Selection (`selectFittestRoutes`)**
Highlights the most efficient routes based on distance and load distribution.
- Evaluates routes and highlights those with distances below a threshold.

### **3. Crossover (`performCrossover`)**
Combines customer assignments between depots to create new solutions.
- Selects parent depots and swaps a subset of customers.
- Updates the visualization to reflect the crossover process.

### **4. Mutation (`performMutation`)**
Introduces random variations to the routes.
- Reassigns customers between depots with available capacity.
- Ensures variations remain valid by checking constraints.

### **5. Fitness Calculation (`calculateFitnessScore`)**
Calculates a fitness score based on:
- **Total Distance:**
  Sum of distances for all routes.
- **Load Balance:**
  How evenly the load is distributed among depots (targeting 80% utilization).

---

## **Visualization Features**

1. **Animated Links:**
   Routes are animated to visualize changes during each step.
2. **Interactive SVG:**
   Mouse movements are tracked to show coordinates dynamically.
3. **Color-Coded Routes:**
   Routes are color-coded based on their status:
    - Default: `#94a3b8`
    - Best Routes: `#f97316`
    - After Crossover: `#a855f7`
    - After Mutation: `#eab308`

---

## **Execution Flow**

### Initialization
```javascript
await initializeRoutes();
```
- Randomly assigns customers to depots.
- Calculates initial fitness.

### Selection
```javascript
await selectFittestRoutes();
```
- Highlights the most efficient routes.

### Crossover
```javascript
await performCrossover();
```
- Swaps customers between depots to create new solutions.
- Updates fitness scores.

### Mutation
```javascript
await performMutation();
```
- Randomly modifies routes to maintain diversity.

---

## **How to Use**

1. **Run the Project:**
   Install dependencies and start the Vue.js app:
   ```bash
   npm install
   npm run serve
   ```
2. **View Visualization:**
   Open the app in a browser and follow the step-by-step execution of the algorithm.
3. **Adjust Parameters:**
   Modify parameters like mutation rate, animation speed, and depot capacities in the code to experiment with different scenarios.

---

## **Key Parameters**

| Parameter         | Description                                  |
|-------------------|----------------------------------------------|
| `mutationRate`    | Probability of mutation in each generation   |
| `animationSpeed`  | Speed of visual animations                  |
| `generation`      | Current generation of the GA                |
| `fitnessScore`    | Fitness score of the current solution       |

---

## **Notes**
- The algorithm is non-deterministic, so results may vary across runs.
- Use a fixed random seed for debugging or consistent results.
- This simulation is for educational purposes and does not solve MDVRP optimally.

---

## **Future Improvements**
- Add support for more depots and customers.
- Implement additional selection methods (e.g., tournament selection).
- Improve mutation logic to handle edge cases.
- Include a real-time performance graph.

---

## **References**
- Genetic Algorithms: https://en.wikipedia.org/wiki/Genetic_algorithm
- MDVRP Overview: https://en.wikipedia.org/wiki/Vehicle_routing_problem
