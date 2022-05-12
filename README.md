### multipleconstraintoptimization

Optimizing local deliveries considering weight, pallet, time window and loading times constraints

# Introduction

This project was co-developed by the author of this GitHub repository and a machine learning engineer whom we're going to call SK.

Here, we have a proposed logistics company that holds products on inventory in their warehouse and makes local deliveries in it's city, in this case, we used addresses in a California metro area.

The preface here is that the company organizes daily deliveries of the products in a manual way, namely, an employee decides every day how the deliveries are going to be organized the next day, purely based on experience.

With optimization being an np-problem, it's actually very humanly hard to come up with an "optimal" solution without the use of linear or non-linear programming.

What we have here is a program that works as follows:
1. It takes delivery addresses and the product going to those destinations with pallet quantity and total weight. It also takes the open and close time of those delivery addresses and in addition to that, it takes the amount of time those products would take to unload.
2. The program converts those addresses into a distance matrix through a Google Maps API to frame it as an optimization problem, the distance matrix uses "time" as the factor between addresses as opposed to "distance" to optimize for time.
3. It takes into consideration the maximum legal time a driver can be on the road. Further, it allows for slack, meaning, a driver can arrive to a destination before it opens if that's the optimal thing to do. In a sense, it plans ahead for openings later in the day.
4. Related, the program plans deliveries such that appointment times can only be set on top of the hour since this is a real life constraint. Moreover, it allows for drivers to be "late" to their appointments for a maximum of 30 minutes. This gives real life flexibility to the program since drivers cannot realistically arrive exactly on time and the optimization program would be severly limited anyway. 
5. Finally, the program optimizes to minimize for number of trucks used and time spent on the road, this ultimately results in minimized logistics costs.

The program outputs clear routes, essentially, it outlines what orders should go on what truck and it chronologically specifies how deliveries will be made, the appointment times for each delivery and it allows for the truck to come back to the origin.

This program takes every real life component into consideration to make it immediatelly and practicallyt useful for logistics applications.
