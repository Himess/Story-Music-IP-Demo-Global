### Introduction
This guide is designed to help you register your music as IP (Intellectual Property) and mint it as an NFT using the Story SDK.
 


## 0. Creating a Test Wallet and Requesting Faucet Tokens

We recommend using a new, empty Metamask test wallet for this project.

1- Create your wallet.
2- Click on the three dots in the top-right corner and select Account Details.


![image](https://github.com/user-attachments/assets/e796eae9-3934-4430-8670-c5716b9b6184)

3- Click Export Private Key and save it securely; you’ll need it later.

After this, you’ll need Test IP tokens.
Go to Story Faucet https://faucet.story.foundation/ to request tokens.

Note: You’ll need Gitcoin scores to request tokens. You can transfer them from your main account to your test wallet.

It typically takes 2–3 minutes for the Test IP tokens to arrive.

Once ready, you can proceed with the setup.

---

## 1. Create a Project Folder

Create a folder on your computer. For example: `StoryProject` .
This folder will contain all your files and code.

![image](https://github.com/user-attachments/assets/cc275a3e-386f-4832-8ba8-9281ee12be42)

---

## 2. Install Visual Studio Code (VS Code)

[VS Code](https://code.visualstudio.com/) 

Download VS Code https://code.visualstudio.com/ for your operating system.

1.Run the downloaded .exe file.
2.Accept the license agreement and click Next.
3.Choose an installation location (default is fine) and click Next.
4.Check the box for Add to PATH. This allows you to run VS Code from the terminal.
5.Click Install and wait for the installation to complete.
Congratulations, the installation is complete!

---

## 3. Install Required Tools

Story ile çalışmaya başlamak için aşağıdaki araçları bilgisayarınıza kurmanız gerekiyor:

### Node.js ve npm Kurulumu


Installing Node.js and npm
Go to the Node.js website and download the LTS (Long-Term Support) version.

[Node.js](https://nodejs.org/tr)


![image](https://github.com/user-attachments/assets/e2a659e7-0c57-402a-a235-ffc3f00e39cb)

Installation Steps:

Run the downloaded installer.
Complete the installation by clicking Next on each step.
Once installed, run the following commands in your terminal:
   ```bash
   npm install -g ts-node
   npm install -g typescript
```

---

## 4. Open Visual Studio Code

1. In VS Code, go to File > Open Folder and select the StoryProject folder you created earlier.

2. Open the terminal by clicking Terminal > New Terminal from the top menu.


![image](https://github.com/user-attachments/assets/32ebc389-6810-488f-b05a-841e5c0d297e)

To verify that Node.js is installed correctly, run the following commands in the terminal:

```bash
node -v
npm -v
```

If you see the versions displayed as below, the installation was successful:

![image](https://github.com/user-attachments/assets/9d39f4d7-0ce9-43fc-89ee-9412e2b99087)

---

## 5. Creating Music with Suno 🎵

Suno is an AI-powered platform that allows you to create music by entering a few descriptive words. We’ll use this platform for our project.

1.Visit https://suno.com/create?wid=default and create an account.
2.In the Song Description field, write what kind of music you want.
Examples:

- "An exciting guitar solo"
- "A soft piano tune inspired by nature"


<img width="553" alt="SUNO" src="https://github.com/user-attachments/assets/723783a3-6173-4a06-8ba3-d486a80aa65b" />

For example, I created music inspired by the "lazy and sleepy nature of Celestine Sloths."
I loved the result! 😊 I recommend listening to it at the end of this guide.

3.After entering your prompt, click Create.
4.Once your music is generated, click on it.

<img width="992" alt="Celestine Sloth's Lullaby" src="https://github.com/user-attachments/assets/15b85ee6-c42b-47d8-bd18-e4a350687919" />

5.Click Share to get the link. The link should look like this:

`https://suno.com/song/eb448e54-4b1b-4558-966c-95dfb31b6b3d` 

The CID in the link is important. In the example above:
`eb448e54-4b1b-4558-966c-95dfb31b6b3d`

6.Use this CID to construct the final music URL like this:

Bu verdiği CID ‘ yi şu şekilde yazacağız. Örnek bu şekilde olmalı.


`https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3`

Make sure to save this URL carefully, as we’ll use it later.

---

## 6. Uploading Your Music NFT Image to IPFS

This step is quite simple.

1.Go back to Pinata at https://app.pinata.cloud/ipfs/files.
2.Click +Add and then File Upload.


<img width="1448" alt="Ekran Resmi 2025-01-27 01 09 26" src="https://github.com/user-attachments/assets/532d8e90-dd45-4afb-ba93-654d20f2cb05" />






![Pasted Graphic 4](https://github.com/user-attachments/assets/bbdf6b9d-7c0a-4733-bb62-596c5079783f)

Once the file is uploaded, click on it. You’ll see a link like this:


`https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54`

This link is critical, as you’ll use it later.

Note: If you haven't configured Pinata Gateways, you may encounter errors. Go back to the interface, create them, and then proceed.




---


## 7. Initializing the Project

Run the following command to initialize a new Node.js project:

```bash
npm init -y
```

This will create a `package.json` file in your project directory.

The output should look like this:

![image](https://github.com/user-attachments/assets/cda37400-2da5-4736-a1ec-14e0bb3561f3)

---

## 8. Create a `.env` File

Create a `.env` file in your project directory to store sensitive information like API keys and private keys.

Steps:

1.In VS Code, right-click in the project folder and select New File.
2.Name the file `.env` and press Enter.

The file should look like this:

![image](https://github.com/user-attachments/assets/9997e18c-85d1-4c64-a06c-bd4b52a73d03)


Sonuç şu şekilde olacaktır:

![image](https://github.com/user-attachments/assets/049c1b5b-6d18-497e-8764-d8f8d5b3e22d)

---

## 9. Add Your Testnet Wallet Private Key

Add your Story Testnet wallet private key to the `.env` file. This key allows your project to interact with the Story network.

Example:
```bash
WALLET_PRIVATE_KEY=<YOUR_WALLET_PRIVATE_KEY>
Not: Özel anahtarınızı asla başkasıyla paylaşmayın. Yeni bir cüzdan oluşturmanızı öneririm.
```

Note: Never share your private key with others. It’s recommended to create a new wallet for testing purposes.

Sample Output:
```bash
WALLET_PRIVATE_KEY=e12312312312312312312312312312312312312312312312312312312312312
```

---

## 10. Add Your Pinata API Key

Pinata is used to upload files to IPFS.

1.Create an account on Pinata and generate an API key (JWT) https://app.pinata.cloud/developers/api-keys by navigating to API Keys.
2.Click + New Key and check the following options:


![image](https://github.com/user-attachments/assets/f64181c3-8c0d-445f-ab9f-a48d995a8533)

Save the JWT key and add it to your `.env` file:
```bash
PINATA_JWT=<YOUR_PINATA_JWT>
```

Example:
```bash
PINATA_JWT=e12321431242141424
```

---

## 11. Update the `.env` File

Add the RPC URL and the NFT contract address to your `.env` file.

```bash
RPC_PROVIDER_URL=https://rpc.odyssey.storyrpc.io
NFT_CONTRACT_ADDRESS=0x041B4F29183317Fd352AE57e331154b73F8a1D73
```

Final `.env` Example:

```bash
WALLET_PRIVATE_KEY=e12312312312312312312312312312312312312312312312312312312312312
PINATA_JWT=e12321431242141424
RPC_PROVIDER_URL=https://rpc.odyssey.storyrpc.io
NFT_CONTRACT_ADDRESS=0x041B4F29183317Fd352AE57e331154b73F8a1D73
```

---

## 12. Install Required Packages

Run the following command in your terminal to install the necessary dependencies for the project:
```bash
npm install @story-protocol/core-sdk pinata-web3 viem
```

Once installed, your project structure should look like this:

![image](https://github.com/user-attachments/assets/38737bb1-65db-447a-a7e2-93c10047889f)

---

## 13. Setting Up Project Files

In this step, we will configure some basic files required to use the Story SDK and create IP data.


### 13.1 Create `utils.ts`

This file will be used to configure the Story SDK (`config`) and initialize the client (`client`).

1.Create a file named `utils.ts` in the root directory of your project.
2.Paste the following code into the file:

```typescript
import { StoryClient, StoryConfig } from '@story-protocol/core-sdk';
import { http } from 'viem';
import { privateKeyToAccount, Address, Account } from 'viem/accounts';

// Çevresel değişkenleri kontrol edin
const privateKey: Address = `0x${process.env.WALLET_PRIVATE_KEY}`;
if (!privateKey) {
  throw new Error('WALLET_PRIVATE_KEY bulunamadı. Lütfen .env dosyanızı kontrol edin.');
}

const account: Account = privateKeyToAccount(privateKey);

const config: StoryConfig = {
  account: account,
  transport: http(process.env.RPC_PROVIDER_URL),
  chainId: 'odyssey',
};

const client = StoryClient.newClient(config);

export { client, account };
```

The result should look like this:

![image](https://github.com/user-attachments/assets/6957e055-ab6a-45a3-9e04-95d52ce9f6b2)

---

## 13.2 Configure Metadata Files

Note: We'll make some changes here to create IP and NFT metadata.

1.Create a file named `main.ts` in the root directory of your project.
2.Paste the following code into the file:

```typescript
import { IpMetadata } from '@story-protocol/core-sdk';
import { client, account } from './utils';
import { uploadJSONToIPFS } from './uploadToIpfs';
import { createHash } from 'crypto';
import { Address } from 'viem';
import { mintNFT } from './mintNFT';

async function main() {
  // 1. IP Metadata oluştur
  const ipMetadata: IpMetadata = client.ipAsset.generateIpMetadata({
    title: 'Celestine Sloths Uyku Sesi',
    description: 'Celestine Sloths NFT topluluğuna özel uyku sesi kaydı.',
    watermarkImg: 'https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54',
    ipType: 'Music',
    media: [
      {
        name: 'Celestine Uyku Sesi',
        url: 'https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3',
        mimeType: 'audio/mpeg',
      },
    ],
    attributes: [
      {
        key: 'Artist',
        value: 'Celestine Sloths',
      },
      {
        key: 'Mood',
        value: 'Relaxing',
      },
      {
        key: 'Duration',
        value: '3:45',
      },
      {
        key: 'Source',
        value: 'Suno.com',
      },
    ],
    creators: [
      {
        name: 'Celestine Community',
        address: account.address,
        contributionPercent: 100,
      },
    ],
  });

  // 2. NFT Metadata oluştur
  const nftMetadata = {
    name: 'Celestine Sloths NFT',
    description: 'Celestine Sloths topluluğunun uyku sesi NFT\'si.',
    image: 'https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54', // NFT için görsel URL'si
    media: [
      {
        name: 'Celestine Uyku Sesi',
        url: 'https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3',
        mimeType: 'audio/mpeg',
      },
    ],
    attributes: [
      {
        key: 'Artist',
        value: 'Celestine Sloths',
      },
      {
        key: 'Mood',
        value: 'Relaxing',
      },
      {
        key: 'Duration',
        value: '3:45',
      },
      {
        key: 'Source',
        value: 'Suno.com',
      },
    ],
  };

  // 3. Metadata'ları IPFS'e yükle
  const ipIpfsHash = await uploadJSONToIPFS(ipMetadata);
  const ipHash = createHash('sha256').update(JSON.stringify(ipMetadata)).digest('hex');
  const nftIpfsHash = await uploadJSONToIPFS(nftMetadata);
  const nftHash = createHash('sha256').update(JSON.stringify(nftMetadata)).digest('hex');

  console.log('IP Metadata IPFS Hash:', ipIpfsHash);
  console.log('NFT Metadata IPFS Hash:', nftIpfsHash);

  // 4. NFT Mint Et
  const tokenId = await mintNFT(account.address, `https://ipfs.io/ipfs/${nftIpfsHash}`);
  if (!tokenId) {
    console.error('NFT mint işlemi başarısız oldu!');
    return;
  }

  console.log('Mint edilen NFT Token ID:', tokenId);

  // 5. NFT'yi IP Asset olarak kaydet
  const response = await client.ipAsset.registerIpAndAttachPilTerms({
    nftContract: process.env.NFT_CONTRACT_ADDRESS as Address,
    tokenId: tokenId,
    terms: [], // Özel IP şartlarını buraya ekleyebilirsiniz.
    ipMetadata: {
      ipMetadataURI: `https://ipfs.io/ipfs/${ipIpfsHash}`,
      ipMetadataHash: `0x${ipHash}`,
      nftMetadataURI: `https://ipfs.io/ipfs/${nftIpfsHash}`,
      nftMetadataHash: `0x${nftHash}`,
    },
    txOptions: { waitForTransaction: true },
  });

  console.log(`Transaction Hash: ${response.txHash}`);
  console.log(`IP Asset ID: ${response.ipId}`);
  console.log(`View on Explorer: https://explorer.story.foundation/ipa/${response.ipId}`);
}

main().catch((error) => {
  console.error('Bir hata oluştu:', error);
});
```

Replace the Links
In the above `main.ts`, replace the following links with your custom ones:

1.Replace the `watermarkImg` link:

```bash
'https://plum-conventional-cephalopod-536.mypinata.cloud/ipfs/bafkreifqjicmmnhianug4sgbainou66qcanhkhoyz2rhvnq2gcp6tegt54'
```

2.Replace the `url` for the music:

```bash
'https://cdn1.suno.ai/eb448e54-4b1b-4558-966c-95dfb31b6b3d.mp3'
```

You can optionally update other parts such as titles and attributes to fit your project theme.

---

## 13.3 Create `uploadToIpfs.ts`

PIn your project root directory, create a file named `uploadToIpfs.ts`. Paste the following code into the file:

```typescript
import { PinataSDK } from 'pinata-web3';

const pinata = new PinataSDK({
  pinataJwt: process.env.PINATA_JWT,
});

export async function uploadJSONToIPFS(jsonMetadata: any): Promise<string> {
  const { IpfsHash } = await pinata.upload.json(jsonMetadata);
  return IpfsHash;
}
```

---

## 13.4 Configure TypeScript and `tsconfig.json`

In the project root, create a file named `tsconfig.json`. Add the following settings:

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "CommonJS",
    "strict": true,
    "esModuleInterop": true,
    "moduleResolution": "node",
    "baseUrl": "./",
    "paths": {
      "*": ["node_modules/*"]
    }
  },
  "include": ["**/*.ts"],
  "exclude": ["node_modules"]
}
```

The result should look like this:

![image](https://github.com/user-attachments/assets/c06ddcb0-23a5-475b-a254-f53e6239d909)

---

## 14. Define the Mint Function
In the project root, create a file named `mintNFT.ts` and add the following code:

```typescript
import { http, createWalletClient, createPublicClient, Address } from 'viem';
import { privateKeyToAccount } from 'viem/accounts';
import { odyssey } from '@story-protocol/core-sdk';
import { account } from './utils';
import { defaultNftContractAbi } from './defaultNftContractAbi';

const baseConfig = {
  chain: odyssey,
  transport: http(process.env.RPC_PROVIDER_URL),
} as const;

export const publicClient = createPublicClient(baseConfig);
export const walletClient = createWalletClient({
  ...baseConfig,
  account,
});

export async function mintNFT(to: Address, uri: string): Promise<number | undefined> {
  const { request } = await publicClient.simulateContract({
    address: process.env.NFT_CONTRACT_ADDRESS as Address,
    functionName: 'mintNFT',
    args: [to, uri],
    abi: defaultNftContractAbi,
  });
  const hash = await walletClient.writeContract(request);
  const { logs } = await publicClient.waitForTransactionReceipt({
    hash,
  });
  if (logs[0].topics[3]) {
    return parseInt(logs[0].topics[3], 16);
  }
}
```

---

## 15. Create `defaultNftContractAbi.ts`

In the project root, create a file named `defaultNftContractAbi.ts` and paste the following code:

```typescript
export const defaultNftContractAbi = [
  {
    inputs: [
      {
        internalType: "address",
        name: "to",
        type: "address",
      },
      {
        internalType: "string",
        name: "uri",
        type: "string",
      },
    ],
    name: "mintNFT",
    outputs: [
      {
        internalType: "uint256",
        name: "tokenId",
        type: "uint256",
      },
    ],
    stateMutability: "nonpayable",
    type: "function",
  },
];
```

---

## 16. Run the Project

Once all files have been created, use the following command to run the project in your terminal:

```bash
ts-node main.ts
```

Example Output

After successfully running the project, you should see the following output:

IP Metadata IPFS Hash: bafkreica73k4b7kkmdkxjscvrqr3qprdfwv2hifp6kwdnoowrxumrczgvq
NFT Metadata IPFS Hash: bafkreih5dspmybxw4orleqxneztdmx6sjxrcypbotffpetorxb3vmhu7sq
Mint edilen NFT Token ID: 492
Transaction Hash: 0xc826f63c7bdb444fac7f5c31a94ef198c4004ab6109ee3c6be60b6cf9b511c3e
IP Asset ID: 0x3ce426e3376dA1786c18e487f280FD32A674F6F8
View on Explorer: https://explorer.story.foundation/ipa/0x3ce426e3376dA1786c18e487f280FD32A674F6F8

Congratulations! 🎉
You have successfully completed the project and registered your music as an IP asset on the Story protocol.
