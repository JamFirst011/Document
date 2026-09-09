## Osprey 

**Motivation**: 传统的`patch similarity`测试因为架构/优化器的不同，以及sematic similarity而很难判断目标代码是否添加了安全补丁(通过比较target和patched code的相似性)。而直接分析sematical的FIBER方式需要symbolic execution，成本过高，因此就有了Osprey

**工作流程**：输入：source patch源码及其binary code
    1. extractor：操作source patch的二进制码，用于确定source patch在binary code中对应的部分(具体到行号)
    2. **optimizer**：
        - 根据机器码生成IR表示，并构建CFG；
        - 根据extractor得到的位置，以及执行路径找出所有affected BB
        - 对BB内代码进行优化
        - 将BB切分为strand(追踪每一条数据流)，并将所有strand组合成为strand graph(将不同BB的同一strand连接，使得strand可以跨数据流，这也是Osprey的特色)
        - 将所有conditional jump或BB内最后一条语句作为root IR，在graph中向前遍历，筛选出candidates strands(目的是用条件跳转作为特征，找到所有可以代表patch语义的数据流)
        - 每一个strand生成一个 `patch signature`
    3. **matcher**: 操作target，将optimizer生成的signature和target进行比较
        - 汇编，构造CFG
        - Coarse BB filter: 根据optimizer筛选出的BB，在target中找到所有相似的BB(根据入度，出度，跳转方式)
        - 随后同样找出root IR并生成strand
        - 将strand和signature进行lexical compare进而得出结果

