# BT-BNN

The topology of biological brains is a key evolutionary indicator for biological intelligence. Some key functional circuits borrowed from the biological brain have been well applied to many artificial neural networks (ANNs), such as convolutional kernels and sparse recurrent loops. However, the compromise of evolution leaves many redundant parameters (brain regions and connections), which causes the direct copy of a brain topology to ANNs might not cause an immediate improvement. Here we propose a brain-like topology (BT) to represent the key network features of the biological brain. The detailed process of generating and applying a BT on biologically-plausible neural networks (BNNs) contains three steps. First, three important BTs covering cognitive functions of sensation, memory, and motor are hierarchically clustered from a whole mouse brain network (the Allen Mouse Brain Atlas). Second, these BTs are copied directly to the BNNs containing leaky-and-integrated neurons, and the connectivity strengths are then modified with the adaptive random search algorithm. Third, the proposed BT improved BNN (BT-BNN) was tested on four Open-AI benchmark reinforcement learning (RL) tasks. The experimental results showed that three BT-BNNs performed differently, but all achieved higher average rewards than BNNs using a random topology and other state-of-the-art ANNs, including long-short-term memory and multi-layer perception. We think borrowing biological structures in more smart ways for artificial and spiking neural networks has much in store for the future.

# preparatory work
First you need to install the Reinforcement Learning environments: [Open-AI Gym](https://www.gymlibrary.dev/) [Roboschool](https://github.com/openai/roboschool) and [mujoco-py](https://github.com/openai/mujoco-py)  
Next you need to compile the pybnn library (simulates neuronal circuits using C++) and copy the shared object to each of the local working directories. You have to install python-boost:  
```Bash
sudo apt-get install libboost-python-dev  
```
and then compile and copy the library:  
```Bash
cd pybnn  
make  
cp bin/pybnn.so ../humanoid/  
cp bin/pybnn.so ../humanoidstandup/  
cp bin/pybnn.so ../mountaincar/  
cp bin/pybnn.so ../half_cheetah/  
```

# Verifying
To check if the toolchain is working as intended you can execute a learned neuronal policy:
```Bash
cd mountaincar/
python3 mountaincar-net46.py --file 46-optimized.bnn
```
or  
```Bash
cd halfcheetah/
python3 halfcheetah-net46.py --file 46-optimized.bnn
```
or  
```Bash
cd humanoid/
python3 humanoid-net46.py --file 46-optimized.bnn
```
or  
```Bash
cd humanoidstandup/
python3 humanoidstandup-net46.py --file 46-optimized.bnn
```

# training
```Bash
cd humanoidstandup/
python3 humanoidstandup-net46.py --optimized --file 46.bnn 
```
