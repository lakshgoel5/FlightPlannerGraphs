# Flight Planner Graphs

A flight route planning system that implements graph algorithms to determine optimal flight routes between cities based on different criteria.

## Overview

This project implements a flight planning system that helps users find the best route between cities based on different optimization criteria:

1. **Least Flights, Earliest Arrival**: Finds a route with the minimum number of flights, and among those, the one that arrives the earliest.
2. **Cheapest Route**: Finds the route with the lowest total fare.
3. **Least Flights, Cheapest Route**: Finds a route with the minimum number of flights, and among those, the one that costs the least.

## Data Structures Used

The project utilizes the following data structures:

- **Graph**: Cities are represented as nodes, and flights are represented as directed edges between cities.
- **Queue**: For breadth-first search to find routes with least number of flights.
- **Custom Heap**: For priority-based path finding (Dijkstra's algorithm) to find cheapest routes.
- **Adjacency List**: To efficiently store flight connections between cities.

## Files in the Project

- `flight.py`: Defines the `Flight` class which contains information about each flight (ID, start city, end city, departure time, arrival time, fare).
- `planner.py`: Contains the `Planner` class with implementations of various route-finding algorithms, as well as helper data structures like `Queue` and `Heap`.
- `main.py`: Contains a sample test case to validate the algorithms.

## Algorithms

1. **Breadth-First Search (BFS)**: Used for finding routes with least number of flights.
2. **Dijkstra's Algorithm**: Modified to find the cheapest route.
3. **Custom Priority-Based Path Finding**: For finding routes with the minimum number of flights that are also cheapest.

## How to Run

1. Ensure you have Python installed on your system.
2. Clone the repository:
   ```
   git clone <repository-url>
   cd FlightPlannerGraphs
   ```
3. Run the main script to see the sample test case:
   ```
   python main.py
   ```

## Creating Custom Test Cases

To create your own test cases, modify the `main.py` file:

1. Create `Flight` objects specifying:
   - `flight_no`: Unique identifier for the flight
   - `start_city`: City where the flight departs (integer ID)
   - `departure_time`: Time of departure
   - `end_city`: City where the flight arrives (integer ID)
   - `arrival_time`: Time of arrival
   - `fare`: Cost of the flight

2. Create a `Planner` object with your flights list
3. Call the appropriate method based on your needs:
   - `least_flights_earliest_route(start_city, end_city, t1, t2)`
   - `cheapest_route(start_city, end_city, t1, t2)`
   - `least_flights_cheapest_route(start_city, end_city, t1, t2)`

Where:
- `start_city`: The ID of the departing city
- `end_city`: The ID of the destination city
- `t1`: The earliest departure time
- `t2`: The latest arrival time

## Example

```python
from flight import Flight
from planner import Planner

# Create flight objects
flights = [
    Flight(0, 0, 0, 1, 30, 50),      # City 0 to 1
    Flight(1, 0, 0, 3, 80, 200),     # City 0 to 3
    # ... more flights
]

# Create planner
flight_planner = Planner(flights)

# Find route with least flights and earliest arrival
route1 = flight_planner.least_flights_earliest_route(0, 4, 0, 300)

# Find cheapest route
route2 = flight_planner.cheapest_route(0, 4, 0, 300)

# Find route with least flights that is also cheapest
route3 = flight_planner.least_flights_cheapest_route(0, 4, 0, 300)

# Print results
print("Route 1:", [f.flight_no for f in route1])
print("Route 2:", [f.flight_no for f in route2])
print("Route 3:", [f.flight_no for f in route3])
```

## Time Complexity Analysis

- **Least Flights, Earliest Route**: O(F + C), where F is the number of flights and C is the number of cities
- **Cheapest Route**: O(F log F), where F is the number of flights
- **Least Flights, Cheapest Route**: O(F log F), where F is the number of flights

## Extensions and Future Work

- Add a graphical user interface to visualize flight routes
- Implement more complex constraints like maximum layover time
- Add support for real-time flight data integration
- Optimize algorithms for very large datasets