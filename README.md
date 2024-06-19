# poly-1
---

## NFT Collection Deployment and Management

This repository contains scripts and contracts to create and manage an NFT (Non-Fungible Token) collection using DALLE 2 or Midjourney, store the items on IPFS via Pinata.cloud, deploy on the Goerli Ethereum Testnet (ERC721 or ERC1155), and optionally map the collection using the Polygon network token mapper.

## Requirements

- Python 3.8 or higher
- Node.js 12.x or higher
- Hardhat (for Ethereum smart contract deployment)
- Pinata.cloud API key (for storing items on IPFS)
- Metamask or another Ethereum wallet provider

## Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/your-username/your-repository.git
   cd your-repository
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Configure Environment Variables**

   Create a `.env` file based on `.env.example` and fill in the required variables:

   ```
   PINATA_API_KEY=your_pinata_api_key
   PINATA_SECRET_API_KEY=your_pinata_secret_api_key
   ETHEREUM_PRIVATE_KEY=your_ethereum_private_key
   POLYGON_PRIVATE_KEY=your_polygon_private_key (if applicable)
   ```

   Ensure you have Ethereum and Polygon (Mumbai) testnet RPC URLs configured in your Hardhat config (`hardhat.config.js`).

4. **Deploy Contracts**

   Deploy the ERC721 or ERC1155 contract to the Goerli Ethereum Testnet:

   ```bash
   npx hardhat run scripts/deploy.js --network goerli
   ```

   Note down the deployed contract address.

5. **Mint NFTs**

   Run the Hardhat script to batch mint all NFTs:

   ```bash
   npx hardhat run scripts/mint.js --network goerli
   ```

6. **Map Collection (Optional)**

   Use the Polygon network token mapper to map your NFT collection for visualization:

   [Polygon Token Mapper](https://mapper.matic.today/)

7. **Batch Transfer to Polygon Mumbai**

   Write a Hardhat script to batch transfer all NFTs from Ethereum to Polygon Mumbai using the FxPortal Bridge. First, approve the NFTs to be transferred and then deposit them to the bridge.

   Example scripts can be found in `scripts/transferToPolygon.js`.

8. **Prompt Description**

   Ensure your ERC721 or ERC1155 contract includes a `promptDescription` function that returns the prompt used to generate the images.

## Usage

- Modify the DALLE 2 or Midjourney scripts (`scripts/generateCollection.js`) to generate your desired 5-item collection.
- Ensure all generated items are uploaded to IPFS using Pinata.cloud.
- Customize the metadata and image generation logic as per your requirements.

## Folder Structure

- `/contracts`: Contains ERC721 or ERC1155 smart contract code.
- `/scripts`: Includes Hardhat scripts for deployment, minting, and transferring to Polygon.
- `/metadata`: Placeholder for metadata files, to be filled with actual generated metadata.

## Resources

- [Hardhat Documentation](https://hardhat.org/)
- [IPFS Pinata Documentation](https://pinata.cloud/documentation)
- [Polygon Token Mapper](https://mapper.matic.today/)

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---
