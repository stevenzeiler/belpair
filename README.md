# belpair

A TypeScript library for managing SECP256k1 key pairs, forked from [bitcoinjs/ecpair](https://github.com/bitcoinjs/ecpair) and published under the name `belpair`.

**Status:** dormant since 2024-08. Last upstream-style package bump 2024-08-05, last commit by Steven 2024-08-26 (a README change). Version in `package.json` is 0.1.3.

## Where it came from

Almost all of the code is the work of the [bitcoinjs-lib](https://github.com/bitcoinjs/bitcoinjs-lib) contributors, under the MIT licence in `LICENSE`. This fork's history adds a few changes by other contributors: dropping the `randombytes` library, adding a random value for signing, a WIF version update and a Buffer type fix. It depends on `belcoinjs-lib` instead of `bitcoinjs-lib`, which suggests it targets a Bitcoin-derived chain with its own network parameters **(inference)**. Steven's own change is a README edit.

## Install

Not published or installed during the docs pass, so check the npm registry before relying on it.

```bash
npm install belpair
```

## Usage

You supply the elliptic-curve library, which must implement `TinySecp256k1Interface` (for example `tiny-secp256k1`). The import name in the code below follows the package name `belpair`; the upstream example used `ecpair`.

```typescript
import { ECPairFactory, ECPairAPI, TinySecp256k1Interface } from 'belpair';
import * as crypto from 'crypto';

const tinysecp: TinySecp256k1Interface = require('tiny-secp256k1');
const ECPair: ECPairAPI = ECPairFactory(tinysecp);

// From a WIF string (use your own key, never commit real ones)
const keyPair1 = ECPair.fromWIF('KXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX');
// From a random private key
const keyPair2 = ECPair.fromPrivateKey(crypto.randomBytes(32));
// Random key pair
const keyPair3 = ECPair.makeRandom();
// Custom random source (be careful)
const keyPair4 = ECPair.makeRandom({ rng: (size: number) => crypto.randomBytes(size) });
// From a public key (33 or 65 byte format)
const keyPair5 = ECPair.fromPublicKey(keyPair1.publicKey);

// Custom network
const network = {}; // your network object
ECPair.makeRandom({ network });
ECPair.fromWIF('wif key...', network);
// Several networks, if you are not sure which one applies
ECPair.fromWIF('wif key...', [network, {}, {}]);
```

## Configure

No environment variables.

## Build and test

```bash
npm install
npm run build   # compiles ts_src/ to src/ (src/ is git-ignored)
```

`npm test` is wired to build, format-check, lint and coverage, but the `test/` folder is not in this repo, so tests cannot run here. Not run during the docs pass.

## How it works

- `ts_src/ecpair.ts` has `ECPairFactory` and the key pair class: create from WIF, private key, public key or random; sign and verify; export WIF.
- `ts_src/types.ts` holds the type checks and interfaces.
- `ts_src/index.ts` re-exports the public API.
- `package.json` points `main` at `./src/index.js`, which only exists after a build.

## Licence

[MIT](LICENSE). Copyright the bitcoinjs-lib contributors. See `CONTRIBUTING.md` for the upstream contribution guide.
