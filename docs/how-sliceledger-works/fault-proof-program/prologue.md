# Prologue

**The program is bootstrapped with two primary inputs:**

* <mark style="color:orange;">`l1_head`</mark> : the L1 block hash that will be perceived as the tip of the L1 chain, authenticating all prior L1 history.
* <mark style="color:orange;">`dispute`</mark> : identity of the claim to verify.

Bootstrapping happens through special input requests to the host of the program.

**Additionally, there are implied inputs, which are derived from the above primary inputs, but can be overridden for testing purposes:**

* <mark style="color:orange;">`l2_head`</mark> : the L2 block hash that will be perceived as the previously agreed upon tip of the L2 chain, authenticating all prior L2 history.
* Chain configurations: chain configuration may be baked into the program, or determined from attributes of the identified <mark style="color:orange;">`dispute`</mark> on L1.
  * <mark style="color:orange;">`l1_chain_config`</mark> : The chain-configuration of the L1 chain (also known as `l1_genesis.json` )
  * <mark style="color:orange;">`l2_chain_config`</mark> : The chain-configuration of the L2 chain (also known as <mark style="color:orange;">`l2_genesis.json`</mark> )
  * <mark style="color:orange;">`rollup_config`</mark> : The rollup configuration used by the rollup-node (also known as <mark style="color:orange;">`rollup.json`</mark> )

The implied inputs rely on L1-introspection to load attributes of the <mark style="color:orange;">`dispute`</mark> through the dispute game interface, in the L1 history up and till the specified <mark style="color:orange;">`l1_head`</mark> .

The <mark style="color:orange;">`dispute`</mark> may be the claim itself, or a pointer to specific prior claimed data in L1, depending on the dispute game interface.

Implied inputs are loaded in a "prologue" before the actual core state-transition function executes. During testing a simplified prologue that loads the overrides may be used.

> _**Note: only the test-prologues are currently supported, since the dispute game interface is actively changing.**_
