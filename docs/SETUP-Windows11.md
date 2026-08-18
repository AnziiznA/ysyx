# Windows 11 新电脑配置清单

换电脑后照着这份做，三分钟回到正轨。代码全在 GitHub，新机器上只需要：拉代码 + 配一次身份 + 装工具链。

## 两条路线怎么选

- **路线 A（推荐）：WSL2 + Ubuntu** —— 和 Linux 环境完全一致，Verilator 等仿真工具最省心，一生一芯的工具链基本都是 Linux 优先
- **路线 B：原生 Windows** —— 不想碰 WSL 就用这条，Git、gh、iverilog、GTKWave 都有 Windows 版

---

## 路线 A：WSL2 + Ubuntu（推荐）

1. 打开 PowerShell（管理员），运行：

   ```powershell
   wsl --install
   ```

   重启电脑，然后安装 Ubuntu：

   ```powershell
   wsl --install -d Ubuntu
   ```

2. 打开 Ubuntu 终端（开始菜单搜 “Ubuntu”），先更新再装工具：

   ```bash
   sudo apt update
   sudo apt install -y git build-essential verilator iverilog gtkwave gh
   ```

3. 拉代码 + 配置身份（一次）：

   ```bash
   git clone https://github.com/AnziiznA/ysyx
   cd ysyx
   gh auth login
   ```

   `gh auth login` 时选：GitHub.com → HTTPS → 用浏览器登录即可，之后推拉都不用再输密码。

4. 日常就在 Ubuntu 终端里开发。Windows 文件在 `/mnt/c/...` 下可以访问，但**代码请放在 WSL 自己的目录里**（性能和权限都更稳）。

---

## 路线 B：原生 Windows

1. 安装 Git 和 GitHub CLI（PowerShell）：

   ```powershell
   winget install --id Git.Git
   winget install --id GitHub.cli
   ```

   装完**重开终端**，然后：

   ```powershell
   gh auth login
   git clone https://github.com/AnziiznA/ysyx
   cd ysyx
   ```

2. C 编译器（二选一）：

   - 装 [MSYS2](https://www.msys2.org)，在 MSYS2 终端里：
     ```bash
     pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-gdb
     ```
   - 或装 Visual Studio Build Tools（含 MSVC）

3. 仿真工具（Windows 原生版）：

   - iverilog：官网下载 Windows 安装包安装
   - GTKWave：官网下载 Windows 安装包安装
   - Verilator：Windows 原生支持较折腾，**建议用到它时切到 WSL2**（路线 A）

---

## 换机注意事项

- **不要复制 token 到新电脑**：每台新机器跑一次 `gh auth login` 就行，更安全
- 代码以 GitHub 为准：新机器第一件事就是 `git clone`，之后每次开工先 `git pull`
- 工作记录放仓库 `worklog/`，跟着代码走，换机器不丢
- 学习计划与勾选清单在工作区的 ICTCAS-3~7，云端保存，任何机器都能看

## 常见问题

- `git` 不是内部或外部命令 → 装了 Git for Windows 后要**重开终端**
- `wsl --install` 提示需要重启 → 重启后继续
- WSL 网络异常 → PowerShell 里 `wsl --shutdown` 后重新打开
- push 提示认证失败 → 先跑 `gh auth status` 确认登录状态
