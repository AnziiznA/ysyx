# Verilog 与 RISC-V CPU 实验（P1/P2）

路线：ALU → 寄存器堆 → 计数器/状态机 → 数据通路 → 单周期 CPU → 五级流水线 → cache。

## 工具链

- 仿真：Verilator 或 iverilog + GTKWave
- 语法参考：IEEE 1364 / SystemVerilog LRM、hdlbits.01xz.net（在线练习）

## 约定

- 每个实验独立目录，带仿真脚本和测试用例
- 模块必须能无稿讲清楚：输入、输出、时序、为什么这么写
- AI 生成的代码，合入前先读懂，并在工作记录里标注
