# OMA3 NFT Royalties Request for Proposals (RFP)
# OMA3 NFT Working Group (NFTWG)

## Introduction

This Request for Proposals (RFP) is released by OMA3’s NFT Working Group (NFTWG). The purpose of this RFP is to solicit implementation proposals for OMA3’s NFT Royalties system (“NFTR”).  It is also a call for non-members with existing products in this area to join OMA3, get your technology adopted by the industry, and help ensure NFT royalties are honored.

## Purpose

The purpose of this Request for Proposals (RFP) is to outline NFTR requirements and criteria and solicit NFTR solutions that can be used to implement NFTR. These solutions may come from the diverse OMA3 community of Creators, Participants and Sponsors, or outside of the OMA3 membership community. Solutions can be already developed or just a high level concept.

## Scope

OMA3 intends to create standards and infrastructure for ensuring royalties and commissions get paid on secondary sales of NFTs. OMA3 aims to ratify solutions that are cross-chain and virtual machine agnostic.  Given this broad mandate, the scope of this RFP is wide.

This RFP starts with descriptions of high-level “use cases” the NFTR could address. The RFP then outlines high-level threats for circumventing an NFTR solution.  The RFP finally details a comprehensive range of functional and non-functional requirements that NFTR solutions need to fulfill. 

Note- OMA3 is not expressing an opinion on whether the assets referred to in this document should be considered securities.

## Use Cases

This section focuses on the use cases for the NFTR “System”. The System is a generic term that encompasses all possible solutions for implementing creator royalties, including smart contracts and legal frameworks.

### Actors

Actors describe anything outside the System that interacts with the System:

  * Creator: Entity that originates the NFT, responsible for its initial creation and minting.
  * Secondary Creators/Collaborators: Entities involved in the NFT's creation process or holding contractual rights, such as publishers, distributors, or collection societies.
  * Wallets: Digital wallets facilitating NFT transactions.
  * NFT: A digital asset governed by an NFT Contract.
  * NFT Contract: Various types of governing smart contracts for NFTs, including those that are immutable, upgradeable, and those representing real-world assets.
      * Primary Contract: The NFT contract that minted the NFT.
      * Wrapper Contract:  An NFT contract that encapsulates a Primary Contract NFT.
  * Blockchain Network: The foundational technology for hosting smart contracts that enable NFT minting, trading, and royalty distribution.
  * Holders: Entities that own NFTs.
      * Seller: current NFT owners
      * Buyer: NFT purchasers that can be collectors, liquidity providers, etc.
          * Lender: Individual investors, institutions, or protocols offering loans against NFT collateral.
          * Renter:  A party interested in acquiring temporary access to the NFT. 
  * Marketplace: Digital platforms for the listing and trading of NFTs, inclusive of curators and online galleries, that facilitate one or more of the following transactions using a combination of on-chain and off-chain infrastructure:
      * NFT Sales, including using FIAT, crypto, and loyalty points for purchases.
      * Renting
      * Fractionalization:  splitting an NFT into shares that can be sold to Buyers.
  * Escrow:  service that holds assets, and then distributes the assets in accordance with a contractual agreement.  Marketplaces may have their own Escrow.

### Base Sales Use Case

  1. The NFT is listed in a Marketplace by Seller.
  2. A Buyer identifies NFT on the Marketplace and decides to purchase it using a price discovery mechanism (e.g.- fixed price, auction, etc.).
  3. The purchase transaction is executed by the Marketplace, including recording the sale in a smart contract and triggering a closing process that distributes value.
  4. As part of the closing process the Marketplace, NFT Contract, and System together initiate the distribution of royalties, as specified in the NFT Contract, to the Creator and any Secondary Creators/Collaborators involved.
  5. All parties (Creator, Secondary Creators, Buyer) receive confirmation of the transaction and any royalty distribution.

     High Frequency Trading adaptation of the Base Use Case:  Numerous sales transactions on an NFT in a short period of time, sometimes within the same block (“flash trading”).

### Loan Default Use Case

  1. Holder applies for a loan on a Marketplace, listing their NFT as collateral.
  2. Potential Lender offers loan terms based on a Marketplace appraisal, or its own appraisal.
  3. Holder accepts the loan.
  4. Marketplace initiates execution of the loan.
  5. NFT is transferred to an Escrow (possibly managed by the Marketplace), and the loan amount is released to the Holder.
  6. Holder makes payment(s) to the Lender.
  7. Holder defaults on the loan. 
  8. In accordance with the NFT Contract, Marketplace and System initiate the default process specified by the NFT Contract, including payment of royalties to the Creator.

     Note:  This does not cover the use case where royalties are distributed on loan payments.

