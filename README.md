# Polygon Proof Module-3 
It is `pragma circom 2.0.0` language, which is a declarative language used for describing and implementing arithmetic circuits. This language is used in the context of zero-knowledge proofs and cryptographic applications to specify circuits and their logic.
## Description
It defines a simple circuit named `Circom`, which consists of three basic logic gates: AND, NOT, and OR. The circuit takes two input signals, `a` and `b`, and produces a single output signal, `Q`.
#### Signal declaration
```
// Declaration of signals.  
   signal input a;  
   signal input b;  

   //Declaration of intermediate signals or signal from gates 
   signal x;
   signal y;

   //Declaration of final signal output
   signal output Q;
```
1. `a` and `b` are input signals.
2. `x` and `y` are intermediate signals used to store the outputs of AND and NOT gates, respectively.
3. `Q` is the final output signal of the circuit.

#### Component gates
```
   //components gates used to create the circuit
   component andGate=AND();
   component notGate=NOT();
   component orGate=OR();
```
The code defines three templates for three basic gates: AND, NOT, and OR. These templates encapsulate the logic of each gate, taking input signals and producing an output signal based on their specific logic. Each template includes "input" and "output" signal declarations that represent the gate's input and output, respectively.        

#### Circuit Logic
```
   //circuit logic
   andGate.a <== a;
   andGate.b <== b;
   x <== andGate.out;

   notGate.in <== b;
   y <== notGate.out;

   orGate.a <== x;
   orGate.b <== y;
   Q <== orGate.out;
```
1. `andGate` is an instance of the AND template. It takes inputs `a` and `b` and produces an output `out` which is stored in the `x` signal.
2. `notGate` is an instance of the NOT template. It takes input `b` and produces an output `out` which is stored in the `y` signal.
3. `orGate` is an instance of the OR template. It takes inputs `x` and `y` and produces an output `out` which is the final output signal `Q`.
## Geting Started
### Prerequisites
1. Node.js and npm: Node.js and npm (Node Package Manager) should be installed on the system.
2. circom Compiler: You need the circom compiler to compile the circuit.circom file and generate the circuit intermediaries.
3. Ethereum Development Environment
### Executing program
**Step 1:** Make the clone of [this](https://github.com/gmchad/zardkat) respository in the system.   

**Step 2:** Open the terminal and install the node pack manager by given command.    
```
npm i
```

**Step 3:** In the same terminal or command prompt, run the following command to compile the circuit.circom file and generate the circuit intermediaries.
```
npx hardhat circom
```

**Step 4:** Open the input.json file and provide the inputs a=0, b=1 for generate the proof.          
```
{
  "a": 0,
  "b": 1
}
```

**Step 5:** Set up a connection to the Mumbai test network on Polygon Blockchain and provides the necessary account information to interact with the network using the specified private key which given in `.env` file.    

**Step 6:** Deploy by using following command on mumbai network.
```
npx hardhat run scripts/deploy.ts --network mumbai
```

**Step 7:** Verify the proof.   
 ## Authors
Abhishek
