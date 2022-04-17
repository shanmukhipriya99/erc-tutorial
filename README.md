# Erc20-tutorial
A tutorial for working with ERC-20 tokens.

### Fungible Tokens
Fungible tokens or assets are divisible and non-unique. For instance, fiat currencies like the dollar are fungible: A $1 bill in New York City has the same value as a $1 bill in Miami. A fungible token can also be a cryptocurrency like Bitcoin: 1 BTC is worth 1 BTC, no matter where it is issued. 

### What is ERC-20?
* An ERC20 token is a standard used for creating and issuing smart contracts on the Ethereum blockchain. 
* Smart contracts can then be used to create smart property or tokenized assets that people can invest in.
* ERC stands for "Ethereum request for comment," and the ERC20 standard was implemented in 2015.

The contract contains some pre-defined variables, functions and events. Most of them need not be changed but we can modify a few details like the name, symbol, decimals, etc.

A few frequently used functions are: 
* TotalSupply: provides information about the total token supply

```function totalSupply() public view returns (uint256);```
* BalanceOf: provides account balance of the owner's account

```function balanceOf(address tokenOwner) public view returns (uint);```
* Transfer: executes transfers of a specified number of tokens to a specified address

```function transfer(address to, uint tokens) public returns (bool);```
* TransferFrom: executes transfers of a specified number of tokens from a specified address

```function transferFrom(address from, address to, uint tokens) public returns (bool);```
* Approve: allow a spender to withdraw a set number of tokens from a specified account

```function approve(address spender, uint tokens) public returns (bool);```
* Allowance: returns a set number of tokens from a spender to the owner

```function allowance(address tokenOwner, address spender) public view returns (uint);```

There are a few other functions that are self-explanatory.
The two events are:
* Transfer: Emitted when `value` tokens are moved from one account (`from`) to another (`to`)

```event Transfer(address indexed from, address indexed to, uint256 value);```
* Approval: Emitted when the allowance of a `spender` for an `owner` is set by a call to {approve}. `value` is the new allowance.

```event Approval(address indexed owner, address indexed spender, uint256 value);```

### How to work with it?
OpenZeppelin is a good place to import the code from. This is the [link](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/IERC20.sol) to the interface of the ERC20 token. This interface contains the functions and events that were discussed in the previous section. This is the [link](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol) to the actual ERC20 smart contract. This is where the above discussed functions are defined and the events are emitted.

We can import them into our smart contract by:
```import "@openzeppelin/contracts/token/ERC20/ERC20.sol";```

We can then inherit the functions in our smart contract by:
```
contract MyContract is ERC20 {
    constructor(uint256 totalSupply) public ERC20("MyToken", "MYT") {        //token name: MyToken, token symbol: MYT
        _balances[msg.sender] = totalSupply;
    }
    
    //your functions here
}
```

Another way to use the above functions and events is in the Example.sol file.