### Rental Use Case

  1. Holder lists NFT on Marketplace making it available for rent, including rental terms.
  2. Renter Discovery: The Renter searches the marketplace and identifies the NFT they wish to rent.
  3. Agreement Acceptance: The Renter agrees to the terms of the rental, which include the rental period and fee.
  4. Rent Execution: The Marketplace and Rental Contract processes the rental agreement, ensuring the Renter pays the rental fee.
  5. Royalties:  Marketplace and System ensure rental royalties are paid in accordance with the NFT Contract or Marketplace infrastructure.
  6. NFT Utilization: The Renter gains access to the benefits associated with the NFT (e.g., using a virtual item in a game or displaying digital art), without direct control over the original NFT, according to the NFT Contract, Marketplace infrastructure, and/or System.
  7. End of Rental Period: Upon conclusion of the rental period, the Marketplace ends the rental agreement. The original NFT remains with the Holder, and the Renter's access rights are revoked.

     Alternative Flow
  * Extension Request: If the Renter wishes to extend the rental period, they must request an extension through the Marketplace before the current rental period expires. The Holder can review and accept or decline the extension under the same or revised terms.
  * Early Termination: The Renter or Holder may terminate the rental agreement early under specific conditions outlined in the smart contract. An early termination by the Renter may not result in a refund of the rental fee.

### Wrapping Use Case

  1. Seller takes possession of a Primary NFT.
  2. Seller takes ownership of a Secondary NFT using the Secondary NFT Contract and possibly the System.
  3. The Seller initiates the transfer of the Primary NFT to the Secondary NFT using the Primary NFT Contract.
  4. The NFT contract verifies ownership and executes the wrapping of the Primary NFT with the Secondary NFT.
  5. Seller may transfer other NFTs (Primary or Secondary) to the Secondary NFT using the same method.
  6. The Secondary NFT, now encapsulating the Primary NFT(s), is listed for sale on a Marketplace.
  7. Buyer purchases the Secondary NFT, acquiring the rights and assets to all NFTs owned by the Secondary NFT.
  8. Ownership of the Secondary NFT, along with the encapsulated Primary NFT, is transferred to the Buyer.
  9. Marketplace and System distribute royalties from the NFTs owned by the Secondary NFT to Creator.

     Alternate Flow: If the transfer or verification fails, the transaction is canceled, and the NFTs remain with Seller.

### Fractionalization Use Case

  1. The Holder decides to fractionalize the NFT into multiple shares.
  2. Holder uses Fractionalization Contract and System to create shares for the NFT.
  3. Shares are listed on a Marketplace with defined terms for sale.
  4. Buyers purchase shares, and transactions are recorded on the Blockchain.
  5. Ownership rights and benefits are distributed among shareholders according to the NFT and/or Fractionalization Contract.
  6. System and Fractionalization Contract distribute royalties from the share sale to Creator and Secondary Creators.

### Swapping Use Case

  1. Initiation: A Holder initiates the swap by listing an NFT for exchange on a Marketplace, specifying value or desired types or specific NFTs for swapping.
  2. Discovery and Agreement: Another Holder discovers the listing and agrees to the swap terms, either through direct negotiation or via automated match-making facilitated by smart contracts on the Marketplace.
  3. Smart Contract Execution: Upon agreement, a Marketplace smart contract is initiated, encapsulating the terms of the swap. This contract ensures that the exchange is executed only if both parties meet the agreed conditions.
  4. Validation and Swap: The Marketplace validates the ownership of the NFTs, temporarily locks them to prevent other transactions, and executes the swap through the smart contract.
  5. Confirmation and Transfer: Upon successful validation, the NFTs are transferred between the Holders’ Wallets. The Blockchain records the transaction.
  6. Royalties:  Marketplace and System distribute royalties to Creator(s).
  7. Post-Exchange: Each Holder now owns the NFT initially held by the other party. They can verify the transfer through their wallet and the transaction history on the Blockchain.

     Alternative Flow:
  * Failed Validation: If the Platform detects issues with the NFTs (e.g., one party attempting to swap someone else’s NFT), the smart contract halts the swap, and the assets remain with their original owners.
  * Cancellation: Either party may cancel the swap before the smart contract execution if the Marketplace allows. Cancellation after contract initiation may require mutual agreement or result in penalties as defined by the contract.

