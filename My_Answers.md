# My Answers - Assignment 1 (CFLP: VNS vs Gurobi)

**Student Information:**
- **Student ID:** ___________447540254 __________
- **Student Name:** ______________Fahad Alfaori _____________
- **Gurobi Version Used:** [ ] Academic [✔] Free
- **Date Completed:** ___________November 7, 2026 ________________

---

## Section A: Solution Quality Analysis (4 marks)

### A.1 (2 marks) - Gap Analysis by Categories

**Analysis of Plot 01:**

[Your answer here - analyze gap patterns by size and difficulty]

**Specific Observations:**
- Highest median gap size: ____13.39%_______
- Median gap value: _______13.13____%
- Effect of difficulty on gap: ____12.37_______

**Outliers identified:**

[Explain outliers and their possible causes]

**Interpretation:**

[Explain WHY these patterns occur]

---

### A.2 (2 marks) - Overall Solution Quality Statistics

**From Excel File (Sheet "All Results"):**

- Total instances analyzed: _____144______
- Instances with gap < 5%: _______2____ ( __1.39___% )
- Instances with gap < 10%: _______31____ ( __21.53___% )
- Mean gap across all instances: ________13.72___%
- Standard deviation of gap: _____5.09______%

**Interpretation:**

[Analyze what these statistics tell you about VNS consistency and quality]

[Is VNS providing good solutions consistently? Explain]

---

## Section B: Computational Efficiency Analysis (4 marks)

### B.1 (2 marks) - Time Comparison

**Analysis of Plot 02:**

**Size at which VNS becomes significantly faster:**

[Your answer with specific size category and time values]

**Most challenging configurations:**
- For VNS: _____Large-Moderate______ (size-difficulty) with time: __4.48___ seconds
- For Gurobi: ____Small-Expensive_______ (size-difficulty) with time: __300.93___ seconds

**Detailed Comparison:**

[Explain the time differences and their implications]

---

### B.2 (2 marks) - Speedup Analysis

**Analysis of Plot 03:**

**Average speedup factors:**
- Small instances: ___9.13___x faster
- Medium instances: ___10.62___x faster
- Large instances: ___5.97___x faster

**Instances where Gurobi is faster (speedup < 1):**

[List if any exist, describe their characteristics]

**Practical Implications:**

[Discuss what these speedup factors mean for real applications]

---

## Section C: Scalability Analysis (3 marks)

### C.1 (1.5 marks) - Scalability Behavior

**Analysis of Plot 04:**

**VNS Scalability:**

[Describe how VNS time grows with problem size]

**Gurobi Scalability:**

[Describe how Gurobi time grows with problem size]

**Comparison:**

[Which scales better and why?]

---

### C.2 (1.5 marks) - Growth Rate and Predictions

**Observed Growth of Average Runtime (from your results):**

| | Small | Medium | Large | Small -> Medium (x) | Medium -> Large (x) |
|---|---|---|---|---|---|
| VNS avg time (s) | 0.65| 0.84| 1.06|1.29x | 1.26x|
| Gurobi avg time (s) | 8.45| 13.98| 5.83| 1.65x| 0.42x|

**Shape of growth in Plot 04:**
- VNS: [ ] Roughly steady [✔ ] Steadily increasing [ ] Sharply increasing
- Gurobi: [ ] Roughly steady [ ] Steadily increasing [✔ ] Sharply increasing

**Justification:**

[Explain your choice using the growth ratios above]

**Rough Prediction for Extra Large Instance (n=50, m=20):**
- Predicted VNS time: ___1.34_____ seconds
- Predicted Gurobi time: ____7.25____ seconds
- How I computed it (e.g., applying the Medium -> Large ratio again): _____Large * Medium->Large______

**Suitability for Very Large Instances:**

[Would you recommend VNS for very large problems? Why?]

---

## Section D: Quality-Time Tradeoff Analysis (3 marks)

### D.1 (1.5 marks) - Sweet Spot Identification

**Analysis of Plot 05:**

**Sweet Spot:**

[Describe the optimal balance point between quality and time]

**Time Savings for High-Quality Solutions (gap < 5%):**
- Average VNS time: ____0.72____ seconds
- Average Gurobi time: ____0.32____ seconds
- Absolute savings: ______0.40__ seconds
- Relative savings: ______-123.24__%

**Interpretation:**

[What does this mean for practitioners?]

---

### D.2 (1.5 marks) - Practical Decision Making

**Scenarios Justifying 10-15% Gap:**

1. [Scenario 1 with justification]

2. [Scenario 2 with justification]

3. [Scenario 3 with justification]

**Recommendation for Real-World Logistics Company:**

