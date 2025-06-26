# Nexus Incentivized Testnet-III — Prover-Node Setup

![image](https://github.com/user-attachments/assets/2fd0802e-d029-44a5-a309-4cc35152810a)

### Testnet III will be live until the Nexus Mainnet launch later in Q3 2025. This means that, unlike past Nexus testnets, participants in every country will have weeks, not days, to contribute to the Nexus supercomputer and earn rewards.

## Features:
- **Installs all required dependencies**
- **Supports 1 to 10 simultaneous nodes**
- **Automatically installs Rust, Nexus CLI, and `nexus-network`**
- **Launches multiple nodes in `screen` sessions**

## Nexus Prover Node — Recommended Hardware Requirements:

| Component        | Minimum                  | Recommended                  |
| ---------------- | ------------------------ | ---------------------------- |
| **CPU**          | 2 cores (x86\_64)        | 4 cores or higher            |
| **RAM**          | 2 GB                     | 4–8 GB                       |
| **Disk Space**   | 10 GB SSD                | 20 GB SSD (NVMe if possible) |
| **Bandwidth**    | 5 Mbps (up/down)         | 10+ Mbps stable              |
| **OS**           | Ubuntu 22.04             | Ubuntu 24.04 LTS             |
| **Architecture** | x86\_64                  | x86\_64                      |
| **Other**        | Root access + open ports | VPS or Dedicated Server      |

## VPS Suggestions:

| Provider          | Plan Example              | Meets Requirements?                   |
| ----------------- | ------------------------- | ------------------------------------- |
| **Contabo VPS S** | 4 vCPU / 8 GB / 50 GB SSD | ✅ Yes                                 |
| **Hetzner CX21**  | 2 vCPU / 4 GB / 40 GB SSD | ✅ Yes                                 |
| **DigitalOcean**  | 2 vCPU / 2 GB / 50 GB SSD | ⚠️ Minimum only                       |
| **Localhost**     | Home PC via Ubuntu VM     | ⚠️ Not recommended if unstable uptime |

## **Guide on How to buy VPS**: [Contabo](https://medium.com/@Airdrop_Jheff/guide-on-how-to-buy-a-vps-server-from-contabo-and-set-it-up-on-termius-0928e0e5cb5d)

## Run the Auto-Installer
Copy and paste the following one-liner to begin setup:
```
wget -q https://raw.githubusercontent.com/SKaaalper/Nexus-Testnet-III/main/nexus-prover-setup.sh && chmod +x nexus-prover-setup.sh && sudo ./nexus-prover-setup.sh
```
- Go to: https://app.nexus.xyz/nodes
- Click **"Add CLI Node"** in the dashboard to generate your `Node ID`.
  
![image](https://github.com/user-attachments/assets/5c184bfa-e426-4bd0-a255-06c36cf2df22)

## If you want to add more nodes
```
cd /root/nexus-prover
screen -dmS nexus3 bash -c "nexus-network start --node-id YOUR_NEW_NODE_ID"
```
- Change `nexus3`, `nexus4`, `nexus5`, `etc`., depending on the next available `screen` session number.
- Replace `YOUR_NEW_NODE_ID` with your actual `Node ID` from the **Nexus dashboard**.

## For Multi-Nodes:
- Each nexus-network instance (per node ID) may need 1–2 GB RAM.
- So for 5 nodes:
  - **CPU**: `4–6 vCores`
  - **RAM**: `6–10 GB` total
  - **Disk**: `15–25 GB`

🔔 Note:
**Avoid using duplicate `screen` session names to prevent conflicts that could stop or disable other running nodes.**

## Monitor or Manage Nodes:

| Action             | Command                     |
| ------------------ | --------------------------- |
| Detach session     | `CTRL+A` then `D`           |
| Reattach session   | `screen -r nexus1`          |
| Stop a node        | `screen -XS nexus1 quit`    |
| Remove setup files | `rm -rf /root/nexus-prover` |

![image](https://github.com/user-attachments/assets/3a9079c6-31b0-43d7-80a2-794be4def4b3)

## Update your node to version `v0.8.13` to stay in sync and continue participating.

**How to Update**:

1. Stop your current prover process (`q or Ctrl+C`)
or
Delete old `screen`:
```
screen -XS nexus1 quit
```

2. Download and install the latest `CLI`:
```
curl https://cli.nexus.xyz/ | sh
```

3. (Optional) Create new `screen`:
```
screen -S nexus1
```
→ **Note**: `If you only pressed Ctrl + C, there's no need to create a new screen session`.

4. Start your node again:
```
nexus-network start --node-id <your-node-id>
```
→ Get your `Node id` HERE: https://app.nexus.xyz/nodes

→ Make sure you replace `<your-node-id>` with your actual `Node ID`.

→ Monitor and Manage your `node`: [GO HERE](https://github.com/SKaaalper/Nexus-Testnet-III/blob/main/README.md#monitor-or-manage-nodes)

- **More Info's** at [Official Docs](https://docs.nexus.xyz/layer-1/testnet/testnet-3)
- **Nexus Official** [Discord](https://discord.gg/zH7rdrt29E)
- **Nexus Official** [Twitter](https://x.com/NexusLabs)

## Join the Telegram for updates and help:
👉 [@KatayanAirdropGnC](https://t.me/KatayanAirdropGnC)
