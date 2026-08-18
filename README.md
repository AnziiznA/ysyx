# ysyx：一生一芯预学习仓库

目标：去中科院计算所学习 CPU 设计，走“一生一芯”官方路径（[ysyx.org](https://ysyx.org)）。

- 近端验收：通过“一生一芯”预学习 + 预学习答辩
- 远端验收：独立实现一个能跑的小 RISC-V 处理器（流水线 + 简单 cache），冲 A 阶段指标

## 目录结构

```text
.
├── C/            # P0 地基：C 语言练习
├── verilog/      # P1/P2：Verilog 实验与 RISC-V CPU
├── docs/         # 学习计划与资料
├── worklog/      # 每 1–3 天一条工作记录
└── README.md
```

## 学习计划

见 [docs/learning-plan.md](docs/learning-plan.md)，工作区 issue **ICTCAS-3** 同步跟踪，每阶段有可勾选清单。

## AI 使用边界

1. AI 能查概念、读报错、解释代码、生成片段；不能整模块代写
2. 合入 AI 代码前必须自己读懂，每周组会能无稿讲清自己写的每个模块
3. 每 1–3 天一条工作记录，AI 参与的部分标注并自己复述

## 资源

- 《CPU设计实战》（LoongArch 版）：Verilog + FPGA 实操
- 胡伟武《计算机体系结构》：系统教材
- RISC-V Unprivileged Spec（RV32I）
- 工具链：Verilator / iverilog + GTKWave；Git
- 换电脑？看 [docs/SETUP-Windows11.md](docs/SETUP-Windows11.md)（Windows 11 配置清单）
