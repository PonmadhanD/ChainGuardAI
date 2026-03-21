<div align="center">
  <h1>🦞 ChainGuard AI</h1>
  <p><strong>Your personalized, AI-powered onchain detective and assistant that learns and guards your crypto behavior.</strong></p>
  
  [![License](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
  [![Frontend](https://img.shields.io/badge/Frontend-Next.js-black?logo=next.js)](./client)
  [![Backend](https://img.shields.io/badge/Backend-Express.js-green?logo=nodedotjs)](./server)
  [![AI Agent](https://img.shields.io/badge/Agent-OpenClaw-orange)](#)
</div>

---

## 📖 Documentation

* [**Project Overview**](docs/PROJECT.md): Problem, solution, business impact, limitations & roadmap
* [**Technical Details**](docs/TECHNICAL.md): Architecture, setup instructions, demo guide
* [**Onchain Proof**](docs/ONCHAIN.md): Live smart accounts and transactions on BNB Chain
* [**AI Build Log**](docs/AI_BUILD_LOG.md): How AI tools were used to build ChainGuard AI
* [**Extras & Media**](docs/EXTRAS.md): Demo video, live demo links

---

## 🏗️ Project Structure

| Directory | What it does |
|-----------|--------------|
| 🌐 **`client/`** | **Next.js app**: User dashboard, send/receive tokens, WalletConnect DApp connectivity, activity logs, invoices, and settings. Proposes transactions and calls queue/execute endpoints. |
| ⚙️ **`server/`** | **Express API**: Handles inline risk analysis on `/queue`, auto-executes safe txs, Telegram notifications with interactive review, `/portfolio` via Zerion, and invoice queues. |
| 🤖 **`zhentan-skills/`** | **OpenClaw skills**: Custom AI logic to sign/execute, reject, deep-analyze (via GoPlus & Honeypot.is), record behavioral patterns, and queue invoices. |

---

## 🌟 What is ChainGuard AI?

ChainGuard AI is a personalized wallet assistant and onchain detective powered by an OpenClaw agent. It actively learns your unique transaction patterns—amounts, timing, recipients, and typical assets—and scores transaction risk in **real time**.

### Key Features:
- 🛡️ **Instant Screening:** Analyzes every pending transaction. Safe transactions (score < 40) are executed immediately. Suspicious transactions are blocked, whilst borderline transactions are sent to your Telegram for manual review.
- 🔌 **WalletConnect Support:** Connect to any external Web3 DApp (PancakeSwap, Uniswap, etc.). DApp requests flow securely through the exact same AI screening pipeline!
- 🔍 **Deep Analysis on Demand:** Ask your Telegram agent to run advanced security checks (GoPlus, Honeypot.is) on recipient addresses and tokens to avoid scams.
- 📈 **Portfolio Visibility:** See live token balances, prices, and 24-hour changes via Zerion API.
- 🎚️ **Screening Toggle:** Need to move fast? Turn the screening off anytime to enable full auto-execution.

Built on an industry-standard **Safe** smart account with a 2-of-2 multisig, Privy embedded wallets for seamless onboarding, and the AI agent as your designated co-signer. 

Enjoy **Zero gas fees** (ERC-4337 Account Abstraction), instant approvals for legitimate flows, and support for any ERC-20 token on BNB Chain! 

> 🌐 **Live demo:** Try non-screened transactions at [http://zhentan.me/](http://zhentan.me/). To experience the full AI screening, approval, review, and blocking mechanisms, please **run the app locally**!

---

## 🔄 How the Ecosystem Works

ChainGuard AI consists of three powerful tiers:

### 1. User-Facing App & Smart Account 👤
Users effortlessly onboard via Google Sign-In using Privy, receiving an automatic embedded wallet. Each user receives an ERC-4337 powered smart account configured as a 2-of-2 multisig. The dashboard displays portfolio balances and allows users to connect to DApps via WalletConnect.

### 2. Instant Risk Analysis Engine ⚡
When a transaction is queued, the server calculates a behavior-based Risk Score (0-100):
- 🟢 **APPROVE (< 40):** Server auto-signs and executes. No delay.
- 🟡 **REVIEW (40-70):** Sends a Telegram message with interactive Approve/Reject buttons.
- 🔴 **BLOCK (> 70):** Transaction is completely blocked for safety.

### 3. OpenClaw Conversational Agent 🤖
Powered by advanced LLMs (Qwen3-235B / Claude 3.5 Sonnet), the agent handles the Telegram interactions, manages deep security analysis requests, and directly interacts with the blockchain to sign and execute your approved transactions.

### 4. Gasless Execution on BNB Chain 🟡
Once approved, the completed UserOperation is sent to a **Pimlico Bundler** for gasless execution on the BNB Chain using Viem and Permissionless.js.
