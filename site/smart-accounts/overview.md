---
outline: deep
head:
  - - meta
    - property: og:title
      content: Smart Accounts
  - - meta
    - name: description
      content: Follow this guide to understand the end-to-end process of integrating smart accounts in your applications with Account Kit.
  - - meta
    - property: og:description
      content: Follow this guide to understand the end-to-end process of integrating smart accounts in your applications with Account Kit.
  - - meta
    - name: twitter:title
      content: Smart Accounts
  - - meta
    - name: twitter:description
      content: Follow this guide to understand the end-to-end process of integrating smart accounts in your applications with Account Kit.
prev:
  text: Packages Overview
  link: /package-overview
next:
  text: Choosing a Smart Account
---

# Overview

In this guide we'll explain the end-to-end journey of integrating smart accounts in your applications with Account Kit. We'll cover the necessary steps such as creating an Alchemy account, selecting the right account and Signer and sending a User Operation. Additionally, we'll touch upon advanced functionalities like sponsoring gas, batching transactions and transferring ownership.

## 1. Setting Up an Alchemy Account

Before diving into smart accounts, it's important to [set up your Alchemy account](https://auth.alchemy.com/signup). This will allow you to access the Alchemy API key which is required to initialize a provider and interact with the blockchain. Additionally, you'll get access to our Gas Manager, which will enable you to sponsor gas for your users.

## 2. Deploying a Smart Account

The next step is to select the right smart account implementation for your application. We recommend using `LightAccount`, which is a simple, secure, and cost-effective solution for most use cases. It supports features such as owner transfers, [ERC-1271](https://eips.ethereum.org/EIPS/eip-1271) message signing, batched transactions and more. However, if you're looking for more advanced features, you can use your own account implementation. We'll cover both options in detail in the following sections:

- [Using Light Account](/smart-accounts/accounts/guides/light-account)
- [Using your own account implementation](/smart-accounts/accounts/guides/using-your-own)

::: tip Note
The `LightAccount` implementation is not [ERC-6900](/smart-accounts/accounts/guides/modular-account) compliant. The `ModularAccount` implementation is launching later this year and will be EIP-6900 compatible. However, `LightAccount` is forward-compatible with `ModularAccount` and can be upgraded to it in the future.
:::

## 3. Choosing a Signer

A Signer is the entity that signs transactions (User Operations) on behalf of the smart account. It can be an EOA, a custodial service, or a multi-party computation (MPC) service. We explain the different types of signers in detail in the [overview](signers/choosing-a-signer) section on choosing a Signer and offer integration guides in these docs, many of which use our `aa-signers` SDK.

At this point you should be able to integrate smart accounts in your application. However, there are a few advanced features that can help you improve the user experience and save on gas costs. Information about these can be found in the `Guides` section.

## 4. Sponsoring Gas

Being able to sponsor gas for your users is one of the most powerful features enabled by smart accounts and can help you build a seamless user experience. We'll cover this in detail with code examples in the [Sponsoring Gas](/tutorials/sponsoring-gas/sponsoring-gas) section.

## 5. Batching Transactions

Transaction batching allows you to bundle multiple transaction calls into a single User Operation and execute them in a single atomic transaction. This can help you save on gas costs and improve the user experience. We'll cover this in detail with code examples in the [Batching Transactions](/tutorials/batching-transactions) section.

## 6. Transferring Ownership

Ownership is an important aspect of smart accounts. The Light Account implementation allows you to transfer the ownership of a smart account to another entity. We'll cover this in detail with code examples in the [Transferring Ownership](/tutorials/transferring-ownership) section.
