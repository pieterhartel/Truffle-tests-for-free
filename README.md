# Truffle-tests-for-free
Verified smart contracts with truffle tests generated from the first 50 historic transactions on the blockchain

## Summary

This repository contains the source code and tests of a sample of about 1100 verified smart contracts that were downloaded on 1 Jan 2019 from etherscan.io. The file `scrapedcontractsVerified.json` contains the name, address and other relevant data of all verified smart contracts present on 1 Jan 2019 on https://etherscan.io/contractsVerified

For each contract there is a directory with the files needed by the `truffle test` command. The test script in the `test` directory has been generated from the first up to 50 historic transactions on the block chain as described in a paper currently under review.

## Prerequisites

```
$ truffle version
Truffle v5.0.2 (core: 5.0.2)
Solidity - 0.4.19 (solc-js)
Node v10.15.0
$ ganache-cli -v
Ganache CLI v6.2.5 (ganache-core: 2.3.3)
```

Some contracts cannot be compiled with versions of Truffle later than v5.0.2.

## Description

A test consists of executing the file `make.sh` in the directory of the contract. This shell script fires up `ganache-cli` with the parameters needed for the test. It then runs `truffle test` to compile, and deploy the contract, and to run the test. The example below was generated from the verified source available here: https://etherscan.io/address/0xef7c7254c290df3d167182356255cdfd8d3b400b#contracts
```
Vitaluck_3b400b.dir/
├── contracts
│   ├── Migrations.sol
│   └── Vitaluck.sol
├── ganache.log
├── make.log
├── make.sh
├── migrations
│   └── 1_initial_migration.js
├── replay.js
├── test
│   ├── support.js
│   └── vitaluck.js
└── truffle-config.js
```
The structure of the `Vitaluck_3b400b.dir` sample directory follows the standard structure for Truffle tests. The directory `contracts` contains the Solidity code of the migration contract and the contract to be tested. The `migrations` directory contains the initial migration script. The `test` directory contains support code and the test script generated from the first 50 historic transactions of th contract. This test can be used as a regression test for modified versions of the contracts. The two `*.log` files and the file `replay.js` are the output of running `make.sh`. The file `replay.js` is a JavaScript program, that when run reports on the success or failure of replaying each of the first 50 transactions of the contract. This is intended only as an illustration of the possibilities. The analysis can easily be extended. See the example below for a sample output of running `make.sh` for the Vitaluck contract

## make.log

