# CitiBike_OperationsOptimisation
This project is to optimise the relocation of the bikes for the bike sharing platform of Citibike and "rebalance" the operations.
We spotted the imbalance of the bike stocks around New York and set the goal to optimise the match the demand with supply, especially during peak time using **integer programming model**. 


### Data Description
The datasets I used for this analysis include:

1. demand.csv - the number of bikes rented at each dock station (during one peak hour)
2. starting_inventory.csv - the initial inventory of bikes at each dock station (before peak hour)
3. distances.csv - the distance between any two dock stations (in km unit)
4. replenishment.csv - the number of extra bikes that will be made available at each station after current users complete their trips

### Analysis Method 
#### Integer Programming Model
Integer programming is the computational and mathematical optimisation program in which some or all of the variables are restricted to be integers. The integer programming can be used when the integer variables represent quantities that can only be integers or when the variables represent decisions and so should be only take on the value 0 or 1.

To deal with the linear integer programming model, I used Gurobi package. Firstly, I decided the decision variables which has to do with the "relocation" of the bikes. Then, I considered the auxiliary variable which could be useful for the decision but not directly related to the computation itself. 

Decision variables: 1) stations, 2) relocation \
Auxiliary variable: satisfied demand (the number of bikes fulfilled for the users)
 
I set the auxiliary varaible to set the appropriate bounds and constraints for the calculations.
