# Neural Network from scratch in C++

A C++ implementation of neural networks and perceptrons from scratch I did as a project during my Bachelor's, with manual implementation of Matrix and matrix operations, backpropagation training, multiple activation functions, and support for various datasets.

## Features

### Neural Networks
- Multi-layer neural networks with configurable architecture
- Backpropagation training algorithm
- Multiple activation functions: tanh, sigmoid, linear
- Loss functions: mean squared error
- Support for training and validation datasets

### Perceptrons
- Single-layer perceptron implementation
- Training for basic logical operations (AND, OR, NAND, XOR)

### Datasets Included
- XOR problem
- Abalone dataset (regression)
- Boston Housing dataset (regression)
- Sine function approximation
- Sinc function approximation

## Requirements

- GCC 13 or later (g++-13)
- C++23 standard support
- Linux environment

## Building

To build the project, run:

```bash
make all
```

This will compile `main.cpp` with debugging symbols enabled.

For a release build with optimizations:

```bash
make release
```

## Usage

After building, run the executable:

```bash
./programa
```

The program contains various commented-out examples. Uncomment the desired section in `main.cpp` to test different neural network configurations or perceptron operations.

### Example: XOR Neural Network

Uncomment the XOR section in `main.cpp` to train a neural network on the XOR problem:

```cpp
// XOR example code
Matrix x_test({0,0, 0,1, 1,0, 1,1}, 2);
Matrix y_test({0,1,1,0}, 1);

std::vector<LayerDescriptor> arch;
arch.emplace_back(2, ActivationFunctions::tanh);
arch.emplace_back(1, ActivationFunctions::tanh);

NeuralNetwork nn(2, arch, LossFunctions::mean_squared_error, 0.1);
TrainResult r = nn.fit(x_test, y_test, 10000, true);
```

### Example: Perceptron AND Gate

Uncomment the AND section to train a perceptron for logical AND:

```cpp
Matrix x_test({0,0, 0,1, 1,0, 1,1}, 2);
Matrix y_and({-1,-1,-1,1}, 1);

Perceptron p_and;
p_and.fit(x_test, y_and, 1000);
```

## Project Structure

```
.
├── main.cpp                 # Main program with examples
├── makefile                 # Build configuration
├── include/                 # Header files
│   ├── neural_network.hpp   # Neural network class
│   ├── perceptron.hpp       # Perceptron class
│   ├── matrix.hpp           # Matrix operations
│   ├── layer.hpp            # Neural network layer
│   ├── activation_functions.hpp # Activation functions
│   ├── loss_functions.hpp   # Loss functions
│   ├── layer_descriptor.hpp # Layer configuration
│   ├── train_result.hpp     # Training results
│   └── random.hpp           # Random utilities
├── *.csv                    # Dataset files
└── prueba-backpropagation.ipynb # Jupyter notebook for testing
```

## Dependencies

The project uses only standard C++ libraries and no external dependencies beyond the compiler.

## Credits

This project was developed by Eduard Duta and Francisco Wendeburg (wendeburg).