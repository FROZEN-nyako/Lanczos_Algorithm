# Lanczos Algorithm

## English Instruction Document

The program provides an implementation of the Lanczos algorithm and employs MPI to perform parallel computation on multiple CPUs, reducing the actual runtime of the codes. The Lanczos algorithm is well-suited for finding the lowest few eigenstates of large sparse matrices, which has many applications in physics.

The inputs of the program are as follows:

1. A $\texttt{scipy}$ sparse matrix in $\texttt{csr}$ format, $M$;
2. The desired number of iterations, $m$ (in this program, for a $3000000 \times 3000000$ matrix, $2000$ iterations can converge approximately $27$ eigenstates);
3. The desired number of eigenstates to output, $n$ (depending on $m$, it may also output unconverged states);
4. A parameter $interval$ for demonstration of convergence, e.g., if this parameter is set to $50$ and $2000$ iterations are performed, the current eigenvalues and corresponding residuals will be displayed every 50 iterations, for a total of 20 displays.

The outputs of the program are as follows:

1. $n$ eigenvalues;
2. $n$ corresponding eigenstates;
3. $n$ corresponding residuals;
4. Time spent on matrix-vector multiplication in the Lanczos algorithm;
5. Time spent on Gram-Schmidt orthogonalization in the Lanczos algorithm (in principle, the runtime of the algorithm consists only of these two parts, but some time is used for inter-process communication, so the total runtime is longer than the sum of the two).
   
Two functions, $\texttt{LanczosAlgorithm}$ and $\texttt{LanczosAlgorithmC}$, are provided depending on whether the matrix is real symmetric or complex Hermitian.

## 中文说明文档

本程序提供了 Lanczos 算法的一个实现，并利用 MPI 在多个 CPU 上进行并行计算来减少代码的实际运行时间。Lanczos 算法适合用来寻找大型稀疏矩阵的特征值最小的几个特征向量，这在物理上有许多应用。

本程序的输入如下：

1. 一个 $\texttt{scr}$ 格式的 $\texttt{scipy}$ 稀疏矩阵 $M$；
2. 希望的迭代次数 $m$（就本程序而言，对于一个 $3000000 \times 3000000$ 矩阵， $2000$ 次迭代能收敛约 $27$ 个特征向量）；
3. 希望输出的特征向量的个数 $n$（取决于 $m$，也可能输出未收敛的向量）；
4. 一个用于展示收敛性的参数 $interval$，例如，若将此参数设为 $50$，并进行 $2000$ 次迭代，则会每隔 $50$ 次迭代展示一次当前得到的特征值和相应的残差，共展示 $20$ 次。

本程序的输出如下：
1. $n$ 个特征值；
2. $n$ 个相应的特征向量；
3. $n$ 个相应的残差；
4. Lanczos 算法执行矩阵-向量乘法的时间；
5. Lanczos 算法执行 Gram-Schmidt 正交化的时间（原则上算法的运行时间只由这两部分组成，但是一部分时间被用于进程间通讯，因此算法的总时间比两者之和长）。

提供了两个函数 $\texttt{LanczosAlgorithm}$ 和 $\texttt{LanczosAlgorithmC}$，取决于矩阵是实对称矩阵还是复厄米矩阵。
