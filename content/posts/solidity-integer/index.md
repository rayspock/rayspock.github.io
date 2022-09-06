---
title: "What Happens if You Overflow or Underflow Integer in Solidity?"
date: 2022-07-18
tags: ["100daysofcode", "solidity", "ethereum", "smart-contracts"]
share_img: posts/solidity-integer/elevate-overflow-unsplash.jpg
---

![image](elevate-overflow-unsplash.jpg)
<div class="cn"><sub>
Photo by <a class="au lc" target="_blank" href="https://unsplash.com/@elevatebeer?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Elevate</a> on <a class="au lc" target="_blank" href="https://unsplash.com/s/photos/overflow?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
</sub></div>

<br/>

Solidity is a programming language used to write smart contracts that are run on Ethereum Blockchain Node. To be precise, it runs on Ethereum Virtual Machine(EVM). Today, I’m about to share one of the more interesting behaviours I found in Solidity.

***Unsigned Integers***

Signed integral types (int) can represent both positive numbers and negative numbers, whereas Unsigned ones (uint) can only represent positive integers

***Size of Integers***

The default size of integers is 32 bytes, which can be declared as `uint`. Also, we can explicitly specify the size of integers by adding the trailing number of bits such as `uint8` which can store in 8 bits allowing 256 combinations (0 through 255).

What if we try to store the result of some arithmetic that falls outside of the declared range? In other programming languages, like Golang, the software may panic and disable the action ( causing an exception in the program), but it's not the case in Solidity(before version 0.8). It will still be runnable without failing the action, but the result won’t be what we expected, it will roll over to the next digit it can represent or store.

Feel free to try the code snippet below and see if you can overflow or underflow integers.
```solidity
pragma solidity >=0.6.0 <0.7.0;

contract Overflow {
    // value range : 0 ~ 255
    uint8 public balance;

    function maxTheBalance() public {
        balance = 2 ** 8 - 1;
    }

    // if the balance was 0, after decreasing it by 1, the balance will become 255
    function decrease() public {
        balance = balance - 1;
    }

    // if the balance was 255, after increasing it by 1, the balance will become 0
    function increase() public {
        balance = balance + 1; 
    } 
}
```
