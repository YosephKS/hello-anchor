<div align="center">

# ⚓︎ Hello Anchor

This repository contains the a basic Solana program made using the Anchor Framework. The code contains all the necessary workflow to develop a Solana Program, from development, deployment, to testing.

</div>

## Table of Contents

- [🛠️ Getting Started](#%EF%B8%8F-getting-started)
  - [Solana CLI](#1-solana-cli)
  - [Anchor CLI](#2-anchor-cli)
  - [Solana Wallet](#3-solana-wallet)
- [🏗️ Development](%EF%B8%8F-development)
- [🚀 Deployment](#-deployment)
- [⚗️ Testing](#%EF%B8%8F-testing)
- [📜 License](#-license)

### 🛠️ Getting Started

This project assumes your local machine have Node and Cargo installed.

#### 1. Solana CLI

**MacOS & Linux**

```sh
sh -c "$(curl -sSfL https://release.solana.com/v1.9.5/install)"
```

**Windows**

```sh
curl https://release.solana.com/v1.9.5/solana-install-init-x86_64-pc-windows-msvc.exe --output C:\solana-install-tmp\solana-install-init.exe --create-dirs
```

#### 2. Anchor CLI

```sh
npm i -g @project-serum/anchor-cli
```

#### 3. Solana Wallet

For this tutorial, we're going to use a Filesystem wallet. This is sufficient for testing, but not recommended for production purpose.

```sh
solana-keygen new --no-outfile
```

### 🏗️ Development

Open [`lib.rs`](https://github.com/YosephKS/hello-anchor/blob/main/programs/hello-anchor/src/lib.rs) and edit the file to your needs. After completing the program, compile it to produce IDL.

```sh
anchor build
```

Once the IDL is generated, get the program id.

```sh
solana address -k target/deploy/hello_anchor-keypair.json
```

After the program id is generated, open [`Anchor.toml`](https://github.com/YosephKS/hello-anchor/blob/main/Anchor.toml) and add the following in it.

```toml
[programs.localnet]
hello_anchor = "program-id"
[programs.devnet]
hello_anchor = "program-id"
[programs.testnet]
hello_anchor = "program-id"
```

### 🚀 Deployment

To deploy the program to a chosen cluster,

```sh
anchor deploy --provider.cluster <cluster-name>
```

where `cluster-name` could be `localhost`, `testnet`, `devnet`, and `mainnet`.

### ⚗️ Testing

Once the program is deployed, you can test it with the following command.

```sh
anchor test
```

### 📜 License

[GNU Affero General Public License v3.0](https://github.com/YosephKS/hello-anchor/blob/main/LICENSE.md)
