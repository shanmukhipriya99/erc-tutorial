Please open images in a new tab for more clarity! 
### Step-1
Following is the code I deployed in the remix IDE:

```//Contract based on [https://docs.openzeppelin.com/contracts/3.x/erc721](https://docs.openzeppelin.com/contracts/3.x/erc721)
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/utils/Counters.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";

contract MyNFT is ERC721URIStorage {
    using Counters for Counters.Counter;
    Counters.Counter public _tokenIds;

    constructor() ERC721("MyNFT", "MNFT") {}

    function mintNFT(address recipient, string memory tokenURI)
        public 
        returns (uint256)
    {
        _tokenIds.increment();

        uint256 newItemId = _tokenIds.current();
        _mint(recipient, newItemId);
        _setTokenURI(newItemId, tokenURI);

        return newItemId;
    }
    
    //your additional functions here
}
```

![1](https://user-images.githubusercontent.com/37501487/165009221-32350dbd-39d8-4417-bcd4-3eeca242c6a5.jpg)

Once you have the contract ready in your remix IDE, compile the contract to make sure that there are no errors.
Then, deploy it using injected web3 (Metamask Wallet).

![2](https://user-images.githubusercontent.com/37501487/165010624-b00d6d35-5653-4f32-b650-ae83a7fe32c9.jpg)

Click on "view on etherscan" to view the contract address.

You can interact with the contract functions on the left-hand side. Look for the mintNFT function and enter a recipient address, and "https://ipfs.io/ipfs/QmUFbUjAifv9GwJo7ufTB5sccnrNqELhDMafoEmZdPPng7". The second parameter is the tokenURI i.e. a string input that results in a JSON text.

Note: You can search this link on your browser and see the JSON text for yourself. You can also see the image link of the NFT in the image attribute.
![3](https://user-images.githubusercontent.com/37501487/165011671-cd56b652-5b42-4cdf-a9b2-33cad2546cba.jpg)

Once again, click on "view on etherscan" to view the contract address and the token ID.

![4](https://user-images.githubusercontent.com/37501487/165011789-2660b537-94aa-45da-a009-ffbe430f2992.jpg)

You can now add the smart contract address into your Metamask wallet to view the newly minted token.

![5](https://user-images.githubusercontent.com/37501487/165012183-791a52d5-87f0-476c-b649-67eeb1a2a023.jpg)
![6](https://user-images.githubusercontent.com/37501487/165012189-650029bc-78fe-450c-ac77-9aabf71cc9eb.jpg)

You can now see the newly minted token in the wallet of the recipient address.

![7](https://user-images.githubusercontent.com/37501487/165012198-199468df-9c6c-45f5-b556-453e0f40e0cf.jpg)

You can interact with the other functions spoken about in the readme file as we are importing them in this contract.

#### Note: TokenURI string taken as a reference from: https://www.quicknode.com/guides/solidity/how-to-create-and-deploy-an-erc-721-nft
