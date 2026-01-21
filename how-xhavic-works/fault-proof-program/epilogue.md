# Epilogue

While the main-content produces the disputed L2 state already, the epilogue concludes what this means for the disputed claim.

**The program produces a binary output to verify the claim, using a standard single-byte Unix exit-code:**

* a <mark style="color:orange;">`0`</mark> for success, i.e. the claim is correct.
* a non-zero code for failure, i.e. the claim is incorrect.
  1. <mark style="color:orange;">`1`</mark> should be preferred for identifying an incorrect claim.
  2. Other non-zero exit codes may indicate runtime failure, e.g. a bug in the program code may resolve in a kind of <mark style="color:orange;">`panic`</mark> or unexpected error. Safety should be preferred over liveness in this case, and the <mark style="color:orange;">`claim`</mark> will fail.

To assert the disputed claim, the epilogue, like the main content, can introspect L1 and L2 chain data and post-process it further, to then make a statement about the claim with the final exit code.

**A disputed output-root may be disproven by first producing the output-root, and then comparing it:**

1. Retrieve the output attributes from the L2 chain view: the state-root, block-hash, withdrawals storage-root.
2. Compute the output-root, as the proposer should compute it.
3. If the output-root matches the <mark style="color:orange;">`claim`</mark> , exit with code 0. Otherwise, exit with code 1.

> _**Note: the dispute game interface is actively changing, and may require additional claim assertions. the output-root epilogue may be replaced or extended for general L2 message proving.**_
