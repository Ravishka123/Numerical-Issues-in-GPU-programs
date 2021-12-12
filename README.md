# A Comprehensive Study on Numerical Issues in GPU Programs

## INTRODUCTION

Numerical applications relies on floating point arithmetic. Floating point numbers are an approximation of real
numbers that follows the IEEE 754 standard floating point format for half, single, and double precision levels.
Applications from several fields including scientific computing, machine learning, earth sciences, graphics, engineering, and finance widely use the floating point arithmetic. However, developers and researchers consider
about the speed up of the applications. Therefore, general purpose graphics processing unit (GPGPU) computing has become a major parallel computing paradigm which supports data parallelism. The data parallelism
helps the programs to execute a single instruction stream on many data elements at the same time. Therefore,
GPUs have the ability to perform a massive number of floating-point calculations per second which improves the
speed up and the efficiency of the programs compared to the CPU programs due to the massive multi-threaded
nature of the GPU hardware.

The general-purpose GPU programming facilitates extraordinary computing power because of the amount
of parallelism available in GPUs to execute applications quickly. GPUs facilitate the ability to compute floating
point operations and produce significant results in a short period of time. Therefore, the capabilities of NVIDIA
GPUs [15] have been expanded in each hardware generation from only supporting single precision in early
NVIDIA architectures, to fully supporting IEEE half, single, double precision, and including FMA (FusedMultiply-Add) [13] operations in modern generations such as Fermi [12] and Kepler [14] GPUs. According to
the evolution of CUDA [3], compute capability below 1.2 only supports single precision floating point arithmetic,
compute capability 1.3 supports both single and double precision arithmetic, and offers double-precision FMA
operations, and compute capability 2.0 and above fully support IEEE compliance. At present, GPUs support
both mixed precision computing [25]. Multi-precision computing uses processors that are capable of calculating
at different precision such as, using double precision when needed, and relying on half- or single-precision
arithmetic for other parts of the application. Mixed-precision computing uses different precision levels within a
single operation to achieve computational efficiency without sacrificing accuracy [25].

Even though, the traditional CPU programming and GPU programming both follows the standard IEEE 754 format for floating point computations, there are differences in terms of floating point computation, accuracy, and performance of the computations between the CPU and the GPU. First, CPUs tend to do floating point calculations in 80-bit ‘extended’ mode while GPUs use 32 bit and 64 bits for single and double precision respectively. [6]. Therefore, different architectures such as x64 and x86, support different levels of precision and rounding under different conditions such as compiler flags [7]. The figure 2 provides some CUDA compiler intrinsics on floating point arithmetic computation. The GPUs support all four rounding modes defined by the IEEE 754. According to Whitehead et al. [39], NVIDIA GPUs differ from the x86 architecture in that rounding modes are encoded within each floating point instruction instead of dynamically using a floating point control word. Exception handlers for floating point exceptions are not supported. There is no status flag to indicate when calculations have overflowed, underflowed, or have involved inexact arithmetic on the GPU. Also, GPUs may produce slightly different results due to the multi threaded environment when the floating point operations run in different orders from one iterations to the other. The race conditions occur during the execution of GPUs is a reason to produce different results. However, the performance of GPU programs degrades when using higher precision such as double values. The CPU to GPU memory transfers and GPU memory allocations take longer time to allocate higher precision numbers. An instances of this issue is addressed in the NVIDIA’s deep learning documentation [2] when half precision (FP16) data compared to higher precision such as single precision (FP32) and double precision (FP64) reduces memory usage of the neural network, allowing training and deployment of larger networks, and FP16 data transfers take less time than FP32 or FP64 transfers in GPU programs. However, CPU programs do not encounter such performance issues. On the other hand, single precision floating point computing, 1) uses less memory, therefore, the data can be transferred into the device faster 2) has less accuracy, therefore, approximations can be used for faster calculations compared to double precision computing. According to Shehzan et al. [32] there is no perfect solution to the problem of choosing between FP32 and FP64 in GPU computing and applications like physics modelling and simulation, high accuracy financial computations etc which call for double precision accuracy at high performance require capable FP64 cards while applications such as image and video processing, signal processing, statistics may not require such high precision and can get away with high FP32 performance only. Therefore, the limitation on floating point arithmetic, and current issues on improving the memory transfers, memory allocations, compiler flags, and performance in the GPU need more addressing to improve the application’s productivity.

![This is an image](https://github.com/Ravishka123/Numerical-Issues-in-GPU-programs/blob/main/Resources/Figure1.JPG)
