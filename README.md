# DNN_MP
DNN on Mobile Platforms - Good Reads

## Papers

### Survey

1. [Efficient Processing of Deep Neural Networks:A Tutorial and Survey](https://arxiv.org/pdf/1703.09039.pdf) [arXiv '17]

Lecture Slides: [Hardware architectures for DNN](http://www.rle.mit.edu/eems/wp-content/uploads/2017/03/Tutorial-on-DNN-CICS-MTL.pdf)

Opportunities for innovation


Algorithmic Optimizations 

     - Kernel Computation - Convert convolutional operation to multiplication
     
     - Computational Transforms 
     
          - Reducing Multiplications
                - Gauss's multiplication algorithm
                - Strassen
                - Winograd 1D  - 36 multi> 16 multi
                
          - FFT
               - Convert conv O(N0^2 Nf^2) -> O(N0^2 logN0) - reduce computation but requires much more mem space and bandwidth  
               
          - cuDNN
           
Solve Memory access bottlenecks

     - Data reuse
          - Convolutional reuse, Fmap reuse, filter reuse
          
     - Local Accumulation

DNN Model and hardware co-design

     - Reduce size of operands for storage/ compute
          - Floating point -> Fixed point
          - Bit width reduction
          - Non-linear quantization
          
     - Reduce Number of operations for storage/ compute
          - Exploit activation statistics (Compression)
          - Network pruning
          - Compact network architectures - break large convolution layers into series of small convolutional layers
          
### CNN on embedded FPGA platforms

1. [Angel-Eye: A Complete Design Flow for Mapping CNN onto Customized Hardware] [ISVLSI '16]

       - Fixed point implementation 
       - Quantization startegy - the best radix position of the fixed point data in each layer is chosen differently
       - But fixed point adders and multipliers remain unchanged
       - Runtime configurable hardware architecture
       - Use caffe framework


2. [NEURAghe: Exploiting CPU-FPGA Synergies for Efficient and Flexible CNN Inference Acceleration on Zynq SoCs](https://arxiv.org/pdf/1712.00994.pdf) [TRETS '17]

       - Have Convolutional-Specific Processor(CSP) implemented on PL side
          -Convolutional Engine
          -Programmable soft core – manages the execution of complex CNN
       - 16 bit fixed point 
       - Used caffe framework
       - Frame rate – VGG-16 5.5 FPS and ResNet-18 6.6 FPS
       - Two CSPs can be fit into next generation Ultrascale+ SoCs


3. [Going Deeper with Embedded FPGA Platform for Convolutional Neural Network](http://cadlab.cs.ucla.edu/~jaywang/papers/fpga16-cnn.pdf) [FPGA '16]

### What's the best combination for mobile platforms? CPU + FPGA/ GPU/ CGRA/ ASIC?

1. Can FPGAs Beat GPUs in Accelerating Next-Generation Deep Learning?[News Article](https://www.nextplatform.com/2017/03/21/can-fpgas-beat-gpus-accelerating-next-generation-deep-learning/) [Paper published in ACM Digital Library, February 2017](http://delivery.acm.org/10.1145/3030000/3021740/p5-nurvitadhi.pdf?ip=137.132.228.29&id=3021740&acc=ACTIVE%20SERVICE&key=FF6731C4D3E3CFFF%2EBB5EB8D2067C1662%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35&__acm__=1523429071_8c3a5ebf30881b77de608f9f9131c1a9)  

FPGA 


     - Superior power efficiency
     - Customizability
         - DNN go deeper -> improved accuracy -> increase comp/mem bw/storage	
         - compact low precision data types  32>16>8>ter>binary
         - Introduce sparsity(the presence of zeros) > using pruning/ReLU
         - Low precision + sparsity > introduce irregular parallelism > difficult for GPU > can exploit extreme customizability of FPGAs

     - Bad floating-point performance – solution DSP and compact low precision data types

  “The current ML problems using 32-bit dense matrix multiplication is where GPUs excel. We encourage other developers and researchers to join forces with us to reformulate machine learning problems to take advantage of the strength of FPGAs using smaller bit processing because FPGAs can adapt to shifts toward lower precision,” 

2. Wave Dataflow Processing Engine [A Dataflow Processing Chip for Training Deep Neural Networks](https://www.hotchips.org/wp-content/uploads/hc_archives/hc29/HC29.22-Tuesday-Pub/HC29.22.60-NeuralNet1-Pub/HC29.22.610-Dataflow-Deep-Nicol-Wave-07012017.pdf)
     [Solving the Performance Challenge For Machine Learning Acceleration](https://www.sra.samsung.com/assets/AI-Summmit-2017/09.-Chris-Nicol-Solving-Performance-Challenge-for-ML-acceleration.pdf)

CGRA 
  
     – Wave DPU - targeting server based DNN training and inferencing     
          – very promising numbers for server based system 
          - Alex Net    inference in the rate of 962,000 fps

ASIC 

     – superior performance but become obsolete  


