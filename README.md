# DNN_MP
DNN on Mobile Platforms - Good Reads

## Papers

### Survey

1. [Efficient Processing of Deep Neural Networks:A Tutorial and Survey](https://arxiv.org/pdf/1703.09039.pdf) [arXiv '17]

Lecture Slides: [Hardware architectures for DNN](http://www.rle.mit.edu/eems/wp-content/uploads/2017/03/Tutorial-on-DNN-CICS-MTL.pdf)

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


### CNN on embedded FPGAs

1. [Angel-Eye: A Complete Design Flow for Mapping CNN onto Customized Hardware] [ISVLSI '16]



2. [NEURAghe: Exploiting CPU-FPGA Synergies for Efficient and Flexible CNN Inference Acceleration on Zynq SoCs](https://arxiv.org/pdf/1712.00994.pdf) [TRETS '17]


3. [Going Deeper with Embedded FPGA Platform for Convolutional Neural Network](http://cadlab.cs.ucla.edu/~jaywang/papers/fpga16-cnn.pdf) [FPGA '16]
