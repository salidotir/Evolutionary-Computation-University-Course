# 8-Queens problem implementation using GA(genetic algorithms)

### What we do:

1) convert chessboard into an array of numbers:
   - index of each element shows coloumn number of chess board
   - the number at each index is the row that queen is in

2) Operators:
   - **Population initialization** -> initialize a population of population-size using initialize_fn
   - **Parent selection** -> **select best 2 parents out of random 5** to create 2 childs from with prpbability of crossover_prob
   - **Crossover** -> **one-point x-over (cut & crossfill x-over)** -> create child1 & child2
   - **Mutation** -> do mutation over each of childs created in the last step with prpbability of mutation_prob -> **swap operator**
   - **Survival selection** -> **replace two childs with 2 worst individuals in population**

3) Fitness function:
   - we should define a fitness function that calculates fitness for each individuals of population.
   - By this, we can find the best and the worst individuals in the population.
   
   - **Fitness-function**: 28 - number of pair of queens who threaten each other
      
   - Because we have a 8\*8 chess board, each queen can threaten at most other 7 queens. therfore we will have at most 7\*8=56 number of clashes which we have to divide by 2 in order to prevent same situations since forexample "A threatens B" is same as "B threatens A".

4) Main loop of algorithm:
```python
for i=1 to number_of_iterations:
  # select 2 best parents out of random 5
  parent1, parent2 = parent_selection_fn(population)

  # perform recombination(crossover) operator
  child1, child2 = crossover_fn(parent1, parent2, crossover_prob)

  # perform mutation over child1 & child2
  child1 = mutation_fn(child1, mutation_prob)
  child2 = mutation_fn(child2, mutation_prob)
                
  # check if any of new born chilren are answer or not
  if child1 is answer:
    answer = child1
    break

  if child2 is answer:
    answer = child2
    break

    # perform survival selection and create the new population with childs
    self.population = self.survival_selectrion_fn(self.population, child1, child2)
```
