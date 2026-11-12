+++
title =  "A Brief Intro to Evolutionary Algorithms!"
tags = ["Python"]
date = "2019-03-02"
+++

Often a simple introduction to a topic that seems complex can certainly help understanding it. Evolutionary computation was something I was truly in awe of and wanted to learn more about. I am taking a math project research course and decided to implement a enolutionary algorithm that plays tetris. However, decided to write a few simple enolutionary algorithms to help understand the concepts. 


### An evolutionary algorithm?! What's that! 

First let's define what an evolutionary algorithm is and how we can build one! Wikipedia defines an evolutionary algorithm as: "a generic population-based metaheuristic optimization algorithm." Evolutionary algorithms use mechanisms such as reproduction, mutation, recombination, and selection! In other terms you would use a population of whatever you are trying to optimize, select some of the population, and create a way to reproduce your population.

A few terms we should cover before starting:

1. population: number of possible solutions to the problem.
1. chromosome: one of the possible solutions from the population.
2. generation: 
2. fitness test:
3. selection
4. crossover
4. mutation

### Let's evolve primes! 

For our simple example, we can create an evolutionary algorithm to evolve prime numbers out of an array of numbers. 

```
def create_population():
  pop = []
  for i in xrange(20):
    pop.append(random.randint(1, 1000))
  return pop
```

After we create the population, we want to determine how to measure how close we are to numbers we want! Our fitness test here is very simple, a number can either be prime or not. In other cases the fitness would have a score and you would want to either minimize or maximize the score to get to your set goal

Our fitness function would look like:

```
def fitness(number):
  fitness = 0
  if isPrime(number):
    fitness = 1
  return fitness
```

Next we would want to create our crossover function, this will be used to create number babies from the parents. There are many different ways to crossover, the most simple one would be a single point crossover! Where we take the same part from each gene and switch them over. In our example we take two numbers, convert them to binary representation, and slice them in half and switch them over.

The crossover function would look like:

```
def crossover(dna1, dna2): 
  bin1 = str(bin(dna1))[2:]
  bin2 = str(bin(dna2))[2:]
  length = len(bin1)
  if length < len(bin2):
    length = len(bin2)
  pos = int(random.random() * length)
  crossover1 = bin1[:pos]+bin2[pos:]
  crossover2 = bin2[:pos]+bin1[pos:]
  ```

Since crossovers are basically changing up genes that come from the parent, we are also able to add traits that do not come from the parent genes, this is called the Mutation. Our mutation function takes a number and adds/subtracts a random number between -10 and 10. This type of mutation would be called a creep mutation. Another mutation that would work well for evolving primes is changing the last binary digit in the number to a 1 if its a 0 as most prime numbers are odd. 

```
def mutate(num):
  return num + random.randint(-10, 10)
```

After that all we have to do is run our algorithm a bunch of times to evolve our numbers! 

<!-- ![]() -->
<img src="/evolvePrimesGenerationResult.png"  width="800" height="400" />
