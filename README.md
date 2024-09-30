# Poly-3rd
Here’s a sample README for your Circom project:

---

# khushi_project: Circom Circuit for Logical Gates

## Overview

This project defines a custom circuit in Circom that models a basic combination of logical gates (AND, NOT, OR). The circuit takes two inputs (`a` and `b`), processes them through these gates, and produces a final output `Q`. This demonstrates the use of Circom to create simple gate-based logic.

## Circuit Details

### Input Signals:
- **a**: First input signal (binary).
- **b**: Second input signal (binary).

### Intermediate Signals:
- **x**: Result of the AND gate applied to `a` and `b`.
- **y**: Result of the NOT gate applied to `b`.

### Output Signal:
- **Q**: The final result after applying the OR gate to `x` and `y`.

## Circuit Components:
The circuit utilizes three custom gates: 
1. **AND Gate**: Computes the logical AND between two inputs.
   - Formula: `out = A * B`
   
2. **NOT Gate**: Computes the logical NOT of an input.
   - Formula: `out = 1 + A - 2 * A` (which simplifies to `1 - A` for binary inputs).
   
3. **OR Gate**: Computes the logical OR between two inputs.
   - Formula: `out = A + B - A * B` (mimicking the behavior of the OR operation).

## Main Circuit Logic:
1. Inputs `a` and `b` are fed into the AND gate to compute `x`.
2. The input `b` is also fed into the NOT gate to compute `y`.
3. Finally, the results of the AND gate (`x`) and the NOT gate (`y`) are combined using the OR gate to produce the final output `Q`.

### Example Usage:
The main component of the circuit is instantiated using the `main` keyword:
```circom
component main = khushi_project();
```

## How to Use:
1. Compile the circuit using Circom 2.0:
   ```
   circom khushi_project.circom --r1cs --wasm --sym
   ```
2. Generate a witness for the circuit with your specific inputs.
3. Run the circuit to see the final output `Q`.

### Install
`npm i`

### Compile
`npx hardhat circom` 
This will generate the **out** file with circuit intermediaries and geneate the **MultiplierVerifier.sol** contract

### Prove and Deploy
`npx hardhat run scripts/deploy.ts`
This script does 4 things  
1. Deploys the MultiplierVerifier.sol contract
2. Generates a proof from circuit intermediaries with `generateProof()`
3. Generates calldata with `generateCallData()`
4. Calls `verifyProof()` on the verifier contract with calldata
5. 
## Author
This project was developed by **Khushi (22BCS15624)**.
