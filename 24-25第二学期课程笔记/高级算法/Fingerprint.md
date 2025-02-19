## Fingerprint算法

1. Checksum校验和 ：将长字符串映射为短字符串

#### 如何判断两个多项式相同(在黑盒情况下)

1. **Methods**: Pick arbitrary distinct x, check if `f(x)=0`.

2. **polynomial interpolation**: Use polynomial interpolation to determine the polynomial(d interpolatin at least according to Fundamental Theorem of algebra)

3. **Fundamental Theorem of Algebra**: Any non-zero d-degree polynomail F has at most d roots

4. **roots**: also called **zero**, is member x of domain of F such that F(x) vanishes at x(F(x)=0)

5. **determine**: 也就是验证两个多项式是否相等，在S个区间中选d个随机数，检验两个多项式在这d个数上是否相等，如果全部相等那么这两个算法肯定相等；若两个多项式不相等，那么他们在这d个数上相等的概率小于d/|S|,当取`S=2d`时，则概率小于`1/2`(Fundamental Theorem of Algebra), 

#### 判断多项式相同的应用：一致性检查

1. **判断两个服务器上的数据是否一致**： 使用数据声称多项式，取一系列随机数并将计算结果发送给另一台服务器进行验证
    - **问题**： 计算结果太大，需要占用太多比特
    - **解决**： 
        1. 发送计算结果的模
        2. **pulic coin**: 发送生成随机数的种子以及计算结果的异或

以上我全都没懂...<br>

***

#### Multivariate Polynomial Identity Testing

1. 和单元多项式一样，只能使用随机算法，取d个数，检验两个多项式在这些数上是否取值相等，出错的概率小于`d/|S|`(According to Schwartz-Zippel Theorem)

