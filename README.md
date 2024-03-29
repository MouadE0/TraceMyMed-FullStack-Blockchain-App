<p align="center"><img align="middle" src="https://s2.gifyu.com/images/ezgif.com-video-to-gif874167c2f88f8eed.gif" /></p>
<img align="left" width="65" right="65" src="https://i.imgur.com/1itG47K.png">

# TraceMyMed (a blockchain project)

Tony Wu, Dylan Sechet, Yoni Gozlan and Mouad El Mensoum.

## Description

This project is a 2nd-year project for the elective course "Introduction to Blockchain" at CentraleSupélec.

It aims to implement a secure blockchain system that could be used to trace medecine in order to bring more transaprency and security to the supply chain. It allows to:

- Append transactions to the blockchain using _Proof of Work_
- Identify transactions with _elliptic curve_ signature
- Check if the current chain is valid
- Solve conflicts by replacing the current chain with the longest one in the network
- And more!

It also features a web-based frontend that allows the client to easily interact with the blockchain :

- Create wallets (a wallet is a container for private and public keys)
- Add new transactions while checking that they are possible
  - NB: To add initial items in the blockchain process, use the admin keys
- Fetch and display the current blocks
- Track the transaction history of a given batch.

You can check out the fully functioning website at https://tracemymedcs.herokuapp.com/

## Dependencies

- Flask (for the node server)
- Angular (for the frontend)
- Elliptic Curve Cryptography library (for cryptographic operations)
- Works with `Python 3.8.5`

## Installation

### Backend

Enter the shell terminal and run the following prompt to install the required modules:

```shell
pip install -r requirements.txt
```

or if you prefer Conda:

```shell
conda env create --file requirements-conda.txt
```

### Frontend

You can now just use our heroku frontend (no longer available): https://tracemymed.herokuapp.com/

If you'd rather host the frontend locally, follow the instructions below.
First, move to the project folder using `cd`.

Then run the following commands in your favorite shell:

```bash
conda install nodejs
npm install -g @angular/cli
cd ./Client/blockchainFrontend
npm install
```

## Usage

1. Move to the project folder using `cd`.

2. Start a blockchain node:

   ```bash
   python ./Blockchain/run_node.py
   ```

3. Start the client app:

   - Run the _flask_ backend server in a separate shell:

     ```
     python ./Client/crypto.py
     ```

   - Run the _angular_ frontend server in another shell (or use the [heroku page](https://tracemymed.herokuapp.com/)):

     ```
     cd Client/blockchainFrontend
     ng serve -o
     ```

   Your default browser should open the webpage automatically.

   Otherwise, enter the following url: http://localhost:4200/.

## Testing

- Start by generating and saving a few key keypairs, to represent the different actors along the chain (you can use the "Generate your wallet" button in the frontend for that - just reload the page once you've copied the credentials).
- Log in as administrator by navigating to the "Administrator" tab and generating the administrator wallet, then navigate to the transaction tab and create some initial transactions pointing to some of the public keys you've generated earlier.
- Log in as the owner of one of the public keys you've send a product to in the previous step, and repeat ! You can take a look at the generated blockchain at any time in the "Blockchain" tab, or track a product's history in "History".

NB : Some low-level tests that bypass the front-end client are also possible: some examples are given in [notebook_test](notebook_test/).
