import random
import math

def generate_initial_state():
    return list(range(8))

def cost_function(state):
    attacks = 0
    for i in range(len(state)):
        for j in range(i + 1, len(state)):
            if state[i] == state[j] or abs(state[i] - state[j]) == j - i:
                attacks += 1
    return attacks

def get_neighbors(state):
    neighbors = []
    for i in range(len(state)):
        for j in range(i + 1, len(state)):
            neighbor = state[:]
            neighbor[i], neighbor[j] = neighbor[j], neighbor[i]
            neighbors.append(neighbor)
    return neighbors

def simulated_annealing():
    current_state = generate_initial_state()
    current_cost = cost_function(current_state)
    temperature = 1.0
    cooling_rate = 0.99

    while temperature > 0.01:
        neighbors = get_neighbors(current_state)
        next_state = random.choice(neighbors)
        next_cost = cost_function(next_state)

        if next_cost < current_cost or random.uniform(0, 1) < math.exp((current_cost - next_cost) / temperature):
            current_state = next_state
            current_cost = next_cost

        temperature *= cooling_rate

    return current_state, current_cost

if __name__ == "__main__":
    sa_solution, sa_cost = simulated_annealing()
    print("SA Solution:", sa_solution)
    print("SA Cost:", sa_cost)
