# FoodPrint
FoodPrint is a small scale farmer food supply chain web application for tracking food from farm to fork. FoodPrint is powered by Blockchain technology. 

## Overview
FoodPrint has 4 types of users:
- System Admin

The System Admin is responsible for setting up the infrastructure, initial data configuration and on-boarding of the various users.

- Farmer

The Farmer is responsible for capturing produce data at harvest time onto FoodPrint. The Farmer also transports the produce to the Market as per order from Market Admin.

- Market Admin

The Market Admin is responsible for receiving produce from the Farmer and capturing the relevant data onto FoodPrint.

- Market Patron

The Market Patron is the customer of the market. They purchase food from the Market. The Market Patron will be able to scan a barcode associated with produce and view the verified produce information and supply chain stories view information on the produce they are buying, it's source and journey, hence from farm to fork. Android versions 8 & 9 and iOS versions 11 & 12 can automatically scan QR codes using the camera app. 

## Documentation
- [Business Case](https://github.com/jajukajulz/foodprint/raw/master/docs/FoodPrint%20-%20Business%20Case%2008072019.pdf)

## Installation (Development Environment)
In order to run FoodPrint, an environment with the following is required:

- Node.js
- Truffle Framework
- Web3.js
- Bootstrap
- MySQL
- MetaMask (MetaMask is an extension for accessing Ethereum enabled distributed applications, or "Dapps" in your browser! The extension injects the Ethereum web3 API into every website's javascript context, so that dapps can read from the blockchain.)

1. Install Truffle globally. Truffle is the most popular smart contract development, testing, and deployment framework. 
```
$npm install -g truffle 
```

2. Install node dependencies.
```
$npm install
```

3. Start Ganache and Create a Workspace (or open an existing one). 

4. Confirm FoodPrint smart contract compiles successfully.
```
$truffle compile
```

5. Run tests for FoodPrint smart contract.
```
$truffe test
$truffle test --network development
```

4. Deploy FoodPrint smart contract to Ganache (assumes Ganache is running).

`truffle migrate` will run all migrations located within your project's migrations directory. If your migrations were previously run successfully, truffle migrate will start execution from the last migration that was run, running only newly created migrations. If no new migrations exists, `truffle migrate` won't perform any action at all. 
```
$truffle migrate
```

The --reset flag will force to run all your migrations scripts again. Compiling if some of the contracts have changed. You have to pay gas for the whole migration again. 
```
$truffle migrate --reset
```

The --all flag will force to recompile all your contracts. Even if they didn't change. It is more time compiling all your contracts, and after that it will have to run all your deploying scripts again.
```
$truffle migrate --compile-all --reset
```

If for some reason truffle fails to acknowledge a contract was modified and will not compile it again, delete the build/ directory. This will force a recompilation of all your contracts and running all your deploy scripts again.

5. Update `truffle-config.js` development network with NetworkID, Host and Port values from your local Blockchain in Ganache.

6. Create a MySQL database
```
run dbxml/foodprintDB.sql
```

7. Populate the MySQL database
```
run dbxml/foodprintDB_schema.sql
```

8. Create a database configuration file in the root folder - `dbconfig.json` and populate with updated json config as below

```
{
        "db_pool": {
        "host"      : <HOSTNAME>,
        "user"      : <USERNAME>,
        "password"  : <PASSWORD>,
        "database"  : <DATABASENAME>
    }
}
```

9. Start the web server (Express) and navigate to http://localhost:3000/ in your browser.
```
$npm run dev
```

## Other
1. Access deployed contract from CLI
```
$ truffle console
$ TheProduct.deployed().then(function(instance) { app = instance })
$ app.noHarvests()
```

2. Add a new migration
```
$touch 2_deploy_contract.js
```

3. Create infura project  at https://infura.io (Infura gives you access to test network).
This project will give you an ID that you will use in `truffle-config.js`
infura means you do not have to sync an ether node or rinkeby node to deploy directly.

4. Get test ether from https://faucet.rinkeby.io/ (you will need to create an Ethereum rinkeby wallet on MetaMask then use the address on twitter).
e.g. 0x4B67D20a4F27d248aF0462C23F8C193f073517FB

5. Update `truffle-config.js` with rinkeby. This will deploy from the metamask accounts, by default account 0 so specify which one you want.

6. Deploy to rinkeby. 
```
$truffle migrate --network rinkeby --compile-all --reset
```
7. Check contract on rinkeby etherscan https://rinkeby.etherscan.io

## Production Deployment
1. To deploy to a production server, first bundle and uglify then deploy
```
$npm run build
$npm run start
```

## Supported Browsers

| [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/edge/edge_48x48.png" alt="IE / Edge" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>IE / Edge | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png" alt="Firefox" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Firefox | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png" alt="Chrome" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Chrome | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari/safari_48x48.png" alt="Safari" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Safari | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari-ios/safari-ios_48x48.png" alt="iOS Safari" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>iOS Safari | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/samsung-internet/samsung-internet_48x48.png" alt="Samsung" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Samsung | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/opera/opera_48x48.png" alt="Opera" width="24px" height="24px" />](http://godban.github.io/browsers-support-badges/)</br>Opera |
| --------- | --------- | --------- | --------- | --------- | --------- | --------- |
| IE11, Edge| Supported| Supported| Supported| Supported| Supported| Supported
