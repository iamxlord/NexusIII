### Nexus Prover Node:
``` Contribute Compute, Earn NEX Points ```

``` Become a vital part of the Nexus ecosystem by contributing your compute resources as a Prover Node! By doing so, you'll earn NEX Points, which track your valuable contributions. ```

**Why Run a Nexus Prover Node?**
 * Earn NEX Points: Your compute power directly translates into NEX Points, rewarding your participation.
 * Flexible Contribution: Use a variety of devices, including desktops, laptops, mobile phones, and Virtual Private Servers (VPS).
 * Centralized Management: Link and manage all your contributing devices from a single Nexus account.
 * Scalability: Run multiple prover nodes simultaneously, even on different browser tabs, to maximize your contributions.

### Get started with NEXUS
 * Create or login to your [Nexus Account](https://app.nexus.xyz/)
 * go to [nodes section](https://app.nexus.xyz/)

You can contribute to the Nexus ecosystem through two primary methods: via your web browser or via the Command Line Interface (CLI).

# Contribute via Web Browser (Easiest Method)
This is the simplest way to get started and is suitable for most users.
 * Log in to your dashboard: Go to https://app.nexus.xyz/ and log in to your Nexus account.
 * Start your node: On the dashboard, locate and click the "Start Node" button.
!note
 * You can run prover nodes on multiple browser tabs simultaneously.
 * This method works seamlessly on desktops, laptops.
 * More active computations mean more NEX Points for you.

# Contribute via CLI (Ubuntu PC/VPS)

System Recommendation:

 * RAM: 8GB or more
 * vCPU: 2 or more
 * Operating System: Ubuntu 24.04 (Older distro may encounter GLIBC compatibility issues.)

### Installation and Setup guide:
 * Install Dependencies:
  ```bash
sudo apt update && sudo apt upgrade -y
```
```bash
sudo apt install screen curl build-essential pkg-config libssl-dev git-all -y
sudo apt install protobuf-compiler -y
sudo apt update
```

 * Install Rust and its components:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
```bash
source $HOME/.cargo/env
```
```bash
rustup target add riscv32i-unknown-none-elf
```

 * Run the Prover:
   To ensure your prover continues running even if your terminal session closes, use screen:
   * Start a new screen session:
```bash
screen -S nexus
```

   * Install and run the Nexus Prover:
```bash
curl https://cli.nexus.xyz/ | sh
```

   * Run with an existing Node ID (if you have one):
```bash
source ~/.bashrc
nexus-network start --node-id my-node-id
```
* [!Note] You'll replace my-node-id with your node ID

### Creating a Node ID
***
You'll need a unique Node ID to link your CLI-based prover to your Nexus account. You have two options:
Create Node ID via Web:
***
 * Go to https://app.nexus.xyz/nodes.
 * Click Add Node, then Add CLI Node.
 * Copy the generated node-id and go back to the previous step
Create Node ID via CLI:
 * Register your wallet address:
```bash
source ~/.bashrc
nexus-network register-user --wallet-address your-wallet-address
```

   * Replace your-wallet-address with the EVM wallet address you linked with your nexus account:
 * Create your Node ID:
```bash
nexus-network register-node
```
 * Run your node with the newly created ID
```bash
nexus-network start --node-id your-node-id
```
```Replace your-node-id with the ID generated in the previous step.```

# Managing your Screen sessions:
screen is a powerful tool for managing multiple terminal sessions.

Minimize the screen (detach): ```CTRL+A+D``` (This allows the process to continue running in the background.)
 * To return to your screen session: ```screen -r nexus``` (Replace nexus with the name of your screen session)
 * Kill a screen session: ```screen -XS nexus quit``` (Replace nexus with the name of the session you want to terminate.)

```Running Multiple CLI Nodes to Earn More NEX```
```You can significantly increase your NEX Points by running multiple CLI nodes on the same server, provided your system resources can handle it. To do this, create separate screen sessions for each node.```
To create a second Node on your machine
 * Create a second screen session:
```bash
screen -S nexus2
```
 * Create another Node ID:
```bash
nexus-network register-node
```
 * Run the second Node with its new ID:
   nexus-network start --node-id your-node-id

   * Replace your-node-id with the newly created ID for this second node.



Monitoring System Resources
> [!Note] It's crucial to monitor your server's RAM and CPU usage to determine how many nodes your system can comfortably run.

 * Install htop (if not already installed):
```bash
sudo apt install htop
```

 * Run htop:
```bash
   htop
```
CLTR + C to exit

htop provides a dynamic, real-time view of your system's processes and resource consumption.