```
$ bash -x make.sh
+ Pid=98557
+ ganache-cli -p 9545 -a 1000 -e 1000000 -d -l 10000000 -t 2018-01-26T13:29:19.000Z
+ sleep 10
+ truffle test
Compiling ./contracts/Migrations.sol...
Compiling ./contracts/Vitaluck.sol...

  Contract: Vitaluck
    ✓ TEST: Vitaluck(  ) (1092ms)
    ✓ TEST: constantFunction 0 (217ms)
    ✓ TEST: Play(  ) (1048ms)
    ✓ TEST: constantFunction 1 (193ms)
    ✓ TEST: Play(  ) (1047ms)
    ✓ TEST: constantFunction 2 (210ms)
    ✓ TEST: Play(  ) (1046ms)
    ✓ TEST: constantFunction 3 (187ms)
    ✓ TEST: Play(  ) (1040ms)
    ✓ TEST: constantFunction 4 (163ms)
    ✓ TEST: Play(  ) (1039ms)
    ✓ TEST: constantFunction 5 (177ms)
    ✓ TEST: Play(  ) (1037ms)
    ✓ TEST: constantFunction 6 (167ms)
    ✓ TEST: Play(  ) (1036ms)
    ✓ TEST: constantFunction 7 (205ms)
    ✓ TEST: Play(  ) (1032ms)
    ✓ TEST: constantFunction 8 (196ms)
    ✓ TEST: Play(  ) (1053ms)
    ✓ TEST: constantFunction 9 (191ms)
    ✓ TEST: Play(  ) (1031ms)
    ✓ TEST: constantFunction 10 (292ms)
    ✓ TEST: Play(  ) (1036ms)
    ✓ TEST: constantFunction 11 (213ms)
    ✓ TEST: Play(  ) (1048ms)
    ✓ TEST: constantFunction 12 (220ms)
    ✓ TEST: Play(  ) (1039ms)
    ✓ TEST: constantFunction 13 (193ms)
    ✓ TEST: Play(  ) (1039ms)
    ✓ TEST: constantFunction 14 (195ms)
    ✓ TEST: Play(  ) (1070ms)
    ✓ TEST: constantFunction 15 (232ms)
    ✓ TEST: Play(  ) (1029ms)
    ✓ TEST: constantFunction 16 (240ms)
    ✓ TEST: Play(  ) (1034ms)
    ✓ TEST: constantFunction 17 (250ms)
    ✓ TEST: Play(  ) (1034ms)
    ✓ TEST: constantFunction 18 (355ms)
    ✓ TEST: Play(  ) (1052ms)
    ✓ TEST: constantFunction 19 (262ms)
    ✓ TEST: Play(  ) (1038ms)
    ✓ TEST: constantFunction 20 (250ms)
    ✓ TEST: Play(  ) (1039ms)
    ✓ TEST: constantFunction 21 (346ms)
    ✓ TEST: Play(  ) (1042ms)
    ✓ TEST: constantFunction 22 (271ms)
    ✓ TEST: Play(  ) (1073ms)
    ✓ TEST: constantFunction 23 (265ms)
    ✓ TEST: Play(  ) (1034ms)
    ✓ TEST: constantFunction 24 (246ms)
    ✓ TEST: Play(  ) (1045ms)
    ✓ TEST: constantFunction 25 (295ms)
    ✓ TEST: Play(  ) (1052ms)
    ✓ TEST: constantFunction 26 (232ms)
    ✓ TEST: check all blocks (284ms)
    ✓ analysis

  56 passing (35s)

+ kill 98557
+ node replay.js
Vitaluck 0xEf7C7254c290DF3d167182356255CDfd8D3b400b
Vitaluck tx 0 success: 1410422 gas used
Vitaluck tx 1 success: 62347 gas used
Vitaluck tx 2 success: 278797 gas used
Vitaluck tx 3 success: 173797 gas used
Vitaluck tx 4 success: 173797 gas used
Vitaluck tx 5 success: 184077 gas used
Vitaluck tx 6 success: 173797 gas used
Vitaluck tx 7 success: 173797 gas used
Vitaluck tx 8 success: 173797 gas used
Vitaluck tx 9 success: 153268 gas used
Vitaluck tx 10 success: 138268 gas used
Vitaluck tx 11 success: 173797 gas used
Vitaluck tx 12 success: 138268 gas used
Vitaluck tx 13 success: 138268 gas used
Vitaluck tx 14 success: 138268 gas used
Vitaluck tx 15 success: 153268 gas used
Vitaluck tx 16 success: 153268 gas used
Vitaluck tx 17 success: 138268 gas used
Vitaluck tx 18 success: 138268 gas used
Vitaluck tx 19 success: 138268 gas used
Vitaluck tx 20 success: 138268 gas used
Vitaluck tx 21 success: 138268 gas used
Vitaluck tx 22 success: 138268 gas used
Vitaluck tx 23 success: 153268 gas used
Vitaluck tx 24 success: 153268 gas used
Vitaluck tx 25 success: 153268 gas used
Vitaluck tx 26 success: 153268 gas used
make.sh: line 6: 98557 Terminated ganache-cli -p 9545 -a 1000 -e 1000000 -d -l 10000000 -t "2018-01-26T13:29:19.000Z" > ganache.log
```

## Zip files

There are 26 zipped directories in this repository called `A.dir.zip` ... `Z.dir.zip`. Each contains the contracts with a name beginning with the given letter of the alphabet.
