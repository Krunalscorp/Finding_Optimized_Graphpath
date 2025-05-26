# Optimizing the Campus Route

## 1. PEAS and Task Environment of the Agent

### PEAS (Performance measure, Environment, Actuators, Sensors)

- **Performance measure:**  
  Minimize the total walking distance and time taken by Rohan to complete all the tasks. This can be measured by calculating the total distance travelled or the total time taken.

- **Environment:**  
  The university campus, including locations such as Admission Office, Hostel Office, Hostel, Campus Canteen, Department, Library, and campus exit. It also includes the walking distances between each pair of locations.

- **Actuators:**  
  Rohan, the student, who can move between locations on the campus.

- **Sensors:**  
  Rohan's ability to perceive his surroundings, including the locations, walking distances, and his current energy level. Rohan can also use a campus map to navigate.

---

### Task Environment

- **Fully observable:**  
  The environment is fully observable, as Rohan has access to the campus map and can see the locations.

- **Deterministic:**  
  The environment is deterministic, as the walking distances between locations are fixed and known.

- **Sequential:**  
  The task is sequential as Rohan must complete all tasks, but **not necessarily in a fixed order** (e.g., registration before hostel office procedures). If the order was fixed, it would change the problem significantly.

- **Static:**  
  The environment is static, as the locations and walking distances do not change during the task.

- **Discrete:**  
  The task is discrete, as Rohan can only move between specific predefined locations.

---

## 2. Heuristic and Fitness Functions for the Algorithms

### A* Algorithm

- **Heuristic function (h):**  
  Estimates the walking distance from the current location to the campus exit. This can be calculated using Euclidean or Manhattan distance.  
  *Example:* If current location is Hostel Office, heuristic might estimate 500 meters to campus exit.

- **Cost function (g):**  
  Calculates the actual walking distance from the Admission Office to the current location.  
  *Example:* If current location is Hostel Office, cost function might calculate 200 meters from Admission Office to Hostel Office.

- **Fitness function (f):**  
  Combines cost and heuristic to guide the search:  
  \[
  f = g + h
  \]  
  *Example:* For Hostel Office, total estimated cost might be \(200 + 500 = 700\) meters.

---

### Random Restart Hill Climbing Algorithm

- **Fitness function:**  
  Calculates the total walking distance for the entire route. It is the sum of distances between consecutive locations.  
  *Example:* For the route Admission Office -> Hostel Office -> Hostel -> Campus Canteen -> Department -> Library -> Campus Exit, total distance might be 1500 meters.

- **Heuristic function:**  
  Not explicitly used in Hill Climbing, but can be used to generate or guide the initial solution.  
  *Example:* The heuristic might help generate a starting solution close to optimal.

---

> **Note:**  
> The heuristic function for A* should be **admissible** (never overestimate the true cost) and **consistent** (estimated cost is always less than or equal to the actual cost).
