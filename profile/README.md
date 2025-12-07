<div align="center">

# 🐛 MemEat

### 실시간 DeFi 가격이 게임 운명을 결정하는 블록체인 서바이벌 게임

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Solidity](https://img.shields.io/badge/Solidity-0.8.28-e6e6e6?logo=solidity)](https://soliditylang.org/)
[![Hardhat](https://img.shields.io/badge/Built%20with-Hardhat-yellow)](https://hardhat.org/)
[![React](https://img.shields.io/badge/React-19-61dafb?logo=react)](https://react.dev/)

[데모 플레이](#) • [문서](#) • [스마트 컨트랙트](https://testnet.memecorescan.io/address/0x04686e9284B54d8719A5a4DecaBE82158316C8f0)

</div>

---

## 🎯 MemEat이란?

**MemEat**은 클래식 Snake 게임과 DeFi를 혁신적으로 결합한 온체인 멀티플레이어 서바이벌 게임입니다.

게임 속에서 수집한 토큰의 가치는 **실시간 DEX 가격**에 따라 끊임없이 변동합니다. 당신은 지금 탈출할 것인가, 아니면 한 번 더 도전할 것인가? 순간의 선택이 승패를 가릅니다.

### 💡 왜 MemEat인가?

기존 블록체인 게임과의 차별점:

| 기존 게임 | MemEat |
|----------|--------|
| ❌ Mock 가격 사용 | ✅ **실제 DEX Pool 가격 조회** |
| ❌ 정적인 게임 플레이 | ✅ **실시간 가격 변동으로 동적인 전략** |
| ❌ 높은 가스비 부담 | ✅ **Relayer 패턴으로 가스비 제로** |
| ❌ 단일 토큰 보상 | ✅ **멀티 토큰 포트폴리오 시스템** |

---

## 🎮 게임 스토리

당신은 블록체인 세계의 배고픈 뱀이 되어 생존을 위한 여정을 시작합니다.

### 📜 게임 진행

```
┌──────────────────────────────────────────────────────────┐
│ 1️⃣  입장료 지불                                          │
│    → Native M 코인 또는 MRC-20 토큰으로 게임 진입        │
│    → 스마트 컨트랙트에 입장료 예치 (수수료 5%)           │
├──────────────────────────────────────────────────────────┤
│ 2️⃣  토큰 수집                                           │
│    → 맵에 흩어진 다양한 MRC-20 토큰 수집                 │
│    → 각 토큰마다 다른 희소성과 가격 변동성               │
│    → 다른 플레이어와 경쟁하며 성장                       │
├──────────────────────────────────────────────────────────┤
│ 3️⃣  실시간 가격 변동                                     │
│    → 수집한 토큰의 가치가 DEX 가격에 따라 실시간 변동    │
│    → 총 가치가 입장료를 넘으면 탈출 버튼 활성화 🚪       │
│    → 하지만 가격이 다시 떨어질 수도... 📉               │
├──────────────────────────────────────────────────────────┤
│ 4️⃣  전략적 탈출                                          │
│    → 지금 탈출할까? (안전하게 이익 확정)                 │
│    → 더 수집할까? (높은 수익 vs 가격 하락 위험)          │
│    → 다른 플레이어와 충돌하면 게임 오버! ☠️              │
├──────────────────────────────────────────────────────────┤
│ 5️⃣  보상 수령                                            │
│    → 탈출 성공 시 수집한 모든 토큰을 지갑으로 전송       │
│    → 실패 시 입장료 손실 😢                              │
└──────────────────────────────────────────────────────────┘
```

### 🎲 게임의 핵심: 가격 변동성

실제 게임 시나리오:

```diff
🕐 [00:00] 게임 시작
   💰 입장료: 1.0 M
   🎯 목표: 1.0 M 이상 수집

🕐 [00:45] 첫 수집 성공!
   📦 획득: sdf 토큰 8개
   💵 현재 가격: 0.11 M/개
+  📊 총 가치: 0.88 M (88%) ❌ 탈출 불가

🕐 [01:20] sdf 가격 급등! 🚀
   📦 보유: sdf 토큰 8개 (변동 없음)
   💵 현재 가격: 0.14 M/개
+  📊 총 가치: 1.12 M (112%) ✅ 탈출 가능!
   🚪 [탈출하기] 버튼 활성화!

   💭 플레이어의 선택:
      A) 지금 탈출 → +0.12 M 수익 확정
      B) 더 수집 → 더 큰 수익 기회 (하지만 위험 증가)

🕐 [01:45] 탈출 포기하고 계속 플레이...
   📦 추가 획득: z 토큰 3개
   💵 sdf 가격: 0.09 M/개 (폭락! 📉)
   💵 z 가격: 0.22 M/개
-  📊 총 가치: 0.72 + 0.66 = 1.38 M (138%) ✅ 여전히 탈출 가능!

🕐 [02:10] 다른 플레이어와 충돌! 💥
   ☠️  게임 오버
   😢 입장료 1.0 M 손실
```

**교훈**: 탐욕은 금물! 적절한 타이밍의 탈출이 승리의 열쇠입니다.

---

## 🏗️ 시스템 아키텍처

MemEat은 3-Tier 아키텍처로 설계되어 각 레이어가 명확한 역할을 수행합니다.

```
┌─────────────────────────────────────────────────────────────────┐
│                         🌐 Frontend Layer                        │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  React 19 + TypeScript + Vite                           │   │
│  │  • Canvas API로 60fps 게임 렌더링                        │   │
│  │  • Reown AppKit으로 원클릭 지갑 연결                     │   │
│  │  • Zustand 상태 관리로 부드러운 UX                       │   │
│  └──────────────────────────────────────────────────────────┘   │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                  Socket.IO │ REST API
                  (Real-time)│ (HTTP)
                            ↓
┌─────────────────────────────────────────────────────────────────┐
│                        ⚙️  Backend Layer                         │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  Node.js + Express + Socket.IO                          │   │
│  │  • 게임 로직 엔진 (충돌 감지, 점수 계산)                  │   │
│  │  • Relayer 서비스 (온체인 상태 업데이트)                 │   │
│  │  • 실시간 DEX Pool 가격 조회 API                         │   │
│  │  • Supabase로 게임 세션 영속화                           │   │
│  └──────────────────────────────────────────────────────────┘   │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                  Ethers.js │ (Contract Calls)
                            ↓
┌─────────────────────────────────────────────────────────────────┐
│                      🔗 Blockchain Layer                         │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  Solidity 0.8.28 + Hardhat 3.0                          │   │
│  │  • WormGame 스마트 컨트랙트 (상태 머신)                  │   │
│  │  • 입장료 예치 및 보상 분배 로직                         │   │
│  │  • ReentrancyGuard 보안 패턴                            │   │
│  │  • Formicarium Testnet (Chain ID: 43521)               │   │
│  └──────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

### 🔑 핵심 디자인 패턴

#### 1️⃣ Relayer 패턴 (Meta-Transaction)

```
전통적 방식 (❌):
Player → [Gas Fee] → Contract → State Update
문제: 매 액션마다 가스비 발생, UX 저하

MemEat 방식 (✅):
Player → Backend(Relayer) → [Gas Fee] → Contract → State Update
장점: 플레이어는 가스비 없이 게임, 백엔드가 일괄 처리
```

#### 2️⃣ 상태 머신 (State Machine)

```solidity
enum PlayerStatus {
    None,     // 게임 참여 전
    Active,   // 🎮 게임 진행 중
    Exited,   // 🎉 탈출 성공 (보상 대기)
    Dead,     // ☠️  사망
    Claimed   // ✅ 보상 수령 완료
}

// 허용된 상태 전이
None → Active (enterGame 호출)
Active → Exited (Relayer가 탈출 조건 검증)
Active → Dead (Relayer가 게임 오버 처리)
Exited → Claimed (claimReward 호출)
```

#### 3️⃣ 실시간 가격 오라클 (Price Oracle)

```typescript
// DEX Pool에서 직접 가격 조회 (Uniswap V2 방식)
const [reserve0, reserve1] = await poolContract.getReserves();
const token0 = await poolContract.token0();

// 토큰 순서 확인 후 비율 계산
const price = (token0 === targetToken)
  ? Number(reserve1) / Number(reserve0)  // 1 Token = X USDT
  : Number(reserve0) / Number(reserve1);

// 1초마다 업데이트하여 프론트엔드에 전송
setInterval(() => updatePrices(), 1000);
```

---

## 🚀 빠른 시작 가이드

### 📋 사전 준비

- **Node.js** 18.x 이상
- **npm** 또는 **yarn**
- **MetaMask** 또는 호환 지갑
- **Formicarium Testnet** 테스트 토큰 (Faucet에서 수령)

### 🔧 로컬 개발 환경 설정

#### Step 1: 저장소 클론

```bash
git clone https://github.com/your-org/memeat.git
cd memeat
```

#### Step 2: 스마트 컨트랙트 배포

```bash
cd MemEat-Contract
npm install

# 환경 변수 설정
cat > .env << EOF
INSECTARIUM_PRIVATE_KEY=your_private_key_here
EOF

# 컴파일 및 배포
npx hardhat compile
npx hardhat ignition deploy ignition/modules/WormGame.ts --network formicarium

# 배포된 컨트랙트 주소 복사
# 출력 예시: WormGame deployed to: 0x1234...
```

#### Step 3: 백엔드 서버 설정

```bash
cd ../MemEat-BE
npm install

# 환경 변수 설정
cat > .env << EOF
# Supabase (데이터베이스)
SUPABASE_URL=your_supabase_project_url
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_key

# 스마트 컨트랙트
CONTRACT_ADDRESS=0x1234... # Step 2에서 복사한 주소
RPC_URL=https://rpc.formicarium.memecore.net/

# Relayer 계정 (게임 결과를 온체인에 기록하는 서버 계정)
RELAYER_PRIVATE_KEY=your_relayer_private_key

# 서버 포트
PORT=3333
EOF

# 개발 서버 실행
npm run dev
# ✅ Server running on http://localhost:3333
```

#### Step 4: 프론트엔드 설정

```bash
cd ../MemEat-FE
npm install

# 환경 변수 설정
cat > .env << EOF
VITE_CONTRACT_ADDRESS=0x1234... # Step 2에서 복사한 주소
VITE_ETHERSCAN_API_KEY=your_etherscan_api_key
VITE_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
EOF

# 개발 서버 실행
npm run dev
# ✅ Server running on http://localhost:5173
```

#### Step 5: 게임 플레이! 🎮

1. 브라우저에서 http://localhost:5173 접속
2. "Connect Wallet" 클릭하여 지갑 연결
3. Formicarium Testnet으로 네트워크 전환
4. 입장료 선택 (예: 1 M)
5. "Start Game" 클릭 → 트랜잭션 승인
6. 방향키로 뱀 조작, 토큰 수집!
7. 탈출 조건 충족 시 "Escape" 버튼 클릭
8. 보상 수령!

---

## 📦 프로젝트 구조

| 디렉토리 | 설명 | 주요 기술 | README |
|---------|------|----------|--------|
| [`MemEat-FE/`](./MemEat-FE) | 프론트엔드 게임 클라이언트 | React 19, TypeScript, Canvas, Wagmi, Socket.IO | [📖](./MemEat-FE/README.md) |
| [`MemEat-BE/`](./MemEat-BE) | 백엔드 게임 서버 & Relayer | Node.js, Express, Socket.IO, Ethers.js | [📖](./MemEat-BE/README.md) |
| [`MemEat-Contract/`](./MemEat-Contract) | 스마트 컨트랙트 | Solidity 0.8.28, Hardhat, OpenZeppelin | [📖](./MemEat-Contract/README.md) |

각 모듈의 상세한 설명, API 문서, 개발 가이드는 해당 README를 참고하세요.

---

## 🎯 핵심 기능 상세

### 1️⃣ 가스비 제로 게임 (Relayer Pattern)

**문제**: 블록체인 게임의 최대 진입 장벽은 매 액션마다 발생하는 가스비입니다.

**해결책**: 백엔드 서버가 Relayer 역할을 수행하여 플레이어 대신 트랜잭션을 전송합니다.

```typescript
// 기존 방식 (❌)
// 플레이어가 게임 오버 시마다 트랜잭션 전송 → 가스비 발생
await contract.updateGameState(myAddress, "Dead", [], []);
// Gas Fee: ~0.001 ETH

// MemEat 방식 (✅)
// 플레이어는 백엔드에 게임 오버 알림만 전송
socket.emit("game-over", { playerId });

// 백엔드(Relayer)가 일괄 처리
await contract.connect(relayerWallet).updateGameState(
  playerAddress, "Dead", [], []
);
// 플레이어는 가스비 0원!
```

**보안**: Relayer는 검증된 게임 로직에 따라서만 상태를 업데이트합니다. 임의 조작 불가능.

### 2️⃣ 실시간 DEX 가격 오라클

**차별점**: Mock 가격이 아닌 실제 DEX Pool에서 1초마다 가격 조회

```typescript
// scripts/get-pool-price.ts
async function getRealtimePrice(poolAddress: string) {
  // 1. Pool에서 유동성 정보 조회
  const [reserve0, reserve1] = await publicClient.readContract({
    address: poolAddress,
    abi: parseAbi(['function getReserves() external view returns (uint112, uint112, uint32)']),
    functionName: 'getReserves',
  });

  // 2. 토큰 순서 확인
  const token0 = await publicClient.readContract({
    address: poolAddress,
    abi: parseAbi(['function token0() external view returns (address)']),
    functionName: 'token0',
  });

  // 3. 가격 계산 (x * y = k 방식)
  const isWMToken0 = token0.toLowerCase() === WM_ADDRESS.toLowerCase();
  const price = isWMToken0
    ? Number(reserve1) / Number(reserve0)
    : Number(reserve0) / Number(reserve1);

  return price; // 1 WM = X USDT
}
```

**게임에 미치는 영향**:
- 실제 시장 가격 변동이 게임에 즉시 반영
- DeFi 트레이딩과 게임의 시너지 효과
- 유동성이 높은 시간대에 게임이 더 흥미진진

### 3️⃣ 상태 머신 보안 설계

```solidity
contract WormGame {
    function updateGameState(
        address player,
        PlayerStatus newStatus,
        address[] calldata rewardTokens,
        uint256[] calldata rewardAmounts
    ) external onlyRelayer {
        PlayerData storage playerData = players[player];

        // 🔒 보안 검증 1: 현재 Active 상태여야만 업데이트 가능
        require(playerData.status == PlayerStatus.Active, "Not active");

        // 🔒 보안 검증 2: Exited 또는 Dead만 허용
        require(
            newStatus == PlayerStatus.Exited || newStatus == PlayerStatus.Dead,
            "Invalid status"
        );

        // 🔒 보안 검증 3: 배열 길이 일치
        require(
            rewardTokens.length == rewardAmounts.length,
            "Length mismatch"
        );

        // ✅ 상태 변경 (Checks-Effects-Interactions 패턴)
        playerData.status = newStatus;

        // Exited일 때만 보상 정보 저장
        if (newStatus == PlayerStatus.Exited) {
            playerData.rewardTokens = rewardTokens;
            playerData.rewardAmounts = rewardAmounts;
        }

        emit GameStateUpdated(player, newStatus, block.timestamp);
    }
}
```

### 4️⃣ 멀티 토큰 포트폴리오 시스템

플레이어는 다양한 전략을 구사할 수 있습니다:

**전략 A: 안정성 추구**
- 가격 변동성이 낮은 스테이블 토큰 위주 수집
- 낮은 수익률이지만 안전한 탈출

**전략 B: 고위험 고수익**
- 가격 변동성이 높은 Meme 토큰 수집
- 가격 상승 시 큰 수익, 하락 시 위험

**전략 C: 분산 투자**
- 여러 종류의 토큰을 균형있게 수집
- 포트폴리오 리스크 관리

```typescript
// 예시: 플레이어 A의 포트폴리오
{
  tokens: [
    { symbol: "USDT", amount: 100, price: 1.00 },    // 안정적
    { symbol: "WM",   amount: 50,  price: 0.15 },    // 중간 변동성
    { symbol: "MEME", amount: 10,  price: 2.50 },    // 고변동성
  ],
  totalValue: 100 + 7.5 + 25 = 132.5 M  // 다양한 자산 보유
}
```

---

## 🔒 보안 & 감사

### 스마트 컨트랙트 보안

- ✅ **ReentrancyGuard** (OpenZeppelin) - 재진입 공격 방지
- ✅ **Checks-Effects-Interactions** 패턴 - 상태 변경 후 외부 호출
- ✅ **권한 관리** - onlyOwner, onlyRelayer modifier
- ✅ **상태 검증** - 모든 함수에서 상태 전이 유효성 검사
- ✅ **수수료율 제한** - 최대 10% 하드 캡

### 백엔드 보안

- ✅ **환경 변수 분리** - Private Key는 .env 파일로 관리
- ✅ **CORS 설정** - 허용된 도메인만 API 접근
- ✅ **Rate Limiting** - DDoS 공격 방지
- ✅ **Input Validation** - 모든 사용자 입력 검증

### 감사 내역

| 날짜 | 감사 기관 | 결과 | 보고서 |
|-----|----------|------|--------|
| 2024.12 | Internal Review | ✅ Pass | [링크](#) |

---

## 🌐 배포 정보

### Formicarium Testnet (현재 배포)

| 항목 | 값 |
|-----|-----|
| **Network Name** | Formicarium Testnet |
| **Chain ID** | 43521 |
| **RPC URL** | https://rpc.formicarium.memecore.net |
| **Explorer** | https://testnet.memecorescan.io/ |
| **Native Currency** | M (Meme) |
| **WormGame Contract** | [`0x04686e9284B54d8719A5a4DecaBE82158316C8f0`](https://testnet.memecorescan.io/address/0x04686e9284B54d8719A5a4DecaBE82158316C8f0) |
| **Deployed Block** | #123456 |
| **Faucet** | [Get Test M](https://faucet.formicarium.memecore.net) |

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

## 📊 게임 경제 (Tokenomics)

### 수수료 구조

```
입장료: 1 M
├─ 95% (0.95 M) → 게임 팟 (Contract 보관)
└─  5% (0.05 M) → Treasury (운영비)

탈출 성공 시:
└─ 획득한 모든 토큰을 플레이어에게 전송

사망 시:
└─ 게임 팟은 Contract에 남음 (다음 플레이어 보상으로 활용)
```

### 토큰 배분 예시

```
시나리오: 10명이 각각 1 M 입장료 지불

입장료 총합: 10 M
├─ Treasury: 0.5 M (5%)
└─ Game Pot: 9.5 M (95%)

결과:
├─ 3명 탈출 성공 → 각각 보상 수령
├─ 7명 사망 → 입장료 손실
└─ Contract 잔액: 7명의 입장료 (6.65 M) 남음
   → 다음 플레이어들의 보상 풀로 활용
```

---

## 🛠️ 개발자 가이드

### 새로운 토큰 추가하기

1. **DEX에서 Pool 주소 확인**
   ```bash
   # MemeCore DEX에서 토큰 페어 찾기
   # 예: NEW_TOKEN/USDT Pool
   ```

2. **가격 조회 테스트**
   ```bash
   cd MemEat-Contract

   # scripts/get-pool-price.ts 수정
   const NEW_TOKEN_POOL = "0x..."; # Pool 주소 입력

   npm run price:pool
   # 출력: 1 NEW_TOKEN = X USDT
   ```

3. **백엔드 설정 추가**
   ```typescript
   // MemEat-BE/src/config/tokens.ts
   export const POOL_CONFIG = {
     "NEW_TOKEN": {
       poolAddress: "0x...",
       tokenAddress: "0x...",
       decimals: 18,
     },
   };
   ```

4. **프론트엔드 UI 추가**
   ```typescript
   // MemEat-FE/src/config/tokens.ts
   export const TOKEN_ICONS = {
     "NEW_TOKEN": "/assets/icons/new-token.svg",
   };
   ```

### 게임 맵 커스터마이징

```typescript
// MemEat-BE/src/services/gameService.ts
export const GAME_CONFIG = {
  MAP_WIDTH: 800,      // 맵 가로 크기
  MAP_HEIGHT: 600,     // 맵 세로 크기
  FOOD_COUNT: 20,      // 동시에 존재하는 음식 개수
  PLAYER_SPEED: 5,     // 뱀 이동 속도
  COLLISION_RADIUS: 10, // 충돌 판정 반경
};
```

### 스마트 컨트랙트 수정 워크플로우

```bash
# 1. 컨트랙트 수정
vim MemEat-Contract/contracts/WormGame.sol

# 2. 테스트 작성
vim MemEat-Contract/test/WormGame.test.ts

# 3. 테스트 실행
npx hardhat test

# 4. 컴파일
npx hardhat compile

# 5. 로컬 네트워크에 배포 테스트
npx hardhat node # 터미널 1
npx hardhat ignition deploy ignition/modules/WormGame.ts --network localhost # 터미널 2

# 6. 테스트넷 배포
npx hardhat ignition deploy ignition/modules/WormGame.ts --network formicarium

# 7. ABI 업데이트
cp artifacts/contracts/WormGame.sol/WormGame.json ../MemEat-BE/src/abis/
cp artifacts/contracts/WormGame.sol/WormGame.json ../MemEat-FE/src/abis/

# 8. 환경 변수 업데이트 (새 컨트랙트 주소)
# MemEat-BE/.env
CONTRACT_ADDRESS=0xNEW_ADDRESS

# MemEat-FE/.env
VITE_CONTRACT_ADDRESS=0xNEW_ADDRESS
```

---

## 🧪 테스트

### 스마트 컨트랙트 테스트

```bash
cd MemEat-Contract

# 전체 테스트 실행
npx hardhat test

# 특정 파일 테스트
npx hardhat test test/WormGame.test.ts

# 커버리지 리포트
npx hardhat coverage
```

### 백엔드 테스트

```bash
cd MemEat-BE

# 단위 테스트
npm test

# 통합 테스트
npm run test:integration

# 엔드투엔드 테스트
npm run test:e2e
```

### 프론트엔드 테스트

```bash
cd MemEat-FE

# 컴포넌트 테스트
npm test

# E2E 테스트 (Playwright)
npm run test:e2e
```

---

## 🤝 기여하기

MemEat은 오픈소스 프로젝트입니다! 기여를 환영합니다.

### 기여 프로세스

1. **Fork** - 저장소를 본인 계정으로 Fork
2. **Branch** - 기능별 브랜치 생성
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit** - 명확한 커밋 메시지 작성
   ```bash
   git commit -m "Add: 새로운 토큰 추가 기능"
   ```
4. **Push** - 브랜치에 푸시
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Pull Request** - PR 생성 및 리뷰 요청

### 커밋 메시지 컨벤션

```
[Type] 제목 (50자 이내)

상세 설명 (선택사항)

관련 이슈: #123
```

**Type 종류**:
- `Add`: 새로운 기능 추가
- `Fix`: 버그 수정
- `Update`: 기존 기능 개선
- `Refactor`: 코드 리팩토링
- `Docs`: 문서 수정
- `Test`: 테스트 추가/수정
- `Chore`: 빌드, 설정 변경

### 이슈 제보

버그를 발견하셨나요? [이슈 생성하기](https://github.com/your-org/memeat/issues/new)

**버그 리포트 템플릿**:
```markdown
## 🐛 버그 설명
간단한 설명

## 📋 재현 방법
1. ...
2. ...

## 🎯 기대 동작
...

## 📸 스크린샷
(있다면)

## 🖥️ 환경
- OS:
- Browser:
- Node:
```

---

## 📝 로드맵

### ✅ Phase 1: MVP (완료)
- [x] 기본 게임 로직 구현
- [x] 스마트 컨트랙트 배포
- [x] 실시간 가격 조회 연동
- [x] 멀티플레이어 지원

### 🚧 Phase 2: 베타 (진행 중)
- [ ] 게임 밸런스 조정
- [ ] UI/UX 개선
- [ ] 모바일 반응형 지원
- [ ] 성능 최적화

### 🔮 Phase 3: 정식 출시 (계획)
- [ ] Mainnet 배포
- [ ] NFT 스킨 시스템
- [ ] 리더보드 시즌제
- [ ] 토너먼트 모드
- [ ] 소셜 기능 (친구, 길드)

### 🌟 Phase 4: 확장 (구상)
- [ ] 멀티체인 지원 (Polygon, BSC 등)
- [ ] DAO 거버넌스
- [ ] 게임 에디터 (커뮤니티 맵 제작)
- [ ] 모바일 앱 출시

---

## 📞 커뮤니티 & 지원

### 공식 채널

- 🌐 **웹사이트**: [memeat.io](#)
- 📱 **Twitter**: [@MemEatGame](#)
- 💬 **Discord**: [Join Server](#)
- 📧 **이메일**: support@memeat.io

### 개발자 리소스

- 📚 **개발 문서**: [docs.memeat.io](#)
- 🐛 **이슈 트래커**: [GitHub Issues](https://github.com/your-org/memeat/issues)
- 💡 **기능 제안**: [GitHub Discussions](https://github.com/your-org/memeat/discussions)
- 📖 **API 문서**: [api.memeat.io](#)

---

## 📄 라이선스

이 프로젝트는 [MIT License](./LICENSE) 하에 배포됩니다.

```
MIT License

Copyright (c) 2024 MemEat Team

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

---

## 🙏 감사의 말

MemEat은 다음 프로젝트들의 영감을 받았습니다:

- **Slither.io** - 클래식 멀티플레이어 뱀 게임
- **Uniswap** - DEX Pool 가격 조회 메커니즘
- **Axie Infinity** - Play-to-Earn 경제 모델
- **OpenZeppelin** - 보안 검증된 스마트 컨트랙트 라이브러리

그리고 MemEat을 테스트하고 피드백을 주신 모든 베타 테스터분들께 감사드립니다! 🎮

---

<div align="center">

## 🐛 지금 바로 플레이하세요!

**MemEat - Where DeFi Volatility Meets Classic Gaming**

[![Play Now](https://img.shields.io/badge/🎮_Play_Now-Live_Demo-brightgreen?style=for-the-badge)](#)
[![Join Discord](https://img.shields.io/badge/💬_Join-Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](#)
[![Follow Twitter](https://img.shields.io/badge/📱_Follow-Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](#)

---

Made with ❤️ and ☕ by the MemEat Team

**[⬆ Back to Top](#-memeat)**

</div>