[VNS or Gurobi? Explain your recommendation considering various factors]

---

## Section E: Algorithm Understanding (3 marks)

### E.1 (1.5 marks) - VNS Neighborhood Structures

**Role of Each Neighborhood:**

**N1 (Open Facility):**
- Purpose: ___________
- Contribution: [ ] Intensification [ ✔] Diversification
- Explanation: ___________

**N2 (Close Facility):**
- Purpose: ___________
- Contribution: [ ✔] Intensification [ ] Diversification
- Explanation: ___________

**N3 (Swap Facilities):**
- Purpose: ___________
- Contribution: [ ] Intensification [ ✔] Diversification
- Explanation: ___________

**N4 (Reassign Clients):**
- Purpose: ___________
- Contribution: [ ✔] Intensification [ ] Diversification
- Explanation: ___________

**How They Complement Each Other:**

[Explain the synergy between neighborhoods]

---

### E.2 (1.5 marks) - Convergence Behavior Analysis

**Selected Convergence Plots:**

**Plot 1:** [Instance 081: _____Small expensive ______]
- Pattern: [ ✔] Smooth [ ] Multiple jumps
- Description: ____The convergence curve remains relatively flat, indicating that VNS does not identify a better solution after its initial local search _______
- What it reveals: ______The initial greedy solution and local search may already represent a local optimum within the explored neighborhoods. However, the remaining gap indicates that the solution is not necessarily globally optimal _____

**Plot 2:** [Instance 084: _____Medium, expensive ______]
- Pattern: [ ] Smooth [ ✔] Multiple jumps
- Description: _____The convergence curve shows an improvement in the objective value during the search, demonstrating that VNS can discover a better solution after its initial solution ______
- What it reveals: _____The neighborhood search and shaking mechanism can help the algorithm move away from its initial solution and identify improved configurations ______

**Plot 3:** [Instance 093: Medium, Expensive_______]
- Pattern: [ ] Smooth [ ✔] Multiple jumps
- Description: ___________
- What it reveals: ___________

**Role of Shaking Mechanism:**

[Explain how shaking helps VNS escape local optima with evidence from plots]

---
Shaking mechanism helps VNS escape local optima by randomly selecting one of the four neighborhood structures and generating a different feasible solution.

## Section F: Critical Reflection (3 marks)

### F.1 (1 mark) - Limitations and Improvements

**Main Limitations of Current VNS Implementation:**

1. [Limitation 1]
Dependence on the greedy initial solution: VNS starts with a greedy solution. If this solution is far from the global optimum, the algorithm may struggle to find significantly better solutions.

2. [Limitation 2]
Limited neighborhood exploration: The algorithm uses a maximum number of neighbors and randomly selects a neighborhood during shaking. This can prevent it from exploring potentially better solutions.

3. [Limitation 3]
Limited diversification: The current implementation can repeatedly explore similar solutions. In particular, N2 and N3 perform essentially the same one-for-one facility swap, reducing the diversity of the neighborhood structures.

**Suggested Improvements:**

1. [Improvement 1 with explanation of expected benefit]
Multiple initial solutions: Generate several initial solutions using different random seeds and select the best one. This could reduce dependence on a single greedy solution.

2. [Improvement 2 with explanation of expected benefit]
Improve neighborhood structures: Correct the N2 implementation and introduce more effective facility-closing and client-reassignment operations. This would increase the diversity of the search.

3. [Improvement 3 with explanation of expected benefit]
Adaptive shaking and search parameters: Adjust the number of neighbors and shaking intensity depending on the search progress. Stronger shaking could be applied when the algorithm repeatedly fails to improve its best solution.

---

### F.2 (1 mark) - Real-World Deployment Considerations

**Additional Constraints for Real Logistics Company:**

1. [Constraint 1 and why it matters]
Transportation time and delivery windows: A company must consider delivery deadlines, traffic conditions, and customer availability. Minimizing transportation costs alone may produce solutions that are not operationally feasible.
2. [Constraint 2 and why it matters]
Demand uncertainty: Customer demand can change because of seasonal fluctuations, market conditions, and unexpected events. The optimization model should accommodate changing demand and uncertain forecasts.

3. [Constraint 3 and why it matters]
Facility availability and operational capacity: Facilities may experience equipment failures, staffing shortages, maintenance requirements, or temporary closures. These factors must be considered when determining facility locations and customer assignments.

**Additional Objectives:**

[Discuss multi-objective considerations beyond cost minimization]

---
Minimizing carbon emissions and environmental impact, reducing delivery times and improving customer satisfaction and maximizing facility utilization. 

### F.3 (1 mark) - Exact Method vs Heuristic in Practice

