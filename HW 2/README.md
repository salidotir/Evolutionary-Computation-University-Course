# Schwefel optimization function using Evolutionary Strategy(ES)

### What we do

The goal is to find the global minimum of the Schwefel objective function using ES algorithm.

The function is defined as below:

> <img src="https://user-images.githubusercontent.com/35997721/161028045-23539e87-9085-469f-8f4a-3c425a41aff8.jpg" width="400">
> 
> <img src="https://user-images.githubusercontent.com/35997721/161028542-27585ec0-7591-4a59-bbc9-8cb25d9e12e4.png" width="400">

Since we are dealing with a continous space, we will use ES as the type of all 4 evolutionary algorithms. The configuration will be set in a seperate configuration-file.

### Default Configuration:
- ES-type: only children will transfer to next generation | ( 𝜇 ,  𝜆 )
- objective function dimension(N): 2
- range of chromosome values(x-range): (-512, +512)
- number of parents selected for next generation( 𝜇 ): 20
- population size( 𝜆 ): 100
- mutation: enabled
- mutation-type: type-1
- mutation step-size( 𝜎 ): 0.15
- recombination-type: type-1


### How to run program:

``` python
model = SchwefelFunctionES(objective_fn=Schwefel_fn, config_file_path=None)
# model = SchwefelFunctionES(objective_fn=Schwefel_fn, config_file_path="config.txt")

_, _ = model.es_main_loop()
```

### output:

> <img src="https://user-images.githubusercontent.com/35997721/161029646-c9abf864-8b56-454b-bb65-f5ebdc282ffc.jpg" width="900">
