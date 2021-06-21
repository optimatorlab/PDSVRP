# The parallel drone scheduling vehicle routing problem (PDSVRP)
This repository provides a collection of test problems, as well as their solutions, for the PDSVRP. The PDSVRP is a variant of the VRP in which multiple UAVs operate in parallel with a number of trucks to deliver parcels in the minimum time.
The repository accompanies the following paper, which is currently under review:
> R. Raj, D. Lee, S. Lee, J. Walteros, C. Murray. A branch-and-price approach for the parallel drone scheduling vehicle routing problem. Available at SSRN: _____
The paper provides details on the PDSVRP definition, and a branch-and-price algorithm as a solution approach.
---- 
## PDSVRP Repository Contents
This repository contains **test problems** with their **solutions** inside the [`Problems`](Problems) folder, which are described in detail below.  

1. The directory [`10_customer_problems`](Problems/10_customer_problems) contains 20 sub-directories (one for each 10-customer problem). Each sub-directory contains the following files:
   - `nodes.csv` describes all nodes in the problem. The first column represents the node number, the next two columns are x- and y-coordinates of the node, and the last column indicates whether the customer-node is a truck-only customer.  The lowest and highest node numbers correspond to the depot and the remaining node numbers correspond to customers.
   - `tau.csv` provides the matrix of truck travel-time between each nodes.
   - `tauprime.csv` provides the matrix of UAV travel-time between each nodes.
   - `Cprime.csv` provides the list of all customers that are eligible to be served by a UAV.

2. The directory [`20_customer_problems`](Problems/20_customer_problems) contains 20 sub-directories (one for each 20-customer problem). The description of this directory is the same as that of the [`10_customer_problems`](Problems/10_customer_problems) directory.

3. The directory [`Large_scale_problems`](Problems/Large_scale_problems) contains 6 files, each of which corresponds to a large-scale problem instance. The first number in each instance file name represents the number of customers. Each instance file contains 4 columns. The first column represents the node number, the next two columns are x- and y-coordinates of the node, and the last column indicates whether the customer-node is a truck-only customer. The lowest and highest node numbers correspond to the depot and the remaining node numbers correspond to customers. For these instances, truck travel times are calculated by assuming Manhattan paths for trucks and Euclidean distances for UAVs, and assuming the UAV speed to be twice as much as the truck speed.

4. [`performance_summary_PDSVRP.csv`](Problems/performance_summary_PDSVRP.csv) provides information about solutions generated for each test problem in the [PDSVRP paper](______). This file contains the following columns:
- `problemName` - The name of the problem instance.  This is either a subdirectory name within the [`10_customer_problems`](Problems/10_customer_problems) and [`20_customer_problems`](Problems/20_customer_problems) directories or a filename within the [`Large_scale_problems`](Problems/Large_scale_problems) directory.
- `problemType` - Indicates whether the problem instance is small- or large-scale.
- `numCustomers` - The total number of customers.
- `UAVspeed` - UAV speed as a multiple of the truck speed. Only applicable for large-scale problems where the UAV travel-time matrix is not explicitly provided.
- `UAVendurance` - UAV endurance in terms of number of minutes.
- `numTrucks` - # of trucks available (`1`, `2`, or `3`).
- `numUAVs` - # of UAVs available (`2`, `4`, or `6`).
- `solverType` - Indicates whether the problem was solved using the arc-based formulation (`DFJ`) or the branch-and-price algorithm (`BNP`).
- `heuristicSwitch` - Indicates whether the exact (`0`) or heuristic (`1`) version of the branch-and-price algorithm was called. Not applicable for the arc-based formulation.
- `timeLimit` - Total time allowed to solve the problem.
- `initialHeuristicSoln` - Objective value obtained from running the initial heuristic in the branch-and-price algorithm.
- `isOptimal` - Indicates whether the final solution is optimal (`1`) or not (`0`).
- `objVal` - The objective function value, as obtained by the given solution approach.
- `numTruckCust` - The number of customers assigned to the truck(s).
- `numUAVcust` - The number of customers assigned to the UAV(s).
- `runTime` - The total runtime of the given solution approach.

5. Finally, the directory [`solutions`](Problems/solutions) contains a total of 1,225 files of the form  `<problemName>_<solverType>_<numCustomers>_<numTrucks>_<numUAVs>.csv` where each file corresponds to a detailed description of the solution whose summary is provided in [`performance_summary_PDSVRP.csv`](Problems/performance_summary_PDSVRP.csv).

----
## Contact Info
For any queries, please send an email to r28@buffalo.edu.