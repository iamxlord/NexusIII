Nexus Prover Node: Contribute Compute, Earn NEX Points
Become a vital part of the Nexus ecosystem by contributing your compute resources as a Prover Node! By doing so, you'll earn NEX Points, which track your valuable contributions.
Why Run a Nexus Prover Node?
 * Earn NEX Points: Your compute power directly translates into NEX Points, rewarding your participation.
 * Flexible Contribution: Use a variety of devices, including desktops, laptops, mobile phones, and Virtual Private Servers (VPS).
 * Centralized Management: Link and manage all your contributing devices from a single Nexus account.
 * Scalability: Run multiple prover nodes simultaneously, even on different browser tabs, to maximize your contributions.
Getting Started
Create Your Nexus Account
The first step to becoming a Nexus Prover is to create an account:
 * Visit the Nexus Dashboard.
 * Follow the on-screen instructions to create your account and link it.
Once your account is set up, you'll be able to:
 * Track your earned NEX Points on the leaderboard.
 * Manage all your connected Prover Nodes in one convenient place.
Contribution Methods
You can contribute to the Nexus ecosystem through two primary methods: via your web browser or via the Command Line Interface (CLI).
Contribute via Web Browser (Easiest Method)
This is the simplest way to get started and is suitable for most users.
 * Log in to your dashboard: Go to https://app.nexus.xyz/ and log in to your Nexus account.
 * Start your node: On the dashboard, locate and click the "Start Node" button.
That's it! Your browser will now begin contributing compute. Remember:
 * You can run prover nodes on multiple browser tabs simultaneously.
 * This method works seamlessly on desktops, laptops, and mobile phones.
 * More active computations mean more NEX Points for you.
Contribute via CLI (For Advanced Users - Ubuntu PC/VPS)
For users who prefer a more robust and dedicated setup, especially on VPS or Ubuntu machines, the CLI method offers greater control.
System Requirements:
Before you begin, ensure your system meets these specifications:
 * RAM: 8GB or more
 * vCPU: 2 or more
 * Operating System: Ubuntu 24.04 (Older distributions may encounter GLIBC compatibility issues.)
Installation and Setup:
 * Install Dependencies:
   sudo apt update && sudo apt upgrade -y
sudo apt install screen curl build-essential pkg-config libssl-dev git-all -y
sudo apt install protobuf-compiler -y
sudo apt update

   Install Rust and its components:
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustup target add riscv32i-unknown-none-elf

 * Run the Prover:
   To ensure your prover continues running even if your terminal session closes, use screen:
   * Start a new screen session:
     screen -S nexus

   * Install and run the Nexus Prover:
     curl https://cli.nexus.xyz/ | sh

   * Run with an existing Node ID (if you have one):
     source ~/.bashrc
nexus-network start --node-id your-node-id

     * Note: You'll replace your-node-id with an ID obtained in the next step.
Creating a Node ID
You'll need a unique Node ID to link your CLI-based prover to your Nexus account. You have two options:
Create Node ID via Web:
 * Go to https://app.nexus.xyz/nodes.
 * Click Add Node, then Add CLI Node.
 * Copy the generated node-id and paste it into your terminal when running the prover.
Create Node ID via CLI:
 * Register your wallet address:
   source ~/.bashrc
nexus-network register-user --wallet-address your-wallet-address

   * Replace your-wallet-address with your EVM compatible wallet address.
 * Create your Node ID:
   nexus-network register-node

 * Run your node with the newly created ID:
   nexus-network start --node-id your-node-id

   * Replace your-node-id with the ID generated in the previous step.
Running Multiple CLI Nodes to Earn More NEX
You can significantly increase your NEX Points by running multiple CLI nodes on the same server, provided your system resources can handle it. To do this, create separate screen sessions for each node.
Example: Creating a Second Node
 * Create a second screen session:
   screen -S nexus2

 * Create a second Node ID:
   nexus-network register-node

 * Run the second Node with its new ID:
   nexus-network start --node-id your-node-id

   * Replace your-node-id with the newly created ID for this second node.
Managing Your screen Sessions
screen is a powerful tool for managing multiple terminal sessions.
 * Minimize the screen (detach): CTRL+A+D (This allows the process to continue running in the background.)
 * Return to a screen session: screen -r nexus (Replace nexus with the name of your screen session, e.g., nexus2.)
 * Kill a screen session: screen -XS nexus quit (Replace nexus with the name of the session you want to terminate.)
Monitoring System Resources
It's crucial to monitor your server's RAM and CPU usage to determine how many nodes your system can comfortably run.
 * Install htop (if not already installed):
   sudo apt install htop

 * Run htop:
   htop

   htop provides a dynamic, real-time view of your system's processes and resource consumption.
Troubleshooting
GLIBC_2.39 Version Not Found Error
You might encounter an error like: nexus-network: /lib/x86_64-linux-gnu/libc.so.6: version 'GLIBC_2.39' not found (required by nexus-network)
This typically means your Ubuntu distribution's GLIBC version is older than what Nexus requires.
 * Confirm your installed GLIBC version:
   ldd --version

   If it's not 2.39 or higher, proceed with the following steps.
 * Install necessary dependencies:
   sudo apt update
sudo apt install -y gawk bison gcc make wget tar

 * Download GLIBC 2.39:
   wget -c https://ftp.gnu.org/gnu/glibc/glibc-2.39.tar.gz
tar -zxvf glibc-2.39.tar.gz
cd glibc-2.39

 * Create a build directory:
   mkdir glibc-build
cd glibc-build

 * Build GLIBC:
   ../configure --prefix=/opt/glibc-2.39
make -j$(nproc)
sudo make install

   cd

 * Run Nexus with the newly installed GLIBC:
   Instead of simply running nexus-network command, you'll need to specify the path to the newly installed GLIBC libraries.
   For example, when registering a user:
   /opt/glibc-2.39/lib/ld-linux-x86-64.so.2 --library-path /opt/glibc-2.39/lib:/lib/x86_64-linux-gnu:/usr/lib/x86_64-linux-gnu /root/.nexus/bin/nexus-network register-user --wallet-address your-wallet-address

   Note: The path /root/.nexus/bin/nexus-network might vary. To find your correct nexus-network directory, run these commands:
   source ~/.bashrc
which nexus-network

   Then, replace /root/.nexus/bin/nexus-network in the example command with the output from which nexus-network.
