---
title: Deploying your first smart contract
description: An introduction to deploying your first smart contract on an Ethereum test network
author: "jdourlens"
tags: ["smart contracts", "remix", "solidity", "deploying"]
skill: beginner
lang: en
published: 2020-04-03
source: EthereumDev
sourceUrl: https://ethereumdev.io/deploying-your-first-smart-contract/
address: "0x19dE91Af973F404EDF5B4c093983a7c6E3EC8ccE"
---

I guess you are as excited as us to [deploy](/developers/docs/smart-contracts/deploying/) and interact with your first [smart contract](/developers/docs/smart-contracts/) on the Ethereum blockchain.

Don’t worry, as it’s our first smart contract, we’ll deploy it on a [local test network](/developers/docs/networks/) so it does not cost anything for you to deploy and play as much as you’d like with it.

## Writing our contract {#writing-our-contract}

To begin, go to the [Remix website](https://remix.ethereum.org/) and initiate the process by creating a new file. In the top-left corner of the Remix interface, select the icon "create new file" and then choose a filename of your preference. For instance, you can name it "first-smart-contract.sol." This extension _.sol_ designates it as a piece of code written in the Solidity programming language.

![Adding a new file in the Remix interface](./remix.png)

In the newly created file, you should insert the following Solidity code:

```solidity
1  // SPDX-License-Identifier: MIT
2  pragma solidity >=0.5.17;
3  
4  contract Counter {
5  
6      // Public variable of type unsigned int to keep the number of counts
7      uint256 public count = 0;
8  
9      // Function that increments our counter
10     function increment() public {
11         count += 1;
12     }
13  
14     // Not necessary getter to get the count value
15     function getCount() public view returns (uint256) {
16         return count;
17     }
18 }
```

Let's take a closer look and gain a better understanding of the code example given.

Line 4: In this line, we define a Solidity contract named Counter.
Line 7: Within the contract, we have a public variable named count, which is of type unsigned integer (uint256). It starts with an initial value of 0.
Line 10: This line contains a function called increment(). When called, this function increases the value of the count variable by 1. It modifies the state of the contract.
Line 15: The code features another function named getCount(). This function is essentially a getter, allowing you to read the value of the count variable. It is marked as view, meaning it doesn't alter the state of the contract. Note that, in this case, declaring a separate getter is optional since the count variable is already marked as public, making its value accessible externally.

The structure of this code resembles that of classes in object-oriented programming languages like Java or C++. It serves as a basic example of a smart contract. You can now proceed to interact with and deploy this contract.

## Deploying our contract {#deploying-our-contract}

As we wrote our very first smart contract, we’ll now deploy it to the blockchain to be able to play with it.

[Deploying the smart contract on the blockchain](/developers/docs/smart-contracts/deploying/) is actually just sending a transaction containing the code of the compiled smart contract without specifying any recipients.

We’ll first [compile the contract](/developers/docs/smart-contracts/compiling/) by clicking on the compile icon on the left hand side:

![The compile icon in the Remix toolbar](./remix-compile-button.png)

Then click on the compile button:

![The compile button in the Remix solidity compiler](./remix-compile.png)

You can choose to select the “Auto compile” option so the contract will always be compiled when you save the content on the text editor.

Then navigate to the deploy and run transactions screen:

![The deploy icon in the Remix toolbar](./remix-deploy.png)

Once you are on the "deploy and run" transactions screen, double check that your contract name appears and click on Deploy. As you can see on the top of the page, the current environment is “JavaScript VM” that means that we’ll deploy and interact with our smart contract on a local test blockchain to be able to test faster and without any fees.

![The deploy button in the Remix solidity compiler](./remix-deploy-button.png)

Once you've clicked the “Deploy” button, you’ll see your contract appear on the bottom. Click the arrow on the left to expand it so we’ll see the content of our contract. This is our variable `counter`, our `increment()` function and the getter `getCounter()`.

If you click on the `count` or `getCount` button, it will actually retrieve the content of the contract’s `count` variable and display it. As we did not called the `increment` function yet, it should display 0.

![The function button in the Remix solidity compiler](./remix-function-button.png)

Let’s now call the `increment` function by clicking on the button. You’ll see logs of the transactions that are made appearing on the bottom of the window. You’ll see that the logs are different when you’re pressing the button to retrieve the data instead of the `increment` button. It’s because reading data on the blockchain does not need any transactions (writing) or fees. Because only modifying the state of the blockchain requires to make a transaction:

![A log of transactions](./transaction-log.png)

After pressing the increment button that will generate a transaction to call our `increment()` function if we click back on the count or getCount buttons we’ll read the newly updated state of our smart contract with the count variable being bigger than 0.

![Newly updated state of the smart contract](./updated-state.png)

In the next tutorial, we’ll cover [how you can add events to your smart contracts](/developers/tutorials/logging-events-smart-contracts/). Logging events is a convenient way to debug your smart contract and understand what is happening while calling a function.