### Loyalty Use Case

  1. NFTs compatible with loyalty programs are minted by Creator using System.  
  2. Earning loyalty points: Engaging in qualifying activities (like purchases), Buyers earn loyalty points in Marketplace infrastructure or smart contracts.
  3. Reward Catalog Access: Buyer accesses a Retailer catalog detailing available NFTs and their respective redemption values.
  4. Purchase:  Buyer purchases NFT with loyalty points.
  5. Transaction:  Retailer reduces Buyer point balance, sends NFT to Buyer Wallet, and disburses royalties to Creator(s) using System.

## Threats

For a background on the section, read Section 4 of the [OMA3 Working Group Process](https://docs.google.com/document/d/1vwR6ST2FoOzjKct06I5m6F3EZW1h2cQrSfB31kPQV0Y/).  The following is a list of mechanisms that can be used to circumvent NFT royalties.

  1. Peer-to-peer NFT sales:  Current Owner transfers NFT to a Buyer directly and sale proceeds happen offchain, potentially also facilitated by a discovery platform (e.g.- Craigslist).
  2. NFT Loans:  Current Owner takes out a loan and uses the NFT as collateral.  Some loans have encumbrances.
  3. NFT Fractionalization:  Current Owner sells a stake in the NFT instead of the whole NFT.
  4. NFT Wrapping:  Current Owner transfers NFT to an account owned by another NFT (NFT wrapping) that is not subject to royalty payments, and the latter NFT is sold
  5. NFT Bundling:  Current Owner bundles an NFT with other NFTs into an account owned by another NFT that is not subject to royalties, and the latter NFT is sold.
  6. Marketplace Apathy:  marketplace smart contracts do not enforce the royalty payment when closing NFT sales.
  7. Chain Transfer:  moving an NFT to a different chain to circumvent royalties.

## Requirements

This section lists the high-level requirements derived from the use cases and threats.

Terminology definitions can be found in Section 5 of the [OMA3 Working Group Process document](https://docs.google.com/document/d/1vwR6ST2FoOzjKct06I5m6F3EZW1h2cQrSfB31kPQV0Y/). 

Companies in the NFT industry, both OMA3 members and non-members, are encouraged to submit proposals that address any of the above use cases and adhere to the following requirements. OMA3 utilizes a [point system](https://github.com/oma3dao/token-litepaper) to help compensate OMA3 members for the contributing time and technology to OMA3.  Points are used to calculate allocation of OMA3 fungible tokens.

1. Use cases
 1.1. SHALL address the base sales use case
 1.2. SHALL address the high frequency trading use case in a manner that is fair to both Creators and Holders
    1.3 SHOULD address the NFT bundling use case
    1.4 MAY address the NFT loan default use case
    1.5 MAY address the NFT fractionalization use case
    1.6 MAY address the NFT renting use case
    1.7 MAY address the NFT swapping use case
    1.8 MAY address the NFT loyalty point use case
    1.9 MAY differentiate between internal and peer to peer wallet transfers
    1.10 SHALL encompass royalty splitting use cases
    1.11 MAY introduce a reputation point system
2. NFT contract types
    2.1 SHALL apply to new NFT contracts
    2.2 SHALL apply to upgradeable existing NFT contracts
    2.3 SHOULD apply to non-upgradeable existing NFT contracts
3. Compatibility
    3.1 MAY work with NFTs bridged to other chains
    3.2 SHALL be consistent with the base ERC-721 standard
    3.3 SHALL honor the underlying legal framework of the NFTs in question
      3.3.1 SHALL take into account legal systems of different jurisdictions
    3.4 SHALL support all EVM chains
    3.5 SHALL support the Solana Metaplex standard
    3.6 SHOULD support the Solana 404 standard
    3.7 MAY support Bitcoin NFT standards that include royalties
4. Governance
    4.1 SHALL have the same level of or more decentralization than OMA3 governance
    4.2 MAY have governance controlled by OMA3
5. Privacy
    5.1 MAY protect user privacy
    5.2 MAY allow users to control data associated with them
6. Cybersecurity
    6.1 SHOULD use “battle tested” code wherever possible
    6.2 SHALL undergo audits and penetration tests
    6.3 SHALL support multisig access control
    6.4 SHALL utilize information security management system (ISMS) software life cycle (SLC) when appropriate
