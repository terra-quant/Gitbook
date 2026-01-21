# Fault Proof Virtual Machine

The **Fault Proof VM** provides a framework for verifying individual execution steps of a virtual machine in a trustless and auditable manner. It is primarily used to enable **interactive dispute resolution** in an OP Stack–style L2 environment.

#### Features

A Fault Proof VM implements the following:

1. **Smart contract verification**
   * Verifies a single execution-trace step (e.g., a single MIPS or RISC-V instruction) on-chain.
2. **Command-line interface (CLI) utilities**
   * Generate a proof for a single execution-trace step.
   * Compute a VM **state-root** at a specified step NNN.
3. **Fault proof program interface**
   * Provides access to missing pre-images based on hints for state reconstruction.
   * Ensures the VM can emulate a program prepared for the target architecture and generate the required **state-root** or **instruction proof data** via the CLI.

***

#### Supported Fault Proof VMs

| VM Name      | Architecture  | Endianness    | Maintainer   | Status             |
| ------------ | ------------- | ------------- | ------------ | ------------------ |
| **Cannon**   | 32-bit MIPS   | Big-endian    | OP Labs      | Active development |
| **Asterisc** | 64-bit RISC-V | Little-endian | @protolambda | Active development |

> Refer to the individual VM documentation for implementation details and usage instructions.

***

### Fault Proof Interactive Dispute Game

The **Interactive Dispute Game** allows participants to resolve disputes about VM execution on-chain.

#### How it works

* The game is **multi-player**: multiple non-aligned actors can participate if they post the required bond.
* The dispute is resolved through a **challenge-response protocol** that recursively bisects the execution trace of the VM.
* Base-case verification is achieved by proving a single VM trace step on-chain.

#### Timing and Response

* **Response times** are allocated based on:
  * Remaining time in the disputed branch of the execution tree
  * Alignment of the responder with the claim
* Maximum response times are limited by the **dispute-game window**.
* Additional time may be granted to account for **L1 fee fluctuations** if posted bonds are insufficient to cover transaction costs.

#### Security and Usage

* Ensures **trustless verification** of L2 execution without needing to replay the full trace on-chain.
* All participants must bond funds, which are slashed in case of invalid responses.
* Designed for **developers building fraud-proofed L2 systems**, enabling secure, verifiable execution.
