# Foundry 安装部署指南基础版 - V1

> **作者： RainWeb3**
> **更新时间：2025-10-27**
---

## 📚 文档目录

1. [第一步：安装 `foundryup`（只需一次）](#第一步安装-foundryup-只需一次)
2. [第二步：加载环境变量（只需一次）](#第二步加载环境变量-只需一次)
3. [第三步：运行 `foundryup` 下载 Foundry 工具](#第三步运行-foundryup-下载-foundry-工具)
4. [第四步：验证安装](#第四步验证安装)
5. [第五步：在项目中锁定版本](#第五步在项目中锁定版本)
6. [第六步：开发时切换到项目指定版本](#第六步开发时切换到项目指定版本)
7. [第七步：更新项目版本（可选）](#第七步更新项目版本可选)
8. [为什么这个方案“大多都在用”？](#为什么这个方案大多都在用)
9. [项目结构示例](#项目结构)
10. [各目录说明](#各目录说明)
11. [forge 常用命令详细表格](#forge常用命令详细表格)
12. [forge 按功能分类速查](#forge按功能分类速查)
13. [cast 常用子命令详细表格](#cast常用子命令详细表格)
14. [cast 按功能分类速查](#cast按功能分类速查)

---

## 第一步：安装 `foundryup`（只需一次）

```bash
# 下载并安装 foundryup（会自动装到 ~/.foundry/bin）
curl -L https://foundry.paradigm.xyz | bash
```

### 示例输出：
```bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   167  100   167    0     0    458      0 --:--:-- --:--:-- --:--:--   457
100  2200  100  2200    0     0   2303      0 --:--:-- --:--:-- --:--:--  2303
Installing foundryup...
```

> 🔹 **说明**：这是官方推荐的安装方式，安全可靠，无需 `sudo` 权限。  
> 🔹 所有文件仅写入用户目录 `~/.foundry/`，不会影响系统全局环境。

---

## 第二步：加载环境变量（只需一次）

安装完成后，需要将 `~/.foundry/bin` 加入 `PATH` 环境变量，并立即生效。

```bash
# 如果你使用 zsh（macOS 默认、大多数 Linux 用户）
source ~/.zshrc

# 如果你使用 bash
source ~/.bashrc
```

> 🔹 **作用**：让你可以在任意终端中直接使用 `forge`、`cast`、`anvil`、`chisel` 等命令。  
> 🔹 **提示**：后续新打开的终端会自动加载，无需重复执行。

---

## 第三步：运行 `foundryup` 下载 Foundry 工具

```bash
foundryup
```

### 示例输出：
```
.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx

 ╔═╗ ╔═╗ ╦ ╦ ╔╗╔ ╔╦╗ ╦═╗ ╦ ╦         Portable and modular toolkit
 ╠╣  ║ ║ ║ ║ ║║║  ║║ ╠╦╝ ╚╦╝    for Ethereum Application Development
 ╚   ╚═╝ ╚═╝ ╝╚╝ ═╩╝ ╩╚═  ╩                 written in Rust.

.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx

Repo       : https://github.com/foundry-rs/foundry
Book       : https://book.getfoundry.sh/
Chat       : https://t.me/foundry_rs/
Support    : https://t.me/foundry_support/
Contribute : https://github.com/foundry-rs/foundry/blob/master/CONTRIBUTING.md

.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx

foundryup: checking if foundryup is up to date...
foundryup: foundryup is up to date.
foundryup: installing foundry (version stable, tag stable)
foundryup: checking if forge, cast, anvil, and chisel for stable version are already installed
################################################################################################################################################ 100.0%
foundryup: downloading forge, cast, anvil, and chisel for stable version
################################################################################################################################################ 100.0%
forge
cast
anvil
chisel
foundryup: downloading manpages
################################################################################################################################################ 100.0%
foundryup: verifying downloaded binaries against the attestation file
foundryup: forge verified ✓
foundryup: cast verified ✓
foundryup: anvil verified ✓
foundryup: chisel verified ✓
foundryup: use - forge 1.4.3-stable (fa9f934bda 2025-10-22T05:31:43.173937269Z)
foundryup: use - cast 1.4.3-stable (fa9f934bda 2025-10-22T05:31:43.173937269Z)
foundryup: use - anvil 1.4.3-stable (fa9f934bda 2025-10-22T05:31:43.173937269Z)
foundryup: use - chisel 1.4.3-stable (fa9f934bda 2025-10-22T05:31:43.173937269Z)
```

> 🔹 `foundryup` 会自动下载并验证 `forge`、`cast`、`anvil`、`chisel` 等核心工具。  
> 🔹 所有二进制文件存放在 `~/.foundry/bin`，安全且易于管理。

---

## 第四步：验证安装

```bash
forge --version

# 示例输出：
forge Version: 1.4.3-stable
Commit SHA: fa9f934bdac4bcf57e694e852a61997dda90668a
Build Timestamp: 2025-10-22T05:31:43.173937269Z (1761111103)
Build Profile: maxperf
```

```bash
anvil --version

# 示例输出：
anvil Version: 1.4.3-stable
Commit SHA: fa9f934bdac4bcf57e694e852a61997dda90668a
Build Timestamp: 2025-10-22T05:31:43.173937269Z (1761111103)
Build Profile: maxperf
```

### 测试forge环境：
```bash
forge build

# 示例输出：
Warning: This is a nightly build of Foundry. It is recommended to use the latest stable version. To mute this warning set `FOUNDRY_DISABLE_NIGHTLY_WARNING` in your environment. 

Compiling 23 files with Solc 0.8.30
installing solc version "0.8.30"
Successfully installed solc 0.8.30
Solc 0.8.30 finished in 9.39s
Compiler run successful
```


```bash
forge test

# 示例输出：
Warning: This is a nightly build of Foundry. It is recommended to use the latest stable version. To mute this warning set `FOUNDRY_DISABLE_NIGHTLY_WARNING` in your environment. 

No files changed, compilation skipped

Ran 2 tests for test/Counter.t.sol:CounterTest
[PASS] testFuzz_SetNumber(uint256) (runs: 256, μ: 29133, ~: 29289)
[PASS] test_Increment() (gas: 28783)
Suite result: ok. 2 passed; 0 failed; 0 skipped; finished in 4.66ms (2.94ms CPU time)

Ran 1 test suite in 19.32ms (4.66ms CPU time): 2 tests passed, 0 failed, 0 skipped (2 total tests)
```


```bash
forge fmt

#示例输出：
Warning: This is a nightly build of Foundry. It is recommended to use the latest stable version. To mute this warning set `FOUNDRY_DISABLE_NIGHTLY_WARNING` in your environment. 
```

```bash
forge snapshot

#示例输出：
Warning: This is a nightly build of Foundry. It is recommended to use the latest stable version. To mute this warning set `FOUNDRY_DISABLE_NIGHTLY_WARNING` in your environment. 

No files changed, compilation skipped

Ran 2 tests for test/Counter.t.sol:CounterTest
[PASS] testFuzz_SetNumber(uint256) (runs: 256, μ: 28667, ~: 29289)
[PASS] test_Increment() (gas: 28783)
Suite result: ok. 2 passed; 0 failed; 0 skipped; finished in 3.05ms (2.36ms CPU time)

Ran 1 test suite in 15.57ms (3.05ms CPU time): 2 tests passed, 0 failed, 0 skipped (2 total tests)
```

```bash
anvil

#示例输出：

                             _   _
                            (_) | |
      __ _   _ __   __   __  _  | |
     / _` | | '_ \  \ \ / / | | | |
    | (_| | | | | |  \ V /  | | | |
     \__,_| |_| |_|   \_/   |_| |_|

    1.4.3-stable (fa9f934bda 2025-10-22T05:31:43.173937269Z)
    https://github.com/foundry-rs/foundry

Available Accounts
==================

(0) 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 (10000.000000000000000000 ETH)
(1) 0x70997970C51812dc3A010C7d01b50e0d17dc79C8 (10000.000000000000000000 ETH)
(2) 0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC (10000.000000000000000000 ETH)
(3) 0x90F79bf6EB2c4f870365E785982E1f101E93b906 (10000.000000000000000000 ETH)
(4) 0x15d34AAf54267DB7D7c367839AAf71A00a2C6A65 (10000.000000000000000000 ETH)
(5) 0x9965507D1a55bcC2695C58ba16FB37d819B0A4dc (10000.000000000000000000 ETH)
(6) 0x976EA74026E726554dB657fA54763abd0C3a0aa9 (10000.000000000000000000 ETH)
(7) 0x14dC79964da2C08b23698B3D3cc7Ca32193d9955 (10000.000000000000000000 ETH)
(8) 0x23618e81E3f5cdF7f54C3d65f7FBc0aBf5B21E8f (10000.000000000000000000 ETH)
(9) 0xa0Ee7A142d267C1f36714E4a8F75612F20a79720 (10000.000000000000000000 ETH)

Private Keys
==================

(0) 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
(1) 0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d
(2) 0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a
(3) 0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6
(4) 0x47e179ec197488593b187f80a00eb0da91f1b9d0b13f8733639f19c30a34926a
(5) 0x8b3a350cf5c34c9194ca85829a2df0ec3153be0318b5e2d3348e872092edffba
(6) 0x92db14e403b83dfe3df233f83dfa3a0d7096f21ca9b0d6d6b8d88b2b4ec1564e
(7) 0x4bbbf85ce3377467afe5d46f804f221813b2bb87f24d81f60f1fcdbf7cbf4356
(8) 0xdbda1821b80551c9d65939329250298aa3472ba22feea921c0cf5d620ea67b97
(9) 0x2a871d0798f97d79848a013d4936a73bf4cc922c825d33c1cf7073dff6d409c6

Wallet
==================
Mnemonic:          test test test test test test test test test test test junk
Derivation path:   m/44'/60'/0'/0/

Chain ID
==================

31337

Base Fee
==================

1000000000

Gas Limit
==================

30000000

Genesis Timestamp
==================

1761569019

Genesis Number
==================

0

Listening on 127.0.0.1:8545
```

```bash
forge script script/Counter.s.sol:CounterScript --rpc-url 127.0.0.1:8545 --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80

#示例输出：
[⠊] Compiling...
No files changed, compilation skipped
Script ran successfully.

## Setting up 1 EVM.

==========================

Chain 31337

Estimated gas price: 2.000000001 gwei

Estimated total gas used for script: 203856

Estimated amount required: 0.000407712000203856 ETH

==========================

SIMULATION COMPLETE. To broadcast these transactions, add --broadcast and wallet configuration(s) to the previous command. See forge script --help for more.

Transactions saved to: /home/test/foundry/foundry-temple-01/broadcast/Counter.s.sol/31337/dry-run/run-latest.json

Sensitive values saved to: /home/test/foundry/foundry-temple-01/cache/Counter.s.sol/31337/dry-run/run-latest.json
```

✅ **恭喜！你已成功安装 Foundry，可以开始 Solidity 开发了！**

---

## 第五步：在项目中锁定版本

为确保团队和 CI 环境使用一致的 Foundry 版本，建议在每个项目中创建 `.foundry-version` 文件。

```bash
# 进入你的项目目录
cd foundry-temple-01

# 初始化项目
forge init

# 创建版本锁定文件（以 v1.4.3 为例）
echo "v1.4.3" > .foundry-version
```

> 🔹 `.foundry-version` 文件的作用是明确声明该项目所需的 Foundry 版本。  
> 🔹 推荐将此文件提交到 Git 仓库，便于团队协作。

---

## 第六步：开发时切换到项目指定版本

每次进入项目目录时，运行以下命令以确保使用正确的 Foundry 版本：

```bash
# 根据 .foundry-version 安装指定版本
foundryup -v $(cat .foundry-version)

# 查看当前项目锁定的版本
cat .foundry-version
```

> 🔹 例如，若 `.foundry-version` 内容为 `v1.4.3`，该命令将确保本地使用此版本。  
> 🔹 **团队成员和 CI/CD 流水线**都应运行此命令，保证环境一致性。

---

## 第七步：更新项目版本（可选）

当项目需要升级 Foundry 时，可按以下步骤操作：

```bash
# 修改 .foundry-version 文件，升级版本
echo "v1.4.4" > .foundry-version

# 更新本地安装的 Foundry 版本
foundryup -v v1.4.4
```

> 🔹 建议在升级前测试新版本的兼容性。  
> 🔹 升级后请通知团队成员同步更新。

---

## 为什么这个方案“大多都在用”？

| 优势 | 说明 |
|------|------|
| ✅ **简单** | 仅需 `curl` 和 `foundryup`，三步完成安装 |
| ✅ **版本可控** | 通过 `.foundry-version` 精确锁定项目依赖 |
| ✅ **团队协作友好** | 所有成员运行相同命令，确保环境一致 |
| ✅ **CI/CD 友好** | GitHub Actions 等 CI 工具可自动安装指定版本 |
| ✅ **不污染项目** | 二进制文件不放入 Git，保持仓库轻量 |

---

## 项目结构

一个标准 Foundry 项目的典型目录结构如下：

```bash
foundry-temple-01/
├── .git/                        # Git 版本控制仓库
├── .github/                     # GitHub Actions 工作流配置
│   └── workflows/               # CI/CD 流水线脚本
│       └── test.yml             # 自动化测试流程定义
├── broadcast/                   # 部署脚本生成的广播文件夹（用于 `forge script`）
│   └── Counter.s.sol/3137/dry-run-cache/  # 模拟部署缓存（dry-run 结果）
├── lib/                         # 外部依赖库
│   └── forge-std/               # Foundry 标准库（如 `Script.sol`, `Test.sol`）
├── out/                         # 编译输出目录（ABI、Bytecode 等）
├── script/                      # 部署脚本（`.sol` 文件）
│   └── Counter.s.sol            # 部署脚本（使用 Forge Script 编写）
├── src/                         # 智能合约源码
│   └── Counter.sol              # 主合约文件
├── test/                        # 测试文件
│   └── Counter.t.sol            # 单元测试文件（使用 Foundry 的 `Test` 合约）
├── .foundry-version             # 🔒 锁定 Foundry 版本（如 v1.4.3）
├── .foundry-snapshot            # 📦 Foundry 快照文件（用于调试和状态恢复）
├── .gas-snapshot                # 📊 Gas 使用快照（记录各函数的 Gas 消耗）
├── .gitignore                   # 忽略文件列表（避免提交缓存和构建产物）
├── .gitmodules                  # Git 子模块配置（管理外部依赖）
├── foundry.lock                 # 🔒 锁定所有依赖版本（类似 package-lock.json）
├── foundry.toml                 # 🔧 Foundry 配置文件（编译器、网络、测试等设置）
└── README.md                    # 项目说明文档
```

### ✅ 各目录说明
| 路径 | 用途 |
|------|------|
| `.git/` | Git 版本控制系统的核心文件，不应手动修改 |
| `.github/workflows/test.yml` | 定义 GitHub Actions 的 CI 流程，例如自动运行测试 |
| `broadcast/Counter.s.sol/...` | `forge script` 执行 `--broadcast` 时生成的部署数据缓存，用于链上执行 |
| `lib/forge-std/` | Foundry 提供的标准库，包含 `Script.sol`（用于部署）、`Test.sol`（用于测试）等 |
| `out/` | 编译后的输出目录，包含 ABI、bytecode、metadata 等（由 `forge build` 生成） |
| `script/Counter.s.sol` | 部署脚本，通常继承自 `Script.sol`，支持交互式或自动化部署 |
| `src/Counter.sol` | 智能合约主代码，实现业务逻辑 |
| `test/Counter.t.sol` | 测试用例，继承自 `Test.sol`，可编写 Solidity 测试 |
| `.foundry-version` | 定义当前项目使用的 Foundry 版本（如 `v1.4.3`），确保团队一致 |
| `.foundry-snapshot` | Foundry 内部状态快照，用于调试和恢复 |
| `.gas-snapshot` | 记录每个函数调用的 Gas 使用情况，便于优化 |
| `.gitignore` | 告诉 Git 忽略哪些文件（如 `out/`, `.cache/`, `broadcast/`） |
| `.gitmodules` | 如果使用了 Git submodule（如自定义库），此文件记录其信息 |
| `foundry.lock` | 锁定所有依赖项的哈希值，确保构建一致性（类似 `package-lock.json`） |
| `foundry.toml` | Foundry 的核心配置文件，定义编译器、网络、测试参数等 |
| `README.md` | 项目介绍文档，建议包含功能说明、部署方式等 |


- ✅ 推荐将 `.foundry-version` 和 `foundry.lock` 提交到 Git，保证团队环境一致。
- ✅ 使用 `forge init` 可自动创建 `src/`, `test/`, `script/` 等基础结构。
- ✅ `lib/forge-std` 是标准库，可通过 `forge install foundry-rs/forge-std` 安装。
- ✅ `broadcast/` 目录是 `forge script --broadcast` 的输出，可用于在链上部署合约。
- ✅ `foundry.toml` 是开发中最重要的配置文件，可配置：
  ```toml
  [profile.default]
  solc-version = "0.8.30"
  ```

> 🔹 `foundry.toml` 用于配置编译器、测试、网络等参数，可参考 [Foundry Book](https://book.getfoundry.sh/) 进行高级配置。

---
## 📋 `forge` 常用命令详细表格

| 命令 | 语法格式 | 作用说明 | 使用场景示例 |
|------|---------|----------|-------------|
| `forge init` | `forge init <project-name>` | 初始化一个新的 Foundry 项目 | 创建新项目，自动生成 `src/`, `test/`, `script/` 结构 |
| `forge build` | `forge build [--optimize]` | 编译项目中的所有 Solidity 合约 | 检查编译是否通过，生成 ABI 和 bytecode |
| `forge clean` | `forge clean` | 删除 `out/` 和 `.cache/` 目录，清理编译产物 | 重新构建项目，避免缓存问题 |
| `forge test` | `forge test [-vvv] [--match-test <name>]` | 运行测试用例（Solidity 测试） | 执行 `test/*.t.sol` 中的单元测试 |
| `forge script` | `forge script <path> [--rpc-url] [--broadcast]` | 执行部署脚本（`.sol` 文件） | 部署合约到测试网或主网 |
| `forge create` | `forge create <contract> --constructor-args [args] --private-key` | 直接部署合约（无需写脚本） | 快速部署单个合约 |
| `forge verify-contract` | `forge verify-contract <addr> <path-to-source> --chain-id <id>` | 验证合约源码（支持 Etherscan、Blockscout） | 在 Etherscan 上提交源码验证 |
| `forge verify-check` | `forge verify-check <guid>` | 检查合约验证状态 | 查询 `verify-contract` 的验证结果 |
| `forge install` | `forge install <github-user/repo>` | 安装外部依赖库（如 OpenZeppelin） | 添加 `lib/` 中的依赖 |
| `forge update` | `forge update <lib-name>` | 更新指定依赖库 | 升级某个依赖到最新版本 |
| `forge remove` | `forge remove <lib-name>` | 删除依赖库 | 移除不再使用的库 |
| `forge config` | `forge config` | 显示当前项目的配置（来自 `foundry.toml`） | 查看编译器版本、optimizer 等设置 |
| `forge remappings` | `forge remappings` | 显示当前的路径重映射（import 别名） | 调试 import 路径问题 |
| `forge tree` | `forge tree` | 显示项目依赖树（类似 npm ls） | 查看 `lib/` 中依赖的层级关系 |
| `forge inspect` | `forge inspect <contract> <attribute>` | 查看合约的编译信息（如 abi, bytecode, storageLayout） | 获取合约 ABI 或分析存储结构 |
| `forge flatten` | `forge flatten <path>` | 将合约及其依赖合并为单个文件 | 提交到 Etherscan 验证或分享 |
| `forge snapshot` | `forge snapshot [--diff]` | 生成或比较 Gas 快照 | 分析函数 Gas 消耗变化 |
| `forge coverage` | `forge coverage` | 生成测试覆盖率报告（HTML） | 查看哪些代码被测试覆盖 |
| `forge doc` | `forge doc` | 生成文档（实验性） | 自动生成合约文档 |
| `forge bind` | `forge bind --bind <contract> -o <output-dir>` | 生成 Solidity 或 TypeScript 的合约绑定（ABI to code） | 在前端或脚本中调用合约 |
| `forge geiger` | `forge geiger` | 检测项目中使用了哪些 Solidity 作弊码（cheatcodes） | 安全审计 |

---

## 🔍 forge按功能分类速查

### 🛠️ 项目管理
| 命令 | 用途 |
|------|------|
| `forge init` | 初始化项目 |
| `forge build` | 编译合约 |
| `forge clean` | 清理构建产物 |
| `forge config` | 查看配置 |
| `forge remappings` | 查看 import 别名 |

### 🧪 测试与调试
| 命令 | 用途 |
|------|------|
| `forge test` | 运行测试 |
| `forge snapshot` | 生成 Gas 快照 |
| `forge coverage` | 生成测试覆盖率 |
| `forge inspect` | 查看合约编译信息 |

### 🚀 部署与交互
| 命令 | 用途 |
|------|------|
| `forge script` | 执行部署脚本 |
| `forge create` | 快速部署合约 |
| `forge broadcast` | 广播交易（配合 script） |
| `forge verify-contract` | 验证合约源码 |
| `forge verify-check` | 检查验证状态 |

### 📦 依赖管理
| 命令 | 用途 |
|------|------|
| `forge install` | 安装依赖 |
| `forge update` | 更新依赖 |
| `forge remove` | 删除依赖 |
| `forge tree` | 查看依赖树 |

### 🔄 代码生成与工具
| 命令 | 用途 |
|------|------|
| `forge flatten` | 合并合约为单文件 |
| `forge bind` | 生成合约绑定代码 |
| `forge doc` | 生成文档 |
| `forge geiger` | 检测 cheatcode 使用 |

---

## 💡 常用组合命令示例

### 1. 初始化项目并安装标准库
```bash
forge init foundry-temple-01
cd foundry-temple-01
forge install foundry-rs/forge-std
```

### 2. 编译并运行测试
```bash
forge build
forge test -vvv  # -v: 日志, -vvv: 详细 trace
```

### 3. 部署合约到 Sepolia
```bash
forge script script/Counter.s.sol:CounterScript \
  --rpc-url https://sepolia.infura.io/v3/YOUR_KEY \
  --private-key YOUR_PRIVATE_KEY \
  --broadcast \
  --verify
```

### 4. 验证已部署的合约
```bash
forge verify-contract \
  0x123...abc \
  src/Counter.sol:Counter \
  --chain-id 11155111 \
  --etherscan-api-key YOUR_ETHERSCAN_KEY
```

### 5. 生成合约绑定（TypeScript）
```bash
forge bind --bind Counter -o src/bindings --export-all
```

---

## 📚 查看帮助

每个命令都支持 `--help`：

```bash
forge <command> --help
```

例如：
```bash
forge test --help
forge script --help
forge verify-contract --help
```

---

## 📋 `cast` 常用子命令详细表格

| 子命令 | 语法格式 | 作用说明 | 使用场景示例 |
|--------|---------|----------|-------------|
| `cast balance` | `cast balance <address> [--rpc-url]` | 查询指定地址的 ETH 余额（单位为 wei） | 检查钱包或合约余额 |
| `cast block-number` | `cast block-number` | 获取当前链的最新区块高度 | 监控链状态 |
| `cast block` | `cast block <block-number\|hash>` | 查询指定区块的完整信息（含交易列表） | 分析区块数据 |
| `cast call` | `cast call <addr> "<func>" [args]` | 调用合约的只读函数（`view`/`pure`），不发送交易 | 查询合约状态，如 `balanceOf`, `name` |
| `cast send` | `cast send <to> "<func>" [args] --private-key` | 发送交易调用合约或转账，需私钥签名 | 执行 `transfer`, `approve`, `mint` 等写操作 |
| `cast abi-encode` | `cast abi-encode "<func>" [args]` | 将函数签名和参数编码为 calldata（ABI 编码） | 构造交易数据、验证调用 |
| `cast calldata` | `cast calldata "<func>" [args]` | 同 `abi-encode`，简写形式 | 快速生成函数调用数据 |
| `cast chain` | `cast chain` | 显示当前链的名称（如 `mainnet`, `sepolia`） | 确认连接的网络 |
| `cast chain-id` | `cast chain-id` | 返回当前链的 ID（如 1, 11155111） | 脚本中判断网络环境 |
| `cast gas-price` | `cast gas-price` | 获取当前建议的 Gas 价格（单位 wei） | 预估交易成本 |
| `cast tx` | `cast tx <tx-hash>` | 查询交易的详细信息（from, to, value, input 等） | 调试交易内容 |
| `cast receipt` | `cast receipt <tx-hash>` | 查询交易回执（logs, status, gasUsed, contractAddress） | 验证交易是否成功，获取事件日志 |
| `cast storage` | `cast storage <addr> <slot>` | 读取合约指定存储槽（storage slot）的值 | 调试合约内部状态，如 `owner`, `totalSupply` |
| `cast index` | `cast index <key> <val> <base_slot>` | 计算 mapping 类型的存储槽索引 | 读取 `mapping(address => uint)` 的值 |
| `cast keccak` | `cast keccak "data"` | 计算 Keccak-256 哈希值 | 生成函数选择器、计算事件签名 |
| `cast wallet new` | `cast wallet new` | 生成一个新的以太坊钱包（地址 + 私钥） | 创建测试账户 |
| `cast wallet address` | `cast wallet address --private-key` | 从私钥推导出地址 | 验证私钥对应的地址 |
| `cast wallet sign` | `cast wallet sign --private-key "msg"` | 使用私钥对消息进行签名 | 构造 EIP-712 签名等 |
| `cast wallet verify` | `cast wallet verify <sig> <msg> <addr>` | 验证签名是否由某地址签发 | 安全验证 |
| `cast rpc` | `cast rpc <method> [params...]` | 直接调用 JSON-RPC 方法（如 `eth_getBalance`） | 高级操作，绕过封装 |
| `cast namehash` | `cast namehash "vitalik.eth"` | 计算 ENS 名称的 namehash | ENS 相关开发 |
| `cast resolve-name` | `cast resolve-name "vitalik.eth"` | 解析 ENS 名称到地址 | 获取 ENS 绑定的地址 |
| `cast lookup-address` | `cast lookup-address <addr>` | 反向解析地址到 ENS 名称 | 查看地址是否有 ENS |
| `cast nonce` | `cast nonce <address>` | 查询地址的 nonce（交易计数） | 构造交易时使用 |
| `cast code` | `cast code <address>` | 获取合约的部署字节码（runtime bytecode） | 验证合约是否存在或比对代码 |
| `cast codesize` | `cast codesize <address>` | 获取合约字节码大小 | 判断是否为合约地址 |
| `cast decode-abi` | `cast decode-abi "<type>" <data>` | 解码 ABI 编码的数据 | 解析事件参数或返回值 |
| `cast decode-calldata` | `cast decode-calldata "<func>" <data>` | 解码 calldata 到函数参数 | 分析交易输入数据 |
| `cast pretty-calldata` | `cast pretty-calldata <data>` | 格式化并解析 calldata，尝试识别函数和参数 | 调试交易输入 |
| `cast create2` | `cast create2 --salt <salt> --init-code <code>` | 计算 CREATE2 部署地址 | 确定确定性部署地址 |
| `cast compute-address` | `cast compute-address <creator> [--nonce <n>]` | 计算通过 `CREATE` 部署的合约地址 | 预测合约地址 |
| `cast to-wei` | `cast to-wei <eth>` | 将 ETH 转换为 wei | 构造交易 value |
| `cast from-wei` | `cast from-wei <wei>` | 将 wei 转换为 ETH | 格式化显示余额 |
| `cast to-hex` / `to-dec` | `cast to-hex <num>` / `to-dec <hex>` | 进制转换 | 数据格式处理 |
| `cast access-list` | `cast access-list <to> [data] --rpc-url` | 生成交易的 access list | 优化 Gas 和避免 revert |
| `cast estimate` | `cast estimate <to> [data]` | 估算交易 Gas 使用量 | 预估 Gas 成本 |

## 🔍 cast按功能分类速查

### 📊 **链上查询类**
| 命令 | 用途 |
|------|------|
| `cast balance` | 查余额 |
| `cast block` / `block-number` | 查区块 |
| `cast tx` / `receipt` | 查交易 |
| `cast storage` / `index` | 查合约存储 |
| `cast code` / `codesize` | 查合约代码 |

### 📡 **合约交互类**
| 命令 | 用途 |
|------|------|
| `cast call` | 读操作（不发交易） |
| `cast send` | 写操作（发交易） |
| `cast abi-encode` / `calldata` | 构造调用数据 |

### 🔐 **钱包与签名类**
| 命令 | 用途 |
|------|------|
| `cast wallet new/address/sign` | 钱包管理 |
| `cast sign` / `verify` | 消息签名验证 |

### 🔤 **编码与转换类**
| 命令 | 用途 |
|------|------|
| `cast keccak` | 哈希计算 |
| `cast to-wei` / `from-wei` | 单位转换 |
| `cast to-hex` / `to-dec` | 进制转换 |
| `cast decode-abi` / `decode-calldata` | 解码数据 |

### 🌐 **网络与 ENS 类**
| 命令 | 用途 |
|------|------|
| `cast chain` / `chain-id` | 查链信息 |
| `cast resolve-name` / `lookup-address` | ENS 解析 |
| `cast namehash` | ENS namehash 计算 |

### 🛠️ **高级与调试类**
| 命令 | 用途 |
|------|------|
| `cast rpc` | 直接调用 JSON-RPC |
| `cast create2` / `compute-address` | 预测合约地址 |
| `cast access-list` / `estimate` | Gas 优化与预估 |

---

🎯 **最佳实践建议**：
> - 保持 `lib/` 目录整洁，仅引入必要依赖
> - 使用 `forge install` 安装库，自动更新 `.gitmodules` 和 `lib/`
> - 在 CI 中运行 `foundryup -v $(cat .foundry-version)` 确保版本一致

🎯 **提示**：更多文档请查阅 [Foundry Book](https://book.getfoundry.sh/) 和 [官方 GitHub](https://github.com/foundry-rs/foundry)。  