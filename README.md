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

# Share based mining (for slow GPUs)
./qubic-pool-sat SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE true
```

# Running the experimental miner
WARNING: it loses some solutions, and it loses even more shares. We advise it for solo mining rather than share-based mining.
Run the miner like this, substituting your label and address:
```
# Solo mining
./qubic-pool-cutoff SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE false

# Share based mining (for slow GPUs)
./qubic-pool-cutoff SARGEsLaptop4090 LVMMXNAABKUVYGFUSPUTVPVABARALIUZGNLQJZLXEEOAIKBNGDKUIZICAUFE true
```
