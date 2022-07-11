# ProcuringRealityProject

## Overview 

The focus of this project was to develop a *proof of concept* digital platform that simulates the processes of buying and selling property, in the residential real-estate industry, using blockchain and smart contract technology.


## Platform, Software & Tool Requirements

 To run this project, the following software is required:-

1. **Docker** 
2. **Docker-Compose**
3. **Geth client** 
4. **NodeJS** 
5. **Truffle**
6. **Process Manager 2 (pm2)** 
7. **Yarn Package Manager** 
8. **Metamask Browser Plugin**

# Operating Systems Tested
1. Ubuntu 18.04 - Windows Subsystem for Linux (WSL)
2. Ubuntu 16.04
3. macOS - High Sierra

# Web Browsers Tested
1. Firefox Quantum 
2. Brave Browser
3. Google Chrome 

# Setup Instructions

1. Ensure you have the above software installed
2. Navigate to the `network` directory
    - Run: `docker-compose build`.
    - Once that's done, run: `docker-compose up -d`.
    - Verify that the network was setup correctly by running `docker ps` to see a list of containers created.
    - Further verify that the authority nodes are up and mining, by running: `docker logs --tail 15 auth1`.
    - Navigate back to the root directory.
3. Navigate to the `contracts` directory
    - Execute the truffle migrations with: `truffle migrate --network development --reset`
    - Once that is complete, navigate back to the root directory.
4. Navigate into each of the following directories, one at a time, and run: `npm install` to install the necessary dependencies.
    - Client
    - Server
    - Oracles
5. Navigate to the root directory
    - Ensure you have *pm2* and the *yarn* package manager installed.
    - Run: `pm2 start`, this will start the client, server and oracle processes.
    - Verify that the client, server and oracles are all online in the console output.
    - Run: `pm2 logs client` to check if the client has fully loaded up yet
6. Proceed to open up 2 ***different*** web browsers.
    - I will assume `Browser A = Firefox Quantum` and `Browser B = Brave Browser`.
7. In Browser A,
    - Ensure you have installed and configured the Metamask browser extension/plugin.
    - Navigate to `http://localhost:8080`
    - Open the metamask extension
        - Click on the avatar in the top right corner
        - Navigate to `Settings -> Networks`
        - Click on *Add Network*
        - Give the network a name of your choice
        - For the RPC URL, enter the following: `http://localhost:10546` and save the changes.
        - Now select the newly added network from the list of available networks.
8. Repeat the steps for Browser A in Browser B
9. You will now have 2 browsers, both of which will have Metamask configured to connect to an authority node in the private ethereum network.
10. Proceed to use one browser as the *Buyer* and the other as the *Seller*.


Note:- Due to the scope of project , we chosen to only implement the use case wherein both parties are in complete agreement throughout all phases of the real-estate transaction.  
This is not true for many real-estate transactions that take place in the real industry today and such cases need to be treated with care as funds are held wthin smart contracts. 
