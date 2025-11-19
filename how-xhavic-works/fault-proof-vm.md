# Fault Proof VM

**A fault proof VM implements:**

* a smart-contract to verify a single execution-trace step, e.g. a single MIPS instruction.
* a CLI command to generate a proof of a single execution-trace step.
* a CLI command to compute a VM state-root at step N.

A fault proof VM relies on a fault proof program to provide an interface for fetching any missing pre-images based on hints.

The VM emulates the program, as prepared for the VM target architecture, and generates the state-root or instruction proof data as requested through the VM CLI.

Refer to the documentation of the fault proof VM for further usage information.

**Fault Proof VMs:**

* Cannon: big-endian 32-bit MIPS proof, by OP Labs, in active development.
* Asterisc: little-endian 64-bit RISC-V proof, by @protolambda , in active development.

### Fault Proof Interactive Dispute Game

The interactive dispute game allows actors to resolve a dispute with an onchain challenge-response game that bisects the execution trace of the VM, bounded with a base-case that proves a VM trace step.

The game is multi-player: different non-aligned actors may participate when bonded.

Response time is allocated based on the remaining time in the branch of the tree and alignment with the claim. The allocated response time is limited by the dispute-game window, and any additional time necessary based on L1 fee changes when bonds are insufficient.
