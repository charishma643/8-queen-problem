import random

def generate_initial_population(size):
    return [list(range(8)) for _ in range(size)]

def fitness_function(state):
    return -cost_function(state)

def select_parents(population, fitnesses):
    total_fitness = sum(fitnesses)
    pick1 = random.uniform(0, total_fitness)
    pick2 = random.uniform(0, total_fitness)

    def roulette_wheel_selection():
        current = 0
        for i, fitness in enumerate(fitnesses):
            current += fitness
            if current > pick1:
                return i

    parent1 = roulette_wheel_selection()
    parent2 = roulette_wheel_selection()

    return population[parent1], population[parent2]

def crossover(parent1, parent2):
    point = random.randint(1, 7)
    child1 = parent1[:point] + parent2[point:]
    child2 = parent2[:point] + parent1[point:]
    return child1, child2

def mutate(state):
    i, j = random.sample(range(8), 2)
    state[i], state[j] = state[j], state[i]

def genetic_algorithm():
    population_size = 100
    generations = 1000
    mutation_rate = 0.1

    population = generate_initial_population(population_size)

    for _ in range(generations):
        fitnesses = [fitness_function(state) for state in population]
        new_population = []

        while len(new_population) < population_size:
            parent1, parent2 = select_parents(population, fitnesses)
            child1, child2 = crossover(parent1, parent2)

            if random.uniform(0, 1) < mutation_rate:
                mutate(child1)
            if random.uniform(0, 1) < mutation_rate:
                mutate(child2)

            new_population.extend([child1, child2])

        population = new_population

    best_state = max(population, key=lambda state: fitness_function(state))
    best_fitness = fitness_function(best_state)
    return best_state, best_fitness

if __name__ == "__main__":
    ga_solution, ga_fitness = genetic_algorithm()
    print("GA Solution:", ga_solution)
    print("GA Fitness:", ga_fitness)
