# 3rd-party-miners
Mining software by @rserge for Qubic Solutions

# Requirements
- Ubuntu 22.04 (the others may work, but not tested)
- NVIDIA GPU (you may make it work with AMD or Intel with ZLUDA - https://github.com/vosen/ZLUDA ). Feel free to ask @rserge on Discord to help you.

# Installation
1) Install CUDA toolkit and driver:
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt-get update
sudo apt-get -y install cuda-toolkit-12-6 nvidia-open
```
2) Install other dependencies:
```
sudo bash -c "$(wget -O - https://apt.llvm.org/llvm.sh)"
sudo apt update
sudo apt install libjemalloc-dev libtbb-dev libomp-18-dev
```

# Running the stable miner
Run the miner like this, substituting your label and address:
```
# Solo mining
./qubic-pool-sat SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE false

# Share based mining (for slow GPUs) - NOT SUPPORTED AS OF 2024-12-04
./qubic-pool-sat SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE true
```

# Running the experimental miner
WARNING: it loses some solutions, and it loses even more shares. We advise it for solo mining rather than share-based mining.
Run the miner like this, substituting your label and address:
```
# Solo mining
./qubic-pool-cutoff SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE false

# Share based mining (for slow GPUs) - NOT SUPPORTED AS OF 2024-12-04
./qubic-pool-cutoff SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE true
```

# Installation on HiveOS:
Follow the CUDA instructions for Ubuntu 20.04:
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-keyring_1.1-1_all.deb
sudo dpkg -i cuda-keyring_1.1-1_all.deb
sudo apt-get update
sudo apt-get install cuda-toolkit-12-6 nvidia-open
```

# IDLE command
You need to provide the amount of work at once parameter, then the IDLE command. If your IDLE command contains arguments, you need to use quotes. Or consider writing a wrapper shell script which you can run without arguments. Below are a few examples:
```
# Experimental miner (now we know it loses 10-20% of solutions)
./qubic-pool-cutoff SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE false 5 IDLE_COMMAND

# Stable miner
./qubic-pool-sat SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE false 2 IDLE_COMMAND
```
Note that for the experimental miner, we run like 5 batches at once, while for a stable miner we run like 2 batches at once. This may affect the it/s, so you can experiment with this.
