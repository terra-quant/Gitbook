# Main Content

To verify a claim about L2 state, the program first reproduces the L2 state by applying L1 data to prior agreed L2 history.

This process is also known as the L2 derivation process, and matches the processing in the rollup node and execution-engine.

The difference is that rather than retrieving inputs from an RPC and applying state changes to disk, the inputs are loaded through the pre-image oracle and the changes accumulate in memory.

**The derivation executes with two data-sources:**

* Interface to read-only L1 chain, backed by the pre-image oracle
  1. Prior L2 chain history is backed by the pre-image oracle, similar to the L1 chain:
  2. The <mark style="color:orange;">`l1_head`</mark> determines the view over the available L1 data: no later L1 data is available.
  3. The implementation of the chain traverses the header-chain from the <mark style="color:orange;">`l1_head`</mark> down to serve by-number queries.
  4. The <mark style="color:orange;">`l1_head`</mark> is the L1 unsafe head, safe head, and finalized head.
* Interface to L2 engine API
  1. Prior L2 chain history is backed by the pre-image oracle, similar to the L1 chain:
     * [ ] The initial <mark style="color:orange;">`l2_head`</mark> determines the view over the initial available L2 history: no later L2 data is available.
     * [ ] The implementation of the chain traverses the header-chain from the <mark style="color:orange;">`l2_head`</mark> down to serve by-number queries.
     * [ ] The <mark style="color:orange;">`l2_head`</mark> is the initial L2 unsafe head, safe head, and finalized head.
  2. New L2 chain history accumulates in memory.
     * [ ] Although the pre-image oracle can be used to retrieve data by hash if memory is limited, the program should prefer to keep the newly created chain data in memory, to minimize pre-image oracle access.
     * [ ] The L2 unsafe head, safe head, and finalized L2 head will potentially change as derivation progresses.
     * [ ] L2 state consists of the diff of changes in memory, and any unchanged state nodes accessible through the read-only L2 history view.

See Pre-image routes for specifications of the pre-image oracle backing of these data sources.

**Using these data-sources, the derivation pipeline is processed till we hit one of two conditions:**

* <mark style="color:orange;">`EOF`</mark> : when we run out of L1 data, the L2 chain will not change further, and the epilogue can start.
* Eager epilogue condition: depending on the type of claim to verify, if the L2 result irreversible (i.e. no later L1 inputs can override it), the processing may end early when the result is ready. E.g. when asserting state at a specific L2 block, rather than the very tip of the L2 chain.
