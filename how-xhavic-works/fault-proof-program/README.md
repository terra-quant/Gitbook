# Fault Proof Program

The Fault Proof Program defines the verification of claims of the state-transition outputs of the L2 rollup as a pure function of L1 data.

The <mark style="color:orange;">`op-program`</mark> is the reference implementation of the program, based on <mark style="color:orange;">`op-node`</mark> and <mark style="color:orange;">`op-geth`</mark> implementations.

**The program consists of:**

* **Prologue:** load the inputs, given minimal bootstrapping, with possible test-overrides.
* **Main content:** process the L2 state-transition, i.e. derive the state changes from the L1 inputs.
* **Epilogue:** inspect the state changes to verify the claim.
