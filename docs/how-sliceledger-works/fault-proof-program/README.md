# Fault Proof Program

The **Fault Proof Program** defines the verification of claims regarding **state-transition outputs** of the L2 rollup, treating them as a **pure function of L1 data**.\
It ensures that all L2 state changes can be independently verified without trusting external parties.\
<br>

#### Reference Implementation

The **op-program** serves as the reference implementation of the Fault Proof Program, built on the foundations of:

* **op-node**
* **op-geth**

This implementation provides a standard baseline for developers building compatible programs and proofs.

***

#### Program Structure

The program is divided into three main phases:

1. **Prologue**
   * Loads the necessary inputs using minimal bootstrapping.
   * Supports optional test overrides for development and debugging.
2. **Main Content**
   * Processes the **L2 state-transition**, deriving state changes from the provided L1 inputs.
   * Implements the core logic of state computation in a deterministic and verifiable manner.
3. **Epilogue**
   * Inspects the resulting state changes.
   * Verifies that the claimed outputs match the derived state, forming the final basis for dispute resolution.
