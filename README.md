# Seminar_Assignment_1
Project Report
# CS260: Motion Planning
# Programming Assignment 1- Multiagent Navigation

## Name : Venkata Ranga Sai Vishal Matcha
## Sid : 862467756

## Social Force Model (SFM)

**Pros:**
- Captures social interactions and crowd behavior effectively.
- Considers psychological aspects of individuals in a crowd.
- Effective for simulating realistic crowd movements.

**Cons:**
- Computationally expensive, especially with many agents.
- Sensitive to parameter tuning.
- May not scale well for very dense crowds.

**Hyperparameters:**
- `goalRadius`: 2
- `dhor`: 10
- `ksi`: 0.5
- `A`: 2000
- `B`: 0.08
- `k`: 1.2e5
- `kappa`: 2.4e5
- `mass`: 80
- `maxF`: 10

## Time to Collision (TTC)

**Pros:**
- Simple and computationally efficient.
- Suitable for real-time applications.
- Doesn't require complex social interaction modeling.

**Cons:**
- Assumes all agents move with constant speed and in a straight line.
- Limited in capturing nuanced social behaviors.
- May result in unnatural-looking crowd movements.

**Hyperparameters:**
- `goalRadius`: 1
- `dhor`: 10
- `ksi`: 0.5
- `timehor`: 5
- `epsilon`: 0.2
- `maxF`: 10

## Velocity Obstacles (VO)

**Pros:**
- Considers the dynamic nature of the environment.
- Better suited for scenarios with non-linear and varying agent velocities.
- Can handle dense crowds effectively.

**Cons:**
- Complexity increases with the number of agents and varying velocities.
- Tuning parameters can be challenging.
- May lead to conservative decisions.

**Hyperparameters:**
- `goalRadius`: 1
- `dhor`: 10
- `epsilon`: 0.2

## Model Comparison Results

| No of Agents | SFM | TTC (epsilon=0) | TTC (epsilon=0.2) | VO (epsilon=0) | VO (epsilon=0.2) |
|--------------|-----|------------------|-------------------|----------------|-----------------|
| 3            | 144 | 138              | 139               | 131            | 134             |
| 5            | 162 | 168              | 146               | 139            | 141             |
| 8            | 277 | 181              | 183               | 130            | 143             |

*Unit of comparison is the number of iterations.*

## Conclusion

Based on the observations, the Time to Collision model (TTC) performed better for all the agents with an epsilon value of 0.2, even though Velocity Obstacle (VO) had fewer iterations. There were still a few collisions with VO, emphasizing the importance of parameter tuning for specific scenarios.
