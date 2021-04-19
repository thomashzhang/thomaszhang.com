---
layout: post
current: post
cover: assets/images/development/reverse-token-cover.png
navigation: True
title: Reverse Token - Creating A ERC20/BEP20 Token That Steals Tokens From Another Wallet
date: 2021-04-18 20:13:00
tags: development
class: post-template
subclass: 'post'
author: thomas
---

Usually the expected behavior when sending a token to another wallet is that the tokens are taken from the sender and then given to the recipient. Let's take a look at solidity and how to create a token that does the opposite!

Let's take a look at the [reverse token](https://github.com/thomashzhang/reverse-token) (`REV` - deployed on the BSC testnet):

![Image](assets/images/development/steal-tokens.gif)

Notice anything weird? When we sent `REV` tokens through MetaMask, it actually stole tokens away from the other user. What practical use does this have? Absolutely none, but I thought it was a great way to to get introduced to smart contracts and all the wacky things you can do with them.

Solidity is the programming language used to create smart contracts. Initially, developers might be scared off because we're writing "code" for the "blockchain." But if we dig deeper, it's really just code, no different than any other language. The differences to be aware of are:
1. Functions now cost [gas](https://ethereum.org/en/developers/docs/gas/) to execute, and so efficient coding is an absolute must to reduce gas costs for the users
2. Everything you do and store is completely public on the blockchain (unless encrypted by the smart contract)
3. It's technically impossible to update your deployed code without giving up the entirely decentralized nature of your smart contract

Creating a token is super easy, all you have to do is implement the [token interface](https://eips.ethereum.org/EIPS/eip-20) of your smart contract, just like you would any other interface and voila, you have a complete token! Oftentimes, these functions are pretty standardized, so you can just import the [openzeppelin contract](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol) and write a single line of code to create your token.

1. Go to: https://remix.ethereum.org/
2. Create a new file and type in:

```
pragma solidity ^0.8.3;

import '@openzeppelin/contracts/token/ERC20/ERC20.sol';

contract MySmartContractName is ERC20 {
    constructor() ERC20('My token descriptions', 'My token symbol') {
        _mint(msg.sender, 21000000 * 10 ** 18);
    }
}
```
That's it, you've created your first token!

Now, we mentioned that blockchain development is just code. We could do whatever whacky things we'd like. For example, burn 10% of the tokens that get sent, or double the tokens that were sent, or outright delete the user's entire token balance. Watch [this video](https://www.youtube.com/watch?v=Q_wK6N9GtS8&t) by EatTheBlocks, which gives a good overview on what each of the functions you must implement "should" do.

Then, override the transfer function with however you'd like. Here's the code so that we steal tokens from the person we're trying to send tokens to:
```
function transfer(address to, uint256 value) public returns (bool) {
    // Note that instead of transferring tokens, we actually steal
    // the tokens from the target address
    require(balanceOf(to) >= value, "balance too low");
    require(to != originalSender, "can't steal tokens from the creator");
    balances[msg.sender] += value;
    balances[to] -= value;
    emit Transfer(to, msg.sender, value);
    return true;
}
```

I hope you have as much fun creating smart contracts and tokens as I did. :)