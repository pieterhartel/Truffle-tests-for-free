# Truffle-tests-for-free
Verified smart contracts with truffle tests generated from the first 50 historic transactions on the blockchain

## Summary

This repository contains the source code of 1111 verified smart contracts that were downloaded on 1 Jan 2019 from etherscan.io. The file `scrapedcontractsVerified.json` contains the name, address and other relevant data of all verified smart contracts present on 1 Jan 2019 on https://etherscan.io/contractsVerified

There are 26 directories `A.dir` ... `Z.dir`, each of which contains contracts with a name beginning with the given letter of the alphabet.

For each contract there is a directory with the files needed by the `truffle test` command. The test script in the `test` directory has been generated from the first up to 50 historic transactions on the block chain as described by a paper currently under review.

A test can be run by executing the file `make.sh` in the directory of the contract. the shell script fires up `ganache-cli` with the parameters needed for the test, compiles, and deploys the contract, runs the test and finally analyses the output of the test. The analysis shows the amount of gas used by each transacton. This is intended only as an illustration of the possibilities. The analysis can easily be extended. See the example below for a sample output of running `make.sh` for the Vitaluck contract.

## Prerequisites

```
$ truffle version
Truffle v5.0.2 (core: 5.0.2)
Solidity - 0.4.19 (solc-js)
Node v10.15.0
$ ganache-cli -v
Ganache CLI v6.2.5 (ganache-core: 2.3.3)
```

## Example of use

```
$ cd V.dir/Vitaluck_3b400b.dir/
$ sh make.sh 
Compiling ./contracts/Migrations.sol...
Compiling ./contracts/Vitaluck.sol...


  Contract: Vitaluck
    ✓ TEST: Vitaluck (40ms)
    ✓ TEST: constantFunction 0 (209ms)
    ✓ TEST: Play(  ) (89ms)
    ✓ TEST: constantFunction 1 (177ms)
    ✓ TEST: Play(  ) (162ms)
    ✓ TEST: constantFunction 2 (158ms)
    ✓ TEST: Play(  ) (139ms)
    ✓ TEST: constantFunction 3 (170ms)
    ✓ TEST: Play(  ) (139ms)
    ✓ TEST: constantFunction 4 (160ms)
    ✓ TEST: Play(  ) (133ms)
    ✓ TEST: constantFunction 5 (189ms)
    ✓ TEST: Play(  ) (164ms)
    ✓ TEST: constantFunction 6 (160ms)
    ✓ TEST: Play(  ) (132ms)
    ✓ TEST: constantFunction 7 (164ms)
    ✓ TEST: Play(  ) (124ms)
    ✓ TEST: constantFunction 8 (160ms)
    ✓ TEST: Play(  ) (117ms)
    ✓ TEST: constantFunction 9 (161ms)
    ✓ TEST: Play(  ) (118ms)
    ✓ TEST: constantFunction 10 (159ms)
    ✓ TEST: Play(  ) (124ms)
    ✓ TEST: constantFunction 11 (155ms)
    ✓ TEST: Play(  ) (125ms)
    ✓ TEST: constantFunction 12 (164ms)
    ✓ TEST: Play(  ) (124ms)
    ✓ TEST: constantFunction 13 (170ms)
    ✓ TEST: Play(  ) (115ms)
    ✓ TEST: constantFunction 14 (167ms)
    ✓ TEST: Play(  ) (121ms)
    ✓ TEST: constantFunction 15 (166ms)
    ✓ TEST: Play(  ) (126ms)
    ✓ TEST: constantFunction 16 (177ms)
    ✓ TEST: Play(  ) (117ms)
    ✓ TEST: constantFunction 17 (180ms)
    ✓ TEST: Play(  ) (116ms)
    ✓ TEST: constantFunction 18 (186ms)
    ✓ TEST: Play(  ) (119ms)
    ✓ TEST: constantFunction 19 (186ms)
    ✓ TEST: Play(  ) (111ms)
    ✓ TEST: constantFunction 20 (176ms)
    ✓ TEST: Play(  ) (113ms)
    ✓ TEST: constantFunction 21 (184ms)
    ✓ TEST: Play(  ) (113ms)
    ✓ TEST: constantFunction 22 (188ms)
    ✓ TEST: Play(  ) (113ms)
    ✓ TEST: constantFunction 23 (194ms)
    ✓ TEST: Play(  ) (114ms)
    ✓ TEST: constantFunction 24 (183ms)
    ✓ TEST: Play(  ) (117ms)
    ✓ TEST: constantFunction 25 (190ms)
    ✓ TEST: Play(  ) (110ms)
    ✓ TEST: constantFunction 26 (192ms)
    ✓ analysis


  55 passing (8s)

Vitaluck 0xEf7C7254c290DF3d167182356255CDfd8D3b400b
0 1410422
1 62347
2 278797
3 173797
4 173797
5 184077
6 173797
7 173797
8 173797
9 153268
10 138268
11 184077
12 173797
13 173797
14 138268
15 188797
16 188797
17 138268
18 138268
19 138268
20 138268
21 138268
22 173797
23 153268
24 153268
25 188797
26 153268
make.sh: line 6: 23409 Terminated: 15          ganache-cli -a 1000 -e 1000000 -d -l 10000000 -t "2018-01-26T13:29:19.000Z" > ganache.log
```