**Gurobi Optimality Status (from the `gurobi_status` column):**
- Instances solved to proven optimality: ___144___ out of ___144___
- Instances stopped at the time limit: ____0__ out of ___144___
- Do the time-limit instances share a size/difficulty? ___N/A________

**What VNS Gives Up and What It Gains:**

[Use your numbers: average gap vs. average time saved]
VNS gives up some solution accuracy in exchange for lower computational time. The average optimality gap is 13.72%, meaning VNS solutions are approximately 13.72% more expensive than the Gurobi solutions on average.

**Practical Value of Heuristics:**

[Discuss the industrial importance of VNS-like algorithms, based on what you observed]

---
The results demonstrate the industrial importance of heuristic algorithms. Although VNS does not consistently find optimal solutions, it can produce feasible solutions much faster than Gurobi on many instances. In real logistics operations, decisions often need to be made within limited time. Waiting for an exact optimization algorithm may not always be practical, particularly when dealing with complex or frequently changing problems. 

## Section G: BONUS - VNS Improvement Challenge (+3 marks, optional)

*Leave this section empty if you do not attempt the bonus. See Section 8 of the guide. Your improved notebook (`StudentID_FirstName_LastName_Assignment1_IMPROVED.ipynb`) must be pushed to your repository.*

### G.1 (1 mark) - Bug Identification

**Where is the bug?** (cell / function / line numbers in `Assignment_1.ipynb`):

[Paste the faulty line(s) of code]
neighbor_facility_opened = facility_opened.copy()
neighbor_facility_opened[j_open] = 0
neighbor_facility_opened[j_close] = 1

**What does the bug do?**
The function is intended to generate neighbors by closing existing facilities. However, it performs a one-for-one facility swap instead. This makes N2 substantially overlap with N3, which already performs facility swaps.
[Describe the specific issue]

**Why does it degrade VNS performance?**

[Explain the effect on the search and link it to the high gaps (>20%) in your results]

---
The duplication reduces the diversity of the neighborhood structures. Instead of exploring a distinct facility-closing operation, the algorithm repeatedly explores facility swaps. This limits its ability to identify solutions that reduce the number of operating facilities and associated fixed costs. Consequently, the algorithm may remain trapped in local optima and produce larger optimality gaps.

### G.2 (1 mark) - The Fix

**Corrected code:**

```python
# paste your fixed line(s) here
def n2_close_open_facility(max_neighbors, facility_opened,
                           service_costs, facility_capacities,
                           client_demands):

    neighbors = []

    opened_indices = np.where(facility_opened == 1)[0]
    np.random.shuffle(opened_indices)

    for j_open in opened_indices:

        if len(neighbors) >= max_neighbors:
            break

        # Close one existing facility without opening another
        neighbor_facility_opened = facility_opened.copy()
        neighbor_facility_opened[j_open] = 0

        # Reassign clients to the remaining open facilities
        neighbor_client_assignments = assign_clients_to_nearest_open_facility(
            service_costs,
            neighbor_facility_opened,
            facility_capacities,
            client_demands
        )

        # Retain only feasible solutions
        if is_feasible(
            neighbor_facility_opened,
            neighbor_client_assignments,
            facility_capacities,
            client_demands
        ):
            neighbors.append((
                neighbor_facility_opened,
                neighbor_client_assignments
            ))

    return neighbors
    
```

**Why does the fix work and why does it not break the rest of the algorithm?**

[Explanation]
The corrected function performs a genuine facility-closing operation without opening another facility. It retains the original function name, parameters, return structure, and feasibility checks. Therefore, it remains compatible with the existing shaking and local-search functions. The correction also makes N2 distinct from N3, allowing VNS to explore a wider range of facility configurations.
---

### G.3 (1 mark) - Demonstrated Improvement

**Before vs After (same instances):**

| Metric | Original VNS | Improved VNS |
|---|---|---|
| Mean gap (%) | | |
| Std of gap (%) | | |
| Instances with gap < 5% | | |
| Instances with gap > 20% | | |
| Mean VNS time (s) | | |

**Analysis:**

[Discuss the improvement, and any change in running time]

**Improved results files (names in your repository):** ___________

---

## Additional Comments (Optional)

[Any additional observations, challenges faced, or insights gained]

---

## Declaration

I hereby declare that:
- I have completed this assignment independently
- All numerical results are from MY experiments using MY student ID
- All analysis and interpretations are MY own work
- I have not copied results or answers from other students
- I understand the consequences of academic dishonesty

**Signature:** ___________447540254____________

**Date:** _____________November 7, 2026______________

---

**END OF MY ANSWERS**
