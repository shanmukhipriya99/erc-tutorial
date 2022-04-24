# Erc721-tutorial
A tutorial for working with ERC-721 tokens.

### Non-Fungible Tokens
Non-Fungible tokens are indivisible and unique. Each and every one of these tokens is distinct in its own way. NFTs can include collecting cards, artworks, plane tickets, and other items. One can tell them apart from the other, but they are not interchangeable. For those unfamiliar with NFTs, think of them as uncommon collectibles. Each one has its own unique traits, as well as its unique attributes, and in most cases, it's metadata. 

### What is ERC-721?
* ERC stands for "Ethereum Request for Comment", and 721 is the proposal identifier number.
* ERC-721 was made to propose the ability to track and move NFTs in smart contracts.
* ERC-721 is an open standard that explains how to make Non-Fungible tokens on EVM-compatible blockchains. It is a standard interface for Non-Fungible tokens, and it has a set of rules that make it easy to work with NFTs.

The contract contains some pre-defined variables, functions and events, similar to the ERC-20 contract. Most of them need not be changed but we can modify a few details like the name, symbol, etc.

A few frequently used functions are: 
* Name: Used to give the token a name that other contracts and apps can use to find it.

```function name() constant returns (string name);```
* Symbol: Used to define token’s shorthand name or symbol.

```function symbol() constant returns (string symbol);```
* TotalSupply: This function is used to determine out how many tokens there are on the blockchain. The supply doesn't have to stay the same.

```function totalSupply() constant returns (uint256 totalSupply);```
* BalanceOf: Returns number of NFTs owned by an address.

```function balanceOf(address _owner) constant returns (uint balance);```

Following are a few functions w.r.t ownership:
* OwnerOf: This function returns the owner of a token's address. Because each ERC-721 token is one-of-a-kind and non-fungible, an ID is used to represent it on the blockchain. This ID can be used by other users, contracts, and apps to determine who owns the token.

```function ownerOf(uint256 _tokenId) constant returns (address owner);```
* Transfer: It enables the token's owner to transfer it to another user.

```function transfer(address _to, uint256 _tokenId);```
* TakeOwnernship: This works as a withdrawal function because it can be used by an outside entity to withdraw tokens from another user's account. As a result, when a user has been approved to own a particular quantity of tokens and desires to withdraw those tokens from another user's balance, takeOwnership can be employed. (Optional)

```function takeOwnership(uint256 _tokenId);```
* Approve: This function grants or approves another entity the permission to transfer tokens on the owner’s behalf.

```function approve(address _to, uint256 _tokenId);```
* Allowance: returns a set number of tokens from a spender to the owner

```function allowance(address tokenOwner, address spender) public view returns (uint);```
* TokenOfOwnerByIndex: Each owner may own multiple NFTs concurrently. Each NFT is identified by a unique ID, and it can become difficult to keep track of IDs over time. As a result, the contract keeps these IDs in an array, and the tokenOfOwnerByIndex function allows us to obtain them. (Optional)

```function tokenOfOwnerByIndex(address _owner, uint256 _index) constant returns (uint tokenId);```

Metadata Function:
* TokenMetadata: This is an interface that allows discovering a token’s metadata or a link to its data.

```function tokenMetadata(uint256 _tokenId) constant returns (string infoUrl);```
The two events are:
* Transfer: This event is triggered when ownership of the token is transferred from one person to another. It emits information on the account that transferred the token, the account that got the token, and the token that was transferred (by ID).

```event Transfer(address indexed _from, address indexed _to, uint256 _tokenId);```
* Approval: This event is triggered anytime a user grants another user permission to acquire ownership of the token, i.e., whenever the approve function is run. It emits information on which account now owns the token, which account has been granted permission to acquire ownership of the token in the future, and which token (by ID) has been granted permission to have its ownership transferred.

```event Approval(address indexed _owner, address indexed _approved, uint256 _tokenId);```

### How to work with it?
OpenZeppelin is a good place to import the code from. This is the [link](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/IERC721.sol) to the interface of the ERC721 token. This interface contains the functions and events that were discussed in the previous section. This is the [link](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol) to the actual ERC721 smart contract. This is where the above discussed functions are defined and the events are emitted.

We can import them into our smart contract by:
```import "@openzeppelin/contracts/token/ERC721/ERC721.sol";```

We can then inherit the functions in our smart contract by:
```
contract MyContract is ERC721 {
    constructor() ERC721("MyNFT", "MNFT") {}              //token name: MyNFT, token symbol: MNFT    
    //your functions here
}
```

A more detailed tutorial is available in the tutorial.md file.

### References
* https://www.quicknode.com/guides/solidity/how-to-create-and-deploy-an-erc-721-nft
* https://ethereum.org/ca/developers/tutorials/how-to-write-and-deploy-an-nft/#connect-to-ethereum
* https://docs.opensea.io/docs/1-structuring-your-smart-contract
* https://medium.com/crypto-currently/the-anatomy-of-erc721-e9db77abfc24
