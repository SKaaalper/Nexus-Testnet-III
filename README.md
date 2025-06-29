# Nexus Incentivized Testnet III — Prover-Node Setup

![image](https://github.com/user-attachments/assets/2fd0802e-d029-44a5-a309-4cc35152810a)

### Testnet III will be live until the Nexus Mainnet launch later in Q3 2025. This means that, unlike past Nexus testnets, participants in every country will have weeks, not days, to contribute to the Nexus supercomputer and earn rewards.

# Table Of Contents:
  - [Hardware requirements](https://github.com/SKaaalper/Nexus-Testnet-III?tab=readme-ov-file#nexus-prover-node--recommended-hardware-requirements)
  - [VPS Suggestion](https://github.com/SKaaalper/Nexus-Testnet-III?tab=readme-ov-file#vps-suggestions)
  - [Run Node](https://github.com/SKaaalper/Nexus-Testnet-III?tab=readme-ov-file#run-the-auto-installer)
  - [Add More NODE via Screen](https://github.com/SKaaalper/Nexus-Testnet-III?tab=readme-ov-file#if-you-want-to-add-more-nodes)
  - [Manage your NODE](https://github.com/SKaaalper/Nexus-Testnet-III?tab=readme-ov-file#monitor-or-manage-nodes)
  - [Update your Node](https://github.com/SKaaalper/Nexus-Testnet-III?tab=readme-ov-file#update-your-node-to-stay-in-sync-and-continue-participating)
  - [FIX GLIBC 2.39 ISSUE](https://github.com/SKaaalper/Nexus-Testnet-III?tab=readme-ov-file#full-commands-to-fix-glibc-239-issue)
  - [Need Help? Join TG Group](https://github.com/SKaaalper/Nexus-Testnet-III?tab=readme-ov-file#join-the-telegram-for-updates-and-help)

## Features:
- **Installs all required dependencies**
- **Supports 1 to 10 simultaneous nodes** `(recommended 1 Node ID : 1 VPS Server, if your server is low RAM)`
- **Automatically installs Rust, Nexus CLI, and `nexus-network`**
- **Launches multiple nodes in `screen` sessions** 

## 💻 Nexus Prover Node — Recommended Hardware Requirements

| **Component**    | **Minimum**              | **Recommended**              |
| ---------------- | ------------------------ | ---------------------------- |
| **CPU**          | **6 cores (x86\_64)**    | **8 cores or higher**        |
| **RAM**          | **12 GB**                | 12 GB or more                |
| **Disk Space**   | 10 GB SSD                | 20 GB SSD (NVMe if possible) |
| **Bandwidth**    | 5 Mbps (up/down)         | 10+ Mbps stable              |
| **OS**           | Ubuntu 22.04             | Ubuntu 24.04 LTS             |
| **Architecture** | x86\_64                  | x86\_64                      |
| **Other**        | Root access + open ports | VPS or Dedicated Server      |

<details>
<summary>⚠️ Memory Notice</summary>

✅ **12 GB of RAM** is now the safe minimum for running a Nexus Prover node without crashes.

You can run multiple nodes on one VPS/device, but not recommended unless you have enough RAM.  
If memory is too low, it may cause system crashes ❗❗  

💡 **More RAM = Higher Cycles/sec**

</details>

## 💡 VPS Suggestions:

| **Provider**       | **Plan Example**                              | **Meets 12GB RAM?** | **Notes**                          |
| ------------------ | --------------------------------------------- | ------------------- | ---------------------------------- |
| **Contabo VPS 30** | 6 vCPU / 12 GB RAM / 300 GB SSD for \~\$12/mo | ✅ Yes               | 💯 Recommended                     |
| Hetzner CPX41      | 8 vCPU / 16 GB RAM / 160 GB SSD               | ✅ Yes               | Excellent performance              |
| DigitalOcean       | 2 vCPU / 2–8 GB RAM                           | ❌ No                | Needs upgrade                      |
| Localhost (VM)     | Ubuntu VM on Home PC                          | ⚠️ Maybe            | Not reliable if uptime is unstable |


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

## Update your node to stay in sync and continue participating.

**How to Update**:

1. Delete old `screen`:
```
screen -XS nexus1 quit
```

2. Download and install the latest `CLI`:
```
curl https://cli.nexus.xyz/ | sh
```
```
source ~/.bashrc
```

3. Create new `screen`:
```
screen -S nexus1
```

4. Start your node again:
```
nexus-network start --node-id <your-node-id>
```
→ Get your `Node id` HERE: https://app.nexus.xyz/nodes

→ Make sure you replace `<your-node-id>` with your actual `Node ID`.

→ Monitor and Manage your `node`: [GO HERE](https://github.com/SKaaalper/Nexus-Testnet-III/blob/main/README.md#monitor-or-manage-nodes)

![image](https://github.com/user-attachments/assets/19232099-9b15-4c94-9cd5-5099c4b89e6f)

### FULL COMMANDS TO FIX `GLIBC 2.39` ISSUE.

1. Install required packages:
```
sudo apt update
sudo apt install -y gawk bison gcc make wget tar
```

2. Download GLIBC 2.39:
```
cd ~
wget -c https://ftp.gnu.org/gnu/glibc/glibc-2.39.tar.gz
tar -zxvf glibc-2.39.tar.gz
cd glibc-2.39
```

3. Create a build directory:
```
mkdir glibc-build
cd glibc-build
../configure --prefix=/opt/glibc-2.39
```

4. Compile and install (this will take time depending on CPU):
```
make -j$(nproc)
sudo make install
cd ~
```

5. Create screen session:
```
screen -S nexus1
```

6. Run the Nexus Node:
→  Replace `<your-node-id>` with your actual `node ID`:
```
/opt/glibc-2.39/lib/ld-linux-x86-64.so.2 \
--library-path /opt/glibc-2.39/lib:/lib/x86_64-linux-gnu:/usr/lib/x86_64-linux-gnu \
/root/.nexus/bin/nexus-network start --node-id <your-node-id>
```
→ Get your Node id HERE: https://app.nexus.xyz/nodes

→ Monitor and Manage your `node`: [GO HERE](https://github.com/SKaaalper/Nexus-Testnet-III/blob/main/README.md#monitor-or-manage-nodes)

- **More Info's** at [Official Docs](https://docs.nexus.xyz/layer-1/testnet/testnet-3)
- **Nexus Official** [Discord](https://discord.gg/zH7rdrt29E)
- **Nexus Official** [Twitter](https://x.com/NexusLabs)

## Join the Telegram for updates and help:
👉 [@KatayanAirdropGnC](https://t.me/KatayanAirdropGnC)
