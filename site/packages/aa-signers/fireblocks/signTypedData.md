---
outline: deep
head:
  - - meta
    - property: og:title
      content: FireblocksSigner • signTypedData
  - - meta
    - name: description
      content: Overview of the signTypedData method on FireblocksSigner
  - - meta
    - property: og:description
      content: Overview of the signTypedData method on FireblocksSigner
---

# signTypedData

`signTypedData` supports signing typed data from the `FireblocksSigner`.

This method must be called after [`authenticate`](/packages/aa-signers/fireblocks/authenticate). Otherwise, this method will throw an error with the message `Not Authenticated`.

## Usage

::: code-group

```ts [example.ts]
import { createFireblocksSigner } from "./fireblocks";
// [!code focus:99]
const fireblocksSigner = await createFireblocksSigner();

const signedTypedData = await fireblocksSigner.signTypedData({
  domain: {
    name: "Ether Mail",
    version: "1",
    chainId: 1,
    verifyingContract: "0xCcCCccccCCCCcCCCCCCcCcCccCcCCCcCcccccccC",
  },
  types: {
    Person: [
      { name: "name", type: "string" },
      { name: "wallet", type: "address" },
    ],
    Mail: [
      { name: "from", type: "Person" },
      { name: "to", type: "Person" },
      { name: "contents", type: "string" },
    ],
  },
  primaryType: "Mail",
  message: {
    from: {
      name: "Cow",
      wallet: "0xCD2a3d9F938E13CD947Ec05AbC7FE734Df8DD826",
    },
    to: {
      name: "Bob",
      wallet: "0xbBbBBBBbbBBBbbbBbbBbbbbBBbBbbbbBbBbbBBbB",
    },
    contents: "Hello, Bob!",
  },
});
```

<<< @/snippets/fireblocks.ts
:::

## Returns

### `Promise<Hex>`

A Promise containing the signature of the typed data.

## Parameters

### `params: SignTypedDataParams` -- the typed data to sign

- `domain: TypedDataDomain` -- The typed data domain
- `types: Object` -- the type definitions for the typed data
- `primaryType: inferred String` -- the primary type to extract from types and use in value
- `message: inferred from types & primaryType` -- the message, inferred from
