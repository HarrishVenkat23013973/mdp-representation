# MDP REPRESENTATION

## AIM:
To model a real-world Warehouse Robot Navigation system using a Markov Decision Process (MDP) and represent its states, actions, rewards, and transitions using Python.

------------------------------------------------------------------------------

# PROBLEM STATEMENT:

Problem Description:
A warehouse robot moves through different locations to pick up and deliver packages. At every location, the robot chooses an action such as moving, picking up a package, or delivering it. The objective is to maximize the total reward by completing deliveries efficiently while avoiding obstacles and unnecessary actions.


# State Space:

| State | Description            |
|-------|------------------------|
| S0    | Charging Station       |
| S1    | Storage Area           |
| S2    | Picking Shelf          |
| S3    | Packing Station        |
| S4    | Obstacle Area          |
| S5    | Delivery Completed     |


## Sample State:

## Current State: S2 (Picking Shelf)

## Meaning:
The robot has reached the picking shelf and is ready to collect a package before moving to the packing station.

------------------------------------------------------------------------------

# Action Space:

| Action | Description      |
|--------|------------------|
| A0     | Move Forward     |
| A1     | Move Left        |
| A2     | Move Right       |
| A3     | Pick Package     |
| A4     | Deliver Package  |
| A5     | Recharge Battery |

------------------------------------------------------------------------------

# Sample Action:

Current State : S2 (Picking Shelf)

Action        : Pick Package

Next State    : S3 (Packing Station)

Reward        : +20

------------------------------------------------------------------------------

# Reward Function:

| Current State        | Action           | Next State           | Reward |
|----------------------|------------------|----------------------|--------|
| Charging Station     | Move Forward     | Storage Area         | +5     |
| Storage Area         | Move Forward     | Picking Shelf        | +10    |
| Picking Shelf        | Pick Package     | Packing Station      | +20    |
| Packing Station      | Deliver Package  | Delivery Completed   | +50    |
| Storage Area         | Move Right       | Obstacle Area        | -20    |
| Obstacle Area        | Move Left        | Storage Area         | -5     |
| Any State            | Invalid Action   | Same State           | -10    |

------------------------------------------------------------------------------

# Graphical Representation:

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/c60b86d7-1fdc-4dff-bbfe-4f89f7591092" />


# PYTHON REPRESENTATION:

```python
# Warehouse Robot MDP

states = [
    "Charging Station",
    "Storage Area",
    "Picking Shelf",
    "Packing Station",
    "Obstacle Area",
    "Delivery Completed"
]

actions = [
    "Move Forward",
    "Move Left",
    "Move Right",
    "Pick Package",
    "Deliver Package",
    "Recharge Battery"
]

transitions = {
    ("Charging Station", "Move Forward"): ("Storage Area", 5),
    ("Storage Area", "Move Forward"): ("Picking Shelf", 10),
    ("Picking Shelf", "Pick Package"): ("Packing Station", 20),
    ("Packing Station", "Deliver Package"): ("Delivery Completed", 50),
    ("Storage Area", "Move Right"): ("Obstacle Area", -20),
    ("Obstacle Area", "Move Left"): ("Storage Area", -5)
}

current_state = "Charging Station"
action = "Move Forward"

print("Current State :", current_state)
print("Action        :", action)

if (current_state, action) in transitions:
    next_state, reward = transitions[(current_state, action)]
else:
    next_state = current_state
    reward = -10

print("Next State    :", next_state)
print("Reward        :", reward)
```
# OUTPUT:
<img width="286" height="80" alt="image" src="https://github.com/user-attachments/assets/9448ce75-730c-46c4-936c-5c33d873aa1f" />

# RESULT:
The Warehouse Robot Navigation problem was successfully represented as a Markov Decision Process (MDP). The states, actions, transition model, and reward function were defined using a real-world warehouse scenario, and the Python program correctly simulated a state transition and displayed the corresponding reward.
