## Uint256 on Cosmwasm math

This is a very early stage idea of extending to Uint256 cosmwasm math file of std_cosmwasm module, the file can be found here:

[https://github.com/CosmWasm/cosmwasm/blob/master/packages/std/src/math.rs](https://)

Rust support natively numbers up to u128 and this cosmwasm library use a wrapper called Decimal to achieve std operation with fixed length math:

```
const DECIMAL_FRACTIONAL: u128 = 1_000_000_000_000_000_000;
```

this is the "one" so 1*10^18 which is quite tipical for many ethereum tokens.

We would like to add more "big numbers" natively to this library and so we would like to start with the possibility to have Uint256 numbers with std operations checked with overflows.

Looking around to the huge crates of Rust community I've found a implementation of big uint made by the Rust team:

[https://crates.io/crates/num-bigint](https://)

this is used by other crates to create more specifics numbers management, an interesting one for uint256 is:

[https://crates.io/crates/num256](https://)

which is exactly creating a struct for Uint256 and giving std operations on them.

I think this could be a starting point to add some bigger numbers to cosmwasm std module or maybe just to use in side projects to have less worries about bigger numbers.

Typical problem I suppose we will have to face are:

* Overflows/Underflows
* Multiplications
* Zero divide

In the example file I've isolated as a single project the math.rs file adding some examples in main function and test functions of elementary math on some Uint256.

So basically I just used the library **num256**, but crate could be extendend also to Uint512 in case of needing.

This is just a draft and any comments, advice or ideas are welcome to go on!

