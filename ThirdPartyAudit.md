This document contains confidential information about smart contracts and intellectual properties of **Databroker**, as well as reports about potential vulnerabilities and methods of their exploitation.   
This confidential data is for internal use by **Databroker** only and shall not be disclosed to third parties.   

<table>
  <tr>
    <td>Name
    </td>
    <td>DTX Staking Third Party Audit
    </td>
  </tr>
  <tr>
    <td>Date
    </td>
    <td>08/24/2021
    </td>
  </tr>
  <tr>
    <td>Audited By
    </td>
    <td>Francis Isberto - Smart Contract Auditor
    </td>
  </tr>
  <table>

## Table of Contents
    
- [x] [Reviewer Introduction](#ReviewerIntroduction)
- [x] [Scope](#Scope)
- [x] [Executive Summary](#ExecutiveSummary)
- [x] [Code Overview](#CodeOverview)
- [x] [Severity Levels and Explanation](#SeverityLevelsAndExplanation)
- [x] [Audit Overview](#AuditOverview)
- [x] [Recommendations](#Recommendations)
- [x] [Conclusion](#Conclusion)
- [x] [Disclaimers](#Disclaimers)
- [x] [Appendix A. Staking Logic](#AppendixA)
- [x] [Appendix B. Automated Tools Reports](#AppendixB)
    
<a name="ReviewerIntroduction"></a>
## Reviewer Introduction
DataBroker needs a third party audit before it's deployed to the ethereum mainnet.  
The sole purpose of building **"DTX-staking"** is exclusively for smart contract audit only. The said repo will be deleted once an audit has been accomplished.
 
<a name="Scope"></a>
## Scope
The scope of the project is to do an audit on contracts/Staking.sol
which can be found on the link below:  
https://github.com/databrokerglobal/DTX-staking/blob/main/Contracts/Staking.sol  

I have scanned Staking.sol for commonly known and more specific vulnerabilities.  
Here are some of my recommendations that can, may, or had been considered (the full list includes but is not limited to):
* ReentrancyGuard.initialize() is recommended for adding in OpenZeppelin SDK. This contract module will help prevent reentrant calls to a function.  
Inheriting from `ReentrancyGuard` will make the {nonReentrant} modifier available, which can be applied to functions to make sure there are no nested (reentrant) calls to them.  
Check OpenZeppelin's past blog for further reference…  https://blog.openzeppelin.com/reentrancy-after-istanbul/
* It is common practice to utilize **“safeMath”** lib to avoid “Underflow/Overflow” in code.  
Let it be known that the contract being reviewed has the updated version in **pragma solidity 0.8.6** where the compiler has automatically taken care of checking for overflows and underflows.  
* No **SELFDESTRUCT** vulnerabilities found. There is no improper access control nor any sign of delegation detected in the contract.
 
<a name="ExecutiveSummary"></a>
## Executive Summary 
This is a full Code Review and Security Analysis Report.  

All issues were performed meticulously, which included the analysis of code functionality, manual audits found during automated analysis were manually reviewed and applicable vulnerabilities are presented in this report.  
The general overview is presented in the **“Code Overview”**.  
    
I found 0 critical, 0 high, 0 medium, and 0 low level issues.
 
<a name="CodeOverview"></a>
## Code Overview

#### File: Staking.sol  
#### Import: ERC20/IERC20, EnumerableSet, AccessControlUpgradeable, PausableUpgradeable, Initializable, UUPSUpgradeable  
#### Observation: Passed  
#### Test Report: Passed  
#### Score: Passed  
#### Conclusion: Passed

<table>
  <tr>
    <td>
      Function
    </td>
    <td>
      Type
    </td>
    <td>
      Observation
    </td>
    <td>
      Test Report
    </td>
    <td>
      Conclusion
    </td>
    <td>
      Score
    </td>
  </tr>
    <tr>                                   
    <td>
      Initialize
    </td>
    <td>
      write
    </td>
    <td>
      passed
    </td>
    <td>
      All Passed
    </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
    <tr>
    <td>
      authorizeUpgrade
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
    <tr>
    <td>
      pauseContract
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      setInitialRatio
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      createStake
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      removeStake
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      getDtxPerShare
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      stakeOf
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      sharesOf
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      rewardOf
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      getTotalStakes
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      getCurrentRewards
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
  <tr>
    <td>
      getTotalStakeholders
    </td>
    <td>
      write
    </td>
    <td>
      Passed
    </td>
    <td>
       All Passed
      </td>
    <td>
      No Issue
    </td>
    <td>
      Passed
    </td>
  </tr>
    </table>
   
 
<a name="SeverityLevelsAndExplanation"></a>
## Severity Levels and Explanation
    
<table>
  <tr>
    <td>Risk Level</td>
    <td>Description</td>
  </tr>
  <tr>
    <td>Critical</td>
    <td>Critical vulnerabilities are severe as they are easy to exploit and can result in loss of tokens, rug pulls, etc.</td>
  </tr>
  <tr>
    <td>High</td>
    <td>High level vulnerabilities are hard to exploit but can have an impact on smart contract execution, e.g. open access to an important function</td>
    </tr>
    <tr>
      <td>Medium</td>
      <td>Medium level vulnerabilities are important to fix but can't lead to loss of tokens</td>
    </tr>
  <tr>
    <td>Low</td>
    <td>Low-level vulnerabilities are mostly outdated code, unused code related. They have very low to no impact on smart contract execution</td>
  </tr>
  <tr>
    <td>Lowest/Code/Style/Info</td>
    <td>Lowest level of vulnerabilities, code style violations and info statement can't affect smart contract execution and can be ignored</td>
  </tr>
    </table>


<a name="AuditOverview"></a>
## Audit Overview   
   
#### Critical  
No critical severity vulnerabilities were identified

#### High  
No high severity vulnerabilities were identified

#### Medium  
No medium severity vulnerabilities were identified

#### Low  
No low severity vulnerabilities were identified. 

#### Lowest / Code style / Info  
No code style issues were identified.

<a name="Recommendations"></a>
## Recommendations
    
Recommendation for Gas Consumption Reduction

According to data from Glassnode, the average price of gas paid per transaction on the Ethereum network has risen roughly 16.5 times over a year from 10.6 in March 3, 2020, to around 175 today.
    
One course of action is through [Biconomy](https://www.biconomy.io/) and [Arbritrum](https://arbitrum.io/).  
As Arbitrum offers low gas costs, DApps can connect with Biconomy’s plug-and-play application programming interfaces to sponsor these gas fees for users.  
People seeking a way out of paying high gas costs will in no time crowd the faster and gasless experience on Arbitrum.  
Users can also enable their users to pay their new low gas fee in ERC20 stablecoins.

<a name="Conclusion"></a>
## Conclusion    

During the audit the contract was manually reviewed, I found no security issues that required fixing.

And given a contract file, I have used all possible tests based on the given object.  
The contract is written systematically, so therefore it is ready to go for production. 
    
Since possible test cases can be unlimited and developer level documentation (code flow diagram with function level description) not provided, for such an extensive smart contract protocol, I provide no such guarantee of future outcomes. 
    
I have used all the latest static tools and manual observations to cover maximum possible test cases to scan everything. 
    
The security state of the reviewed contract is now **“well secured”**.
    
<a name="Disclaimers"></a>
## Disclaimers    

The audit does not give any warranties on the security of the code. A single audit may not be enough, I highly encourage several independent audits and public bug bounties to ensure optimum security of the smart contracts.
 
<a name="AppendixA"></a>
## Appendix A. Evidence

Staking Logic explained  
https://docs.google.com/spreadsheets/d/1am9ZI1WfkjeKPh4CRhzKWh4AzEfh9_kkGZwuhVdOoPM/edit#gid=0
 
<a name="AppendixB"></a>
## Appendix B. Automated tools reports
None
