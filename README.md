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

Of course, I had to consider the new bikes coming in and out every hour which should be definitely considered for the calculation. Without the variables of replenishment, the optimisation for the relocation of bikes will be off the realistic situation (Even though I assumed that all the replenishment before the demand arrives). The net revenue has changed after considering the replenishment as we didn't need to move the extra bikes that were already meant to move to the targeted stations.

#### Big-M Method
Finally, I have also considered the types of vehicles to carry the bikes around. As we can now predict the number of bikes to carry between each station, we should not waste the money on the vehicles. 

I use the big-M method with two binary variables (small capacity vehicles, large capacity vehicles). The big-M method is a way of solving a linear programmes using the simplex algorithm. It introduces the 'greater-than' constraints to the model by applying a very large constant which wont' be part of any optimal solution. It is a useful method when there are conditions to add. 

### Results
By using integer programming model and the big-M method, we successfully sorted out how much bikes should be moved hourly and the number and types of vehicles we should use for the relocation. This type of calculation can be very complex if we don't use the decision analytics, but it became very simple analytical method with integer programming model.

