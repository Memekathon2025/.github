<div align="center">

# 🐛 MemEat

### 실시간 DeFi 가격이 게임 운명을 결정하는 블록체인 서바이벌 게임

[![MemeCore](https://img.shields.io/badge/Built%20on-MemeCore-FF6B6B?style=flat&logo=ethereum)](https://memecore.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Solidity](https://img.shields.io/badge/Solidity-0.8.28-e6e6e6?logo=solidity)](https://soliditylang.org/)
[![Hardhat](https://img.shields.io/badge/Built%20with-Hardhat-yellow)](https://hardhat.org/)
[![React](https://img.shields.io/badge/React-19-61dafb?logo=react)](https://react.dev/)

**🎮 [지금 플레이하기](https://memeat-fe.onrender.com/)** | **📊 [피치덱 보기](../docs/MemEat_PitchDeck.pdf)** | **🎬 [데모 영상](../docs/MemEat_Demo.mp4)**

</div>

---

## 🎥 데모 영상

<div align="center">

**[📥 데모 영상 다운로드](../docs/MemEat_Demo.mp4)**

</div>

---

## 📊 피치덱

<div align="center">

**[📄 피치덱 PDF 보기](./docs/MemEat_PitchDeck.pdf)**

</div>

---

## 🎯 MemEat이란?

**MemEat**은 클래식 Snake 게임과 DeFi를 결합한 멀티플레이어 블록체인 게임입니다.

게임 속에서 수집한 토큰의 가치는 **실시간 DEX 가격**에 따라 변동합니다. 입장료 이상의 코인을 수집하면 탈출할 수 있습니다.

### 💡 핵심 특징

| 기존 게임             | MemEat                                  |
| --------------------- | --------------------------------------- |
| ❌ Mock 가격 사용     | ✅ **실제 MemeX API 가격 조회**         |
| ❌ 정적인 게임 플레이 | ✅ **실시간 가격 변동으로 동적인 전략** |
| ❌ 높은 가스비 부담   | ✅ **Relayer 패턴으로 가스비 제로**     |
| ❌ 단일 토큰 보상     | ✅ **멀티 토큰 수집 시스템**            |

---

## 🎮 게임 방법

### 1️⃣ 입장료 지불

- Native M 코인 또는 MRC-20 토큰으로 게임 진입
- 스마트 컨트랙트에 입장료 예치 (수수료 5%)

### 2️⃣ 토큰 수집

- 맵에 흩어진 다양한 MRC-20 토큰 수집
- 각 토큰은 실시간 MemeX API 가격으로 평가

### 3️⃣ 탈출 조건

- 수집한 토큰의 총 M 환산 가치 ≥ 입장료

### 4️⃣ 보상 수령

- 탈출 성공 시 수집한 모든 토큰을 지갑으로 전송
- 실패 시 입장료 손실

---

## 🏗️ 시스템 아키텍처

```
┌─────────────────┐
│   MemEat-FE     │  React 19 + TypeScript + Vite
│  (Frontend)     │  • Canvas 게임 렌더링
│                 │  • Wagmi/Viem 지갑 연동
└────────┬────────┘  • Socket.IO 실시간 통신
         │
         │ WebSocket + REST API
         ↓
┌─────────────────┐
│   MemEat-BE     │  Node.js + Express + Socket.IO
│   (Backend)     │  • 게임 로직 처리 (충돌 감지, 점수 계산)
│                 │  • Relayer 역할 (온체인 상태 업데이트)
└────────┬────────┘  • 실시간 MemeX API 가격 조회
         │
         │ Ethers.js
         ↓
┌─────────────────┐
│MemEat-Contract  │  Solidity 0.8.28 + Hardhat 3.0
│  (Smart Contract)│  • WormGame 컨트랙트 (상태 머신)
│                 │  • 입장료 예치 및 보상 분배
└─────────────────┘  • ReentrancyGuard 보안
```

### 핵심 디자인 패턴

**1. Relayer 패턴**

- 플레이어는 가스비 없이 게임 진행
- 백엔드 서버가 게임 결과를 검증하고 온체인 상태 업데이트

**2. 상태 머신**

```
None → Active → Exited → Claimed
              ↘ Dead
```

**3. 실시간 가격 반영**

- MemeX API를 통한 실시간 가격 조회
- 1초마다 업데이트하여 게임에 반영

---

## 🚀 빠른 시작

### 사전 요구사항

- Node.js 18.x 이상
- MetaMask 또는 호환 지갑
- Formicarium Testnet 테스트 토큰

### 1. 스마트 컨트랙트 배포

```bash
cd MemEat-Contract
npm install
npx hardhat compile
npx hardhat ignition deploy ignition/modules/WormGame.ts --network formicarium
```

### 2. 백엔드 서버 실행

```bash
cd MemEat-BE
npm install

# .env 파일 설정
# SUPABASE_URL=your_url
# SUPABASE_SERVICE_ROLE_KEY=your_key
# CONTRACT_ADDRESS=deployed_address
# RPC_URL=https://rpc.formicarium.memecore.net/
# RELAYER_PRIVATE_KEY=your_key
# PORT=3333

npm run dev
```

### 3. 프론트엔드 실행

```bash
cd MemEat-FE
npm install

# .env 파일 설정
# VITE_CONTRACT_ADDRESS=deployed_address
# VITE_ETHERSCAN_API_KEY=your_key
# VITE_PUBLIC_SUPABASE_ANON_KEY=your_key

npm run dev
```

### 4. 게임 플레이

1. http://localhost:5173 접속
2. 지갑 연결 (Formicarium Testnet)
3. 입장료 지불 후 게임 시작
4. 마우스로 뱀 조작, 토큰 수집
5. 탈출 조건 충족 시 "Escape" 클릭
6. 보상 수령

---

## 📦 프로젝트 구조

| 디렉토리                                | 설명                       | 주요 기술                                      |
| --------------------------------------- | -------------------------- | ---------------------------------------------- |
| [`MemEat-FE/`](./MemEat-FE)             | 프론트엔드 게임 클라이언트 | React 19, TypeScript, Canvas, Wagmi, Socket.IO |
| [`MemEat-BE/`](./MemEat-BE)             | 백엔드 게임 서버 & Relayer | Node.js, Express, Socket.IO, Ethers.js         |
| [`MemEat-Contract/`](./MemEat-Contract) | 스마트 컨트랙트            | Solidity 0.8.28, Hardhat, OpenZeppelin         |

각 모듈의 자세한 설명은 해당 디렉토리의 README를 참고하세요.

---

## 🎯 핵심 기능

### 1. 가스비 제로 게임 (Relayer Pattern)

```typescript
// 플레이어는 백엔드에 이벤트만 전송
socket.emit("game-over", { playerId });

// 백엔드(Relayer)가 트랜잭션 처리
await contract
  .connect(relayerWallet)
  .updateGameState(playerAddress, "Dead", [], []);
// 플레이어는 가스비 0원!
```

### 2. 실시간 DEX 가격 조회

```typescript
// scripts/get-pool-price.ts
const [reserve0, reserve1] = await poolContract.getReserves();
const token0 = await poolContract.token0();

const price = isToken0
  ? Number(reserve1) / Number(reserve0)
  : Number(reserve0) / Number(reserve1);
```

### 3. 상태 머신 보안

```solidity
// contracts/WormGame.sol
function updateGameState(
    address player,
    PlayerStatus newStatus,
    address[] calldata rewardTokens,
    uint256[] calldata rewardAmounts
) external onlyRelayer {
    require(playerData.status == PlayerStatus.Active, "Not active");
    require(
        newStatus == PlayerStatus.Exited || newStatus == PlayerStatus.Dead,
        "Invalid status"
    );
    // 상태 업데이트...
}
```

---

## 🔒 보안

### 스마트 컨트랙트

- ✅ **ReentrancyGuard** (OpenZeppelin)
- ✅ **Checks-Effects-Interactions** 패턴
- ✅ **권한 관리** (onlyOwner, onlyRelayer)
- ✅ **수수료율 제한** (최대 10%)

### 백엔드

- ✅ **환경 변수 분리** (.env)
- ✅ **CORS 설정**
- ✅ **Input Validation**

---

## 🌐 배포 정보

### Formicarium Testnet

| 항목                  | 값                                                                                                                                 |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Network Name**      | Formicarium Testnet                                                                                                                |
| **Chain ID**          | 43521                                                                                                                              |
| **RPC URL**           | https://rpc.formicarium.memecore.net                                                                                               |
| **Explorer**          | https://testnet.memecorescan.io/                                                                                                   |
| **WormGame Contract** | [`0x04686e9284B54d8719A5a4DecaBE82158316C8f0`](https://testnet.memecorescan.io/address/0x04686e9284B54d8719A5a4DecaBE82158316C8f0) |

### 메타마스크 네트워크 추가

```json
{
  "chainId": "0xA9E1",
  "chainName": "Formicarium Testnet",
  "nativeCurrency": {
    "name": "Meme",
    "symbol": "M",
    "decimals": 18
  },
  "rpcUrls": ["https://rpc.formicarium.memecore.net"],
  "blockExplorerUrls": ["https://testnet.memecorescan.io/"]
}
```

---

## 🛠️ 개발 가이드

### 새로운 토큰 추가

1. DEX에서 Pool 주소 확인
2. `MemEat-Contract/scripts/get-pool-price.ts`에서 가격 조회 테스트
3. `MemEat-BE`의 토큰 설정 추가
4. `MemEat-FE`의 UI 업데이트

### 스마트 컨트랙트 수정

```bash
# 컨트랙트 수정
vim MemEat-Contract/contracts/WormGame.sol

# 컴파일 및 테스트
npx hardhat compile
npx hardhat test

# 배포
npx hardhat ignition deploy ignition/modules/WormGame.ts --network formicarium

# ABI 업데이트
cp artifacts/contracts/WormGame.sol/WormGame.json ../MemEat-BE/src/abis/
cp artifacts/contracts/WormGame.sol/WormGame.json ../MemEat-FE/src/abis/
```

---

## 📄 라이선스

이 프로젝트는 [MIT License](./LICENSE) 하에 배포됩니다.

---

<div align="center">

Made with ❤️ by the MemEat Team

**[⬆ Back to Top](#-memeat)**

</div>
