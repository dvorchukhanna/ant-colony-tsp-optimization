# Ant Colony Optimization (ACO) for Travelling Salesperson Problem

A Python implementation of the **Ant Colony Optimization (ACO)** metaheuristic algorithm applied to solve the NP-hard **Travelling Salesperson Problem (TSP)** across 25 administrative centers of Ukraine.

## Overview
The Travelling Salesperson Problem seeks the shortest possible round-trip visit to a set of cities, returning to the origin city. Given 25 cities, the search space contains $(25-1)! / 2 \approx 3.1 \times 10^{23}$ candidate tours, making exact brute-force search computationally infeasible.

This project models artificial ant behavior using:
- **Pheromone trails ($\tau_{ij}$)** to balance exploitation of historically successful paths.
- **Heuristic desirability ($\eta_{ij} = 1 / d_{ij}$)** to encourage exploration of locally short edges.
- **Roulette-wheel probabilistic transition rule**:
  $$P_{ij} = \frac{(\tau_{ij})^\alpha \cdot (\eta_{ij})^\beta}{\sum_{k \in \text{allowed}} (\tau_{ik})^\alpha \cdot (\eta_{ik})^\beta}$$
- **Pheromone evaporation and global reinforcement** ($\rho$) to prevent premature stagnation at local optima.

## Features
- **Zero external dependencies**: Built purely with Python standard libraries (`random`).
- **Parameter grid-search**: Evaluates convergence and tour quality across combinations of $\alpha$, $\beta$, and $\rho$.
- **Customizable origin**: Default tour begins and terminates in Kyiv.

## Hyperparameters
- $\alpha$ (Pheromone influence weight): controls preference for heavily reinforced edges.
- $\beta$ (Heuristic visibility weight): controls preference for geometrically closer nodes.
- $\rho$ (Evaporation rate): controls rate of pheromone decay across iterations.

## How to Run

Ensure Python 3 is installed:
```bash
python3 main.py