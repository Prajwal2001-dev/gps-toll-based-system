# GPS Toll Base System

## Overview
The GPS Toll Base System is a project that simulates the toll calculation for vehicles based on their GPS coordinates. The system includes vehicles and toll stations, and it calculates the toll charges for each vehicle as they pass through different toll stations. The toll charges are calculated based on the distance traveled by the vehicle and the toll rate of the respective toll stations.

## Features
- **Vehicles**: Each vehicle has a unique ID, vehicle type, GPS coordinates, and a toll balance.
- **Toll Stations**: Each toll station has a unique ID, location (GPS coordinates), and a toll rate.
- **GPS Simulator**: Randomly generates GPS coordinates for each vehicle to simulate movement.
- **Toll Calculator**: Calculates the toll charges based on the distance between the vehicle's current GPS coordinates and the toll station's location using the Haversine formula.

## Implementation

### Classes

1. **Vehicle Class**
    - `id`: Unique identifier for the vehicle.
    - `vehicle_type`: Type of the vehicle (e.g., car, truck).
    - `gps_coordinates`: Current GPS coordinates of the vehicle, initialized at origin (0, 0).
    - `toll_balance`: Total toll balance for the vehicle, initialized at 0.

2. **TollStation Class**
    - `id`: Unique identifier for the toll station.
    - `location`: GPS coordinates of the toll station.
    - `toll_rate`: Rate at which the toll is charged per unit distance.

### Functions

1. **gps_simulator(vehicle)**
    - Generates random GPS coordinates for the vehicle.

2. **toll_calculator(vehicle, toll_stations)**
    - Calculates the toll charges for the vehicle as it passes through each toll station.
    - Uses the Haversine formula to calculate the distance between the vehicle's current GPS coordinates and the toll station's location.
    - Updates the vehicle's toll balance.

3. **haversine_distance(coord1, coord2)**
    - Calculates the great-circle distance between two points on the Earth's surface given their latitude and longitude in decimal degrees.

## Simulation
- The simulation runs for a specified number of time steps (e.g., 10).
- For each time step, the GPS coordinates of each vehicle are updated using the `gps_simulator` function.
- The toll charges are calculated for each vehicle using the `toll_calculator` function.
- The final toll balances for each vehicle are printed at the end of the simulation.

## Example
```python
# Initialize system
vehicles = [Vehicle(1, "car"), Vehicle(2, "truck")]
toll_stations = [TollStation(1, (37.7749, -122.4194), 5.0), TollStation(2, (37.8024, -122.4056), 3.0)]

# Run simulation
for i in range(10):  # Simulate 10 time steps
    for vehicle in vehicles:
        gps_simulator(vehicle)
        toll_calculator(vehicle, toll_stations)

# Print final toll balances
for vehicle in vehicles:
    print(f"Vehicle {vehicle.id} final toll balance: {vehicle.toll_balance:.2f}")

## Conclusion
The GPS Toll Base System efficiently simulates the toll calculation process for vehicles using GPS coordinates. The system can be expanded to include more vehicles, toll stations, and additional features such as different toll rates for different vehicle types, toll discounts, and more. This project demonstrates the practical application of GPS data and mathematical calculations in real-world scenarios.
```
