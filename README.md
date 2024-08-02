
### 1. Install Dependency

```bash
npm install
```

### 2. Set .env File

create .env file in root project

```bash
PRIVATE_KEY="your private key"
```

### 3. Update Smart Contract (Skipp if you won't modify NFT name)

- Open contracts folder
- Open Nft.sol file
- Feel free to modify token name and token symbol

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract TestNFT is ERC721 {
    uint256 private _currentTokenId = 0;

    event NFTMinted(address recipient, uint256 tokenId);

    constructor() ERC721("...", "...") {}

    function mintNFT(address recipient) public returns (uint256) {
        _currentTokenId += 1;
        uint256 newItemId = _currentTokenId;
        _mint(recipient, newItemId);

        emit NFTMinted(recipient, newItemId);

        return newItemId;
    }

    function burnNFT(uint256 tokenId) public {
        _burn(tokenId);
    }
}

```

### 4. Compile Smart Contract

```bash
npm run compile
```

### 5. Deploy Smart Contract

```bash
npm run deploy
```

### 6. Mint Token

```bash
npm run mint
```

