# Fraud Proof

## Overview

**A fault proof, also known as fraud proof or interactive game, consists of 3 components:**

1. **Program:** given a commitment to all rollup inputs (L1 data) and the dispute, verify the dispute statelessly.
2. **VM:** given a stateless program and its inputs, trace any instruction step, and prove it on L1.
3. **Interactive Dispute Game:** bisect a dispute down to a single instruction, and resolve the base-case using the VM.

Each of these 3 components may have different implementations, which can be combined into different proof stacks, and contribute to proof diversity when resolving a dispute.

"Stateless execution" of the program, and its individual instructions, refers to reproducing the exact same computation by authenticating the inputs with a Pre-image Oracle.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

## Pre-image Oracle

The pre-image oracle is the only form of communication between the Program (in the Client role) and the VM (in the Server role).

**The program uses the pre-image oracle to query any input data that is understood to be available to the user:**

* The initial inputs to bootstrap the program. See Bootstrapping.
* External data not already part of the program code. See Pre-image hinting routes.

The communication happens over a simple request-response wire protocol, see Preimage communication.
