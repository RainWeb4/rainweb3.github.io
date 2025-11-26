# Foundry 工具多方式安装与卸载完整指南
---
> **作者：RainWeb3**
> **更新时间：2025年10月27日**  
> **适用平台：Linux、macOS、Windows（WSL）**  
> **目标读者：智能合约开发者、区块链工程师、DevOps 工程师**

---

## 目录

- [一、简介](#一简介)
- [二、安装方式推荐排序](#二安装方式推荐排序由高到低)
- [三、详细安装与卸载方式](#三详细安装与卸载方式)
    - [1. foundryup 脚本（官方推荐）](#1-foundryup-脚本官方推荐)
    - [2. Homebrew（仅限 macOS 和 Linux）](#2-homebrew仅限-macos-和-linux)
    - [3. Cargo（Rust 包管理器）](#3-cargo-rust-包管理器)
    - [4. 手动下载二进制文件](#4-手动下载二进制文件)
    - [5. Docker 容器](#5-docker-容器)
- [四、安装方式对比总结](#四安装方式对比总结)
- [五、推荐选择建议](#五推荐选择建议)

---

## 一、简介

Foundry 是一套用于以太坊智能合约开发的 Rust 编写的工具链，主要包括：

- `forge`：编译、测试、部署合约
- `cast`：与链交互、编码解码、查询链上数据
- `anvil`：本地测试网络（类似 Hardhat Network 或 Ganache）
- `chisel`：交互式 Solidity REPL

本文档详细列出 Foundry 的所有安装方式（按推荐度排序），并提供对应的卸载方法，明确标注每种方式是**全局安装**还是**局部安装**，并解释不同安装方式之间的区别。

---

## 二、安装方式推荐排序（由高到低）

| 排名 | 安装方式               | 类型   | 推荐理由 |
|------|------------------------|--------|----------|
| 1    | foundryup 脚本         | 全局   | 官方推荐、一键安装/更新、自动管理 |
| 2    | Homebrew（macOS/Linux）| 全局   | macOS 用户友好、依赖管理清晰 |
| 3    | Cargo（Rust）          | 全局或局部 | 适合 Rust 开发者、可指定版本 |
| 4    | 手动下载二进制         | 全局或局部 | 无网络依赖、适合离线环境 |
| 5    | Docker 容器            | 局部   | 隔离环境、适合 CI/CD 或临时使用 |

---

## 三、详细安装与卸载方式

### 1. foundryup 脚本（官方推荐）

**类型：全局安装**

#### 安装步骤

```bash
# 下载并运行官方安装脚本
curl -L https://foundry.paradigm.xyz | bash

示例：
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   167  100   167    0     0     94      0  0:00:01  0:00:01 --:--:--    93
100  2200  100  2200    0     0   1049      0  0:00:02  0:00:02 --:--:--  1049
Installing foundryup...

Detected your preferred shell is bash and added foundryup to PATH.
Run 'source /home/test/.bashrc' or start a new terminal session to use foundryup.
Then, simply run 'foundryup' to install Foundry.

# 将 foundryup 加入 PATH（若未自动添加）
# 通常脚本会提示你运行以下命令：
foundryup

示例：
.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx.xOx

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
foundryup: found attestation for stable version, downloading attestation artifact, checking...
################################################################################################################################################ 100.0%
foundryup: binaries not found or do not match expected hashes, downloading new binaries
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

#### 说明

- 第一次运行 `curl` 命令会安装 `foundryup` 工具本身（一个小型 Rust 程序）。
- 然后运行 `foundryup` 会从 GitHub Releases 下载最新版 `forge`、`cast`、`anvil`、`chisel` 并安装到 `~/.foundry/bin`。
- 脚本会自动将 `~/.foundry/bin` 添加到你的 shell 配置文件（如 `~/.bashrc`、`~/.zshrc`）。

#### 验证安装

```bash
forge --version

示例：
forge Version: 1.4.3-stable
Commit SHA: fa9f934bdac4bcf57e694e852a61997dda90668a
Build Timestamp: 2025-10-22T05:31:43.173937269Z (1761111103)
Build Profile: maxperf

cast --version

示例：
cast Version: 1.4.3-stable
Commit SHA: fa9f934bdac4bcf57e694e852a61997dda90668a
Build Timestamp: 2025-10-22T05:31:43.173937269Z (1761111103)
Build Profile: maxperf

```

#### 更新方式

```bash
foundryup
```

#### 卸载步骤

```bash
# 删除二进制文件
rm -rf ~/.foundry

# 从 shell 配置中移除 PATH（手动编辑）
# 打开 vim ~/.bashrc 或 ~/.zshrc，删除类似以下行：
export PATH="$HOME/.foundry/bin:$PATH"


# 重新加载 shell
source ~/.bashrc   # 或 source ~/.zshrc
```
#### 验证卸载是否成功
```bash
先确认实际安装路径：
which forge

示例：
/home/test/.cargo/bin/forge 或 /usr/local/bin/forge 或 /opt/foundry/bin/forge

如果路径不是 ~/.foundry/bin/forge，说明你删错了目录。
查看你的 PATH：echo $PATH

示例：
/home/test/.foundry/bin:/home/test/.vscode-server/bin/  ...

Shell缓存了命令路径
某些 shell（如 zsh）会缓存命令路径。即使你删除了二进制文件，which 可能仍显示缓存结果。
清除 shell 命令哈希缓存：hash -r  

若运行 forge --version：（依然能输出版本信息，可能是你安装的目录不对。）

示例：
forge Version: 1.4.3-dev
Commit SHA: 1a5de245468a3825a96992fb7a690353950a411e
Build Timestamp: 2025-10-21T16:07:30.217792003Z (1761062850)
Build Profile: release

然后根据上面的（which forge）显示路径，选择其他卸载方式即可。

验证版本：
foundry --version

示例：
foundry: command not found

验证版本：
cast --version

示例：（则说明 命令路径缓存残留” + “二进制文件已删除但 shell 仍尝试调用旧路径”）
bash: /home/test/.cargo/bin/cast: No such file or directory

清除 shell 命令路径缓存：hash -r 

验证版本：cast --version
示例：（缓存及Foundry卸载成功）
Command 'cast' not found, did you mean:
  command 'fast' from snap fast (0.0.4)
  command 'cass' from snap cass (0.17.2)
  command 'cas' from deb amule-utils (1:2.3.3-3build1)
  command 'casw' from deb epics-base (7.0.7+dfsg1-5)
  command 'cat' from deb coreutils (9.4-3ubuntu6.1)
  command 'ast' from deb jruby (9.3.9.0+ds-1)
  command 'cmst' from deb cmst (2023.03.14-1)
  command 'cst' from deb imx-code-signing-tool (3.3.2+dfsg-1)
  command 'nast' from deb nast (0.2.0-10)
  command 'last' from deb util-linux (2.39.3-9ubuntu6.3)
See 'snap info <snapname>' for additional versions.

```
####  清除缓存
```bash
hash -r
```
> **注意**：`foundryup` 本身也会被删除，因为它就在 `~/.foundry/bin` 中。

---

### 2. Homebrew（仅限 macOS 和 Linux）

**类型：全局安装**

#### 安装步骤

```bash
# 不推荐在 Linux 上用 Homebrew-缺点如下：
 安装复杂、构建慢、占用空间大、 更新不及时、 包管理冲突

# 添加 Foundry 官方 tap（Homebrew 需要在Linux上预先安装）
brew tap foundry-rs/foundry

-----------------如果是macOS可以直接跳过这里-----------------------------------------
# 上面命令执行后，若你不是 macOS 会出现：

示例：
brew tap foundry-rs/foundry
Command 'brew' not found, did you mean:
  command 'brec' from deb bplay (0.991-10.2)
  command 'qbrew' from deb qbrew (0.4.1-8build1)
Try: sudo apt install <deb name>

若你想在Linux上使用Homebrew:(执行如下命令，可能需要sudo权限)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

示例：
==> Checking for `sudo` access (which may request your password)...
[sudo] password for name（你的root）: （这里输入，你曾经设置过的Linux密码）

# 按下回车键后：（安装路径通常是 /home/linuxbrew/.linuxbrew）
示例：
/home/linuxbrew/.linuxbrew/sbin
/home/linuxbrew/.linuxbrew/share
/home/linuxbrew/.linuxbrew/var
/home/linuxbrew/.linuxbrew/opt
/home/linuxbrew/.linuxbrew/share/zsh
/home/linuxbrew/.linuxbrew/share/zsh/site-functions
/home/linuxbrew/.linuxbrew/var/homebrew
/home/linuxbrew/.linuxbrew/var/homebrew/linked
/home/linuxbrew/.linuxbrew/Cellar
/home/linuxbrew/.linuxbrew/Caskroom
/home/linuxbrew/.linuxbrew/Frameworks

Press RETURN/ENTER to continue or any other key to abort:
# 再次点击回车键，就会继续执行Homebrew安装了。

# 安装过程顺利完成，没有报错，但可能会提示一个重要警告：

示例：
Warning: /home/linuxbrew/.linuxbrew/bin is not in your PATH.

# 这意味着你现在还不能直接在终端中使用 brew 命令，除非你先执行 eval 命令或重启终端（前提是已配置好环境变量）。
# 下一步，配置环境变量：（非macOS系统，必须配置）

示例：
# 作用：向 .bashrc 文件追加一行空行（test换成你的用户名）
echo >> /home/test/.bashrc 

# 作用：将 Homebrew 的环境变量初始化脚本写入 .bashrc，确保每次打开终端都能识别 brew
#（test换成你的用户名）
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/test/.bashrc

# 作用：立即在当前终端会话中加载该配置（无需重启终端）
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"

# 验证安装是否生效：
brew --version
示例：Homebrew 4.6.18

# 可以再试一个安装命令：（比如安装 hello 测试包，若成功安装并运行，说明安装成功）
brew install hello

示例：
==> Fetching downloads for: hello
==> Downloading https://ghcr.io/v2/homebrew/core/hello/manifests/2.12.2
############################################################################################################################# 100.0%
==> Fetching hello
==> Downloading https://ghcr.io/v2/homebrew/core/hello/blobs/sha256:bc74355f9ea73a40f629dd7e5adcaaad7c0ac7ffda2f3acc860bd7e52baabb94
############################################################################################################################# 100.0%
==> Pouring hello--2.12.2.x86_64_linux.bottle.tar.gz
🍺  /home/linuxbrew/.linuxbrew/Cellar/hello/2.12.2: 57 files, 720.6KB
==> Running `brew cleanup hello`...
Disable this behaviour by setting `HOMEBREW_NO_INSTALL_CLEANUP=1`.
Hide these hints with `HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).

# Homebrew 公式很多需要编译，可能需要安装基础构建工具：（以下命令供参考，根据需要自行选择安装或不装）
# 作用：执行这条命令后，你的 Linux 系统将具备：
# 编译能力（build-essential）、系统监控能力（procps）、网络交互能力（curl）、文件识别能力（file）、代码版本控制能力（git）
sudo apt-get install build-essential procps curl file git

# 作用：安全地清理系统中不再被任何已安装软件依赖的自动安装包。
sudo apt autoremove

# 作用：通过 Homebrew/Linuxbrew 安装一个独立、最新版本的 GNU C/C++ 编译器（ 安装的 GCC 版本通常比系统自带的更新）
# 安装后可用 gcc-14 或类似命令，具体版本号视情况而定
brew install gcc

# 作用：关闭匿名统计 （Homebrew 默认开启匿名数据分析）
brew analytics off

# 其他 brew 常用命令：
# 查看帮助：brew help
# 搜索软件：brew search <name>
# 安装软件：brew install <formula>
# 卸载软件：brew uninstall <formula>
# 更新 Homebrew：brew update
# 检查问题：brew doctor
# 删除旧版本：brew cleanup        
# 删除下载的压缩包：brew cleanup -s     
# brew文档主页：https://docs.brew.sh
# Linux 特定说明：https://docs.brew.sh/Homebrew-on-Linux

#  安全卸载方式
# 下载卸载脚本：curl -fsSL -O https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh
# 赋予执行权限：chmod +x uninstall.sh
# 执行卸载：./uninstall.sh

示例：
Warning: This script will remove:
/home/linuxbrew/.linuxbrew/Caskroom/
/home/linuxbrew/.linuxbrew/Cellar/
/home/linuxbrew/.linuxbrew/Homebrew/
/home/linuxbrew/.linuxbrew/Homebrew/.claude/
/home/linuxbrew/.linuxbrew/Homebrew/.cursor/
/home/linuxbrew/.linuxbrew/Homebrew/.devcontainer/
/home/linuxbrew/.linuxbrew/Homebrew/.dockerignore
/home/linuxbrew/.linuxbrew/Homebrew/.editorconfig
....
接着会提示你：（是否清理 shell 配置（.bashrc 等））
Are you sure you want to uninstall Homebrew? This will remove your installed packages! [y/N] y
输入Y，回车即可。

# 验证 Homebrew 是否已成功卸载。（所有命令都应无输出或提示“未找到”）
# 1. 检查 brew 命令是否存在（无输出，则正常）
which brew

# 2. 尝试运行 brew（应报错）
brew --version

示例：（残留 PATH 引用）
bash: /home/linuxbrew/.linuxbrew/bin/brew: No such file or directory

# 3. 检查 Homebrew 主目录（Linux）
ls -la /home/linuxbrew/.linuxbrew

示例： Homebrew 被部分删除，但未完全卸载。核心文件（如 bin/brew）已丢失，但安装目录仍残留。
drwxr-xr-x 4 test test 4096 Oct 26 21:01 .
drwxr-xr-x 3 root root 4096 Oct 25 20:49 ..
drwxrwxr-x 2 test test 4096 Oct 26 21:01 lib
drwxrwxr-x 3 test test 4096 Oct 26 21:01 share

# 4. 检查用户级缓存
ls -la ~/Library/Caches/Homebrew 2>/dev/null || echo "目录不存在（正常）"

示例：（缓存已清理-正常）
目录不存在（正常）

# 5. 检查临时文件
ls -la /tmp/homebrew*

示例：（临时文件已清理-正常）
ls: cannot access '/tmp/homebrew*': No such file or directory

# 接着清理剩余卸载残留
# 彻底删除 Homebrew 安装目录：（可能需要用户权限，需要输入你的密码）
sudo rm -rf /home/linuxbrew/.linuxbrew

示例：
[sudo] password for test:

# 验证是否删除成功
 ls -la /home/linuxbrew/.linuxbrew

示例：（已清理成功）
ls: cannot access '/home/linuxbrew/.linuxbrew': No such file or directory

# 检查并清理 .bashrc 中的 Homebrew 配置
grep -n "brew" ~/.bashrc

示例：（无任何输出，则正常，若输出如下。继续下面的操作）
127:eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"

# 打开编辑器
vi ~/.bashrc （打开文件后，使用 ？搜索 brew）

或 

vim ~/.bashrc （打开文件后，使用 ？搜索 brew）

或 

nano ~/.bashrc （打开文件后，Ctrl + W 搜索 brew）

# 找到如上面输出的~/.bashrc文件中的127行。
手动删除 eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"

# 或者用sed命令一键删除：sed -i '/brew shellenv/d' ~/.bashrc

# 再次检查配置:(无输出)
grep "brew" ~/.bashrc

# 检查 brew 命令是否存在
which brew（无输出）

brew --version

示例：（说明还有缓存）
bash: /home/linuxbrew/.linuxbrew/bin/brew: No such file or directory

# 清除缓存： hash -r

# 再次验证：brew --version

示例：（现在已成功干净的卸载了 Homebrew）
Command 'brew' not found, did you mean:
  command 'qbrew' from deb qbrew (0.4.1-8build1)
  command 'brec' from deb bplay (0.991-10.2)
Try: sudo apt install <deb name>
-------------------macOS可以直接跳过---------------------------------------

# 安装
brew install foundry

示例：
==> Fetching downloads for: foundry
==> Downloading https://ghcr.io/v2/homebrew/core/foundry/manifests/1.4.3
Already downloaded: /home/test/.cache/Homebrew/downloads/bdc9f38c9e21de7569ee50c0c404f581a91b577c93f09d7198d1f655044f7b61--foundry-1.4.3.bottle_manifest.json
==> Fetching foundry
==> Downloading https://ghcr.io/v2/homebrew/core/foundry/blobs/sha256:e86c972b648ad231a4a26930a546e0fbaf2dd9debf1def053328bb70ee3a6433
Already downloaded: /home/test/.cache/Homebrew/downloads/3abb9c6b77d7ece38842a71da7d97ba77a8b42693dc201a79cfcbea7ea863e23--foundry--1.4.3.x86_64_linux.bottle.tar.gz
==> Pouring foundry--1.4.3.x86_64_linux.bottle.tar.gz
🍺  /home/linuxbrew/.linuxbrew/Cellar/foundry/1.4.3: 25 files, 202.9MB
==> Running `brew cleanup foundry`...
Disable this behaviour by setting `HOMEBREW_NO_INSTALL_CLEANUP=1`.
Hide these hints with `HOMEBREW_NO_ENV_HINTS=1` (see `man brew`).
==> Caveats
Bash completion has been installed to:
  /home/linuxbrew/.linuxbrew/etc/bash_completion.d
```

#### 验证安装

```bash
forge --version

示例：
forge Version: 1.4.3-Homebrew
Commit SHA: VERGEN_IDEMPOTENT_OUTPUT
Build Timestamp: 2025-10-22T03:58:23.000000000Z (1761105503)
Build Profile: release
```

#### 验证初始化项目

```bash
forge init my-foundry-project

示例：
Initializing /home/test/foundry/foundry-temple-test/foundry-temple-01/my-foundry-project...
Installing forge-std in /home/test/foundry/foundry-temple-test/foundry-temple-01/my-foundry-project/lib/forge-std (url: Some("https://github.com/foundry-rs/forge-std"), tag: None)
Cloning into '/home/test/foundry/foundry-temple-test/foundry-temple-01/my-foundry-project/lib/forge-std'...
remote: Enumerating objects: 2338, done.
remote: Counting objects: 100% (1177/1177), done.
remote: Compressing objects: 100% (210/210), done.
remote: Total 2338 (delta 1065), reused 985 (delta 966), pack-reused 1161 (from 3)
Receiving objects: 100% (2338/2338), 819.31 KiB | 838.00 KiB/s, done.
Resolving deltas: 100% (1552/1552), done.
    Installed forge-std tag=v1.11.0@8e40513d678f392f398620b3ef2b418648b33e89
    Initialized forge project
```

#### 更新方式

```bash
brew upgrade foundry

示例：
Warning: foundry 1.4.3 already installed
```

#### 卸载步骤

```bash
# 卸载软件包
brew uninstall foundry

# 可选：移除 tap
brew untap foundry-rs/foundry
```
####  清除缓存
```bash
hash -r
```
> **优点**：与系统包管理集成，适合 macOS 用户。  
> **缺点**：更新可能略滞后于 `foundryup`（取决于维护频率）。

---

### 3. Cargo（Rust 包管理器）

**类型：可选全局或局部**

- **全局安装**：适用于日常开发
- **局部安装**：在特定项目中使用（不推荐，因 Foundry 是 CLI 工具）

#### 安装步骤（全局）

```bash
# 确保已安装 Rust（若未安装）
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

示例：
info: downloading installer
warn: It looks like you have an existing rustup settings file at:
warn: /home/test/.rustup/settings.toml
warn: Rustup will install the default toolchain as specified in the settings file,
warn: instead of the one inferred from the default host triple.

Welcome to Rust!
.....

# 安装 Foundry工具链
# 安装 forge
cargo install --git https://github.com/foundry-rs/foundry forge
# 安装 
cargo install --git https://github.com/foundry-rs/foundry cast
# 安装 anvil
cargo install --git https://github.com/foundry-rs/foundry anvil
# 安装 chisel
cargo install --git https://github.com/foundry-rs/foundry chisel

示例：
....(省略)
 Compiling foundry-linking v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/linking)
   Compiling foundry-config v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/config)
   Compiling foundry-wallets v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/wallets)
   Compiling foundry-evm-core v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/evm/core)
   Compiling forge-script-sequence v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/script-sequence)
   Compiling forge-fmt v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/fmt)
   Compiling forge-doc v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/doc)
   Compiling foundry-evm-coverage v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/evm/coverage)
   Compiling foundry-evm-traces v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/evm/traces)
   Compiling foundry-evm-fuzz v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/evm/fuzz)
   Compiling foundry-cheatcodes v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/cheatcodes)
   Compiling foundry-evm v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/evm/evm)
   Compiling foundry-cli v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/cli)
   Compiling chisel v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/chisel)
    Finished `release` profile [optimized] target(s) in 2m 06s
  Installing /home/test/.cargo/bin/chisel
   Installed package `chisel v1.4.4 (https://github.com/foundry-rs/foundry#b8f6d5a9)` (executable `chisel`)

```

#### 验证安装

```bash
forge --version
cast --version
anvil --version
chisel --version

若出现类似的错误-例如：（可能是 Shell 缓存了旧的命令路径导致）
forge --version
bash: /home/linuxbrew/.linuxbrew/bin/forge: No such file or directory

# 验证 ~/.cargo/bin 是否有 forge
ls ~/.cargo/bin/ | grep forge

示例：（说明forge 二进制文件已经成功安装到了 ~/.cargo/bin/）
forge

# 解决方案：清除 Bash 的命令缓存
hash -d forge 或 hash -r（更彻底）

# 验证是否修复：

which forge

示例：/home/test/.cargo/bin/forge

#验证forge成功：

forge --version

示例：
forge Version: 1.4.4-dev
Commit SHA: b8f6d5a95efaa0db68aa5b2921c8973ca6ba62e2
Build Timestamp: 2025-10-26T11:34:05.801662462Z (1761478445)
Build Profile: release

# 初始化项目
forge init my-foundry-project

```

#### 安装步骤（局部，不推荐）

```bash
# 在项目目录中（不推荐用于 CLI 工具）
cargo install --git https://github.com/foundry-rs/foundry --root ./local-bin forge cast anvil chisel

示例：
 Updating git repository `https://github.com/foundry-rs/foundry`
    Updating git repository `https://github.com/foundry-rs/foundry`
    Updating git repository `https://github.com/foundry-rs/foundry`
    Updating git repository `https://github.com/foundry-rs/foundry`
  Installing forge v1.4.4 (https://github.com/foundry-rs/foundry#b8f6d5a9)
    Updating git repository `https://github.com/rust-cli/rexpect`
    Updating crates.io index
warning: Patch `rexpect v0.6.2 (https://github.com/rust-cli/rexpect?rev=2ed0b1898d7edaf6a85bedbae71a01cc578958fc#2ed0b189)` was not used in the crate graph.
....
....
  Compiling chisel v1.4.4 (/home/test/.cargo/git/checkouts/foundry-87057ca846c16966/b8f6d5a/crates/chisel)
    Finished `release` profile [optimized] target(s) in 9m 12s
  Installing ./local-bin/bin/chisel
   Installed package `chisel v1.4.4 (https://github.com/foundry-rs/foundry#b8f6d5a9)` (executable `chisel`)
     Summary Successfully installed forge, cast, anvil, chisel!
warning: be sure to add `./local-bin/bin` to your PATH to be able to run the installed binaries

# 然后手动将 ./local-bin/bin 加入 PATH
export PATH="$PWD/local-bin/bin:$PATH"
```


#### 更新方式

```bash
# 逐个强制重新安装（推荐）
# --force 会强制重新编译并覆盖已存在的二进制，相当于“更新”。
cargo install --git https://github.com/foundry-rs/foundry --force cast
cargo install --git https://github.com/foundry-rs/foundry --force anvil
cargo install --git https://github.com/foundry-rs/foundry --force chisel
cargo install --git https://github.com/foundry-rs/foundry --force forge

示例：
 Updating git repository `https://github.com/foundry-rs/foundry`
    Updating git repository `https://github.com/foundry-rs/foundry`
    Updating git repository `https://github.com/foundry-rs/foundry`
    Updating git repository `https://github.com/foundry-rs/foundry`
  Installing forge v1.4.4 (https://github.com/foundry-rs/foundry#b8f6d5a9)
    Updating git repository `https://github.com/rust-cli/rexpect`
    Updating crates.io index
warning: Patch `rexpect v0.6.2 (https://github.com/rust-cli/rexpect?rev=2ed0b1898d7edaf6a85bedbae71a01cc578958fc#2ed0b189)` was not used in the crate graph.
Check that the patched package version and available features are compatible
with the dependency requirements. If the patch has a different version from
what is locked in the Cargo.lock file, run `cargo update` to use the new
version. This may also occur with an optional dependency that is not enabled.
.....
.....

# 或者采用shell循环更新
for tool in cast anvil chisel forge; do
  cargo install --git https://github.com/foundry-rs/foundry --force $tool
done
```

#### 卸载步骤（全局）

```bash
cargo uninstall forge cast anvil chisel

或

cargo uninstall forge
cargo uninstall cast
cargo uninstall anvil
cargo uninstall chisel

```

#### 卸载步骤（局部）

```bash
rm -rf ./local-bin  # 删除本地安装目录
```
####  清除缓存
```bash
hash -r
```
> **适用场景**：Rust 开发者、需要自定义编译选项、贡献代码。

---

### 4. 手动下载二进制文件

**类型：可配置为全局或局部**

#### 安装步骤

1. 访问 [Foundry Releases 页面](https://github.com/foundry-rs/foundry/releases)
2. 根据系统下载对应压缩包（如 `foundry_nightly_linux_amd64.tar.gz`）
3. 解压并放置到目标目录

##### 全局安装示例

```bash
# 学习、开发、测试：✅ 推荐使用
# 严格生产环境（如审计脚本）：⚠️ 小心使用
wget https://github.com/foundry-rs/foundry/releases/download/nightly-6ccbf569d191af7d857d4085d367113f1b0aecdf/foundry_nightly_linux_amd64.tar.gz

# 解压Foundry工具包
tar -xzf foundry_nightly_linux_amd64.tar.gz

# 将以下四个可执行文件移动到系统目录中，使其在终端任何位置都可直接运行。
sudo mv forge cast anvil chisel /usr/local/bin/
```

##### 局部安装示例

```bash
# 安全地创建一个用于存放 Foundry 二进制文件的目录，即使它已存在或父目录缺失也不会出错。
mkdir -p ./foundry-bin

# 将 foundry_nightly_linux_amd64.tar.gz 压缩包解压到 ./foundry-bin 目录中，可通过路径调用。
tar -xzf foundry_nightly_linux_amd64.tar.gz -C ./foundry-bin

# 仅对当前终端会话有效（一旦你关闭终端或打开新终端，这个 PATH 修改就失效了）
export PATH="$PWD/foundry-bin:$PATH"
```

#### 验证安装

```bash
forge --version
cast --version
anvil --version
chisel --version

# 初始化项目
forge init my-foundry-project

示例：
Warning: This is a nightly build of Foundry. It is recommended to use the latest stable version. To mute this warning set `FOUNDRY_DISABLE_NIGHTLY_WARNING` in your environment. 

Initializing /home/test/foundry/foundry-temple-test/foundry-temple-01/my-foundry-project...
Installing forge-std in /home/test/foundry/foundry-temple-test/foundry-temple-01/my-foundry-project/lib/forge-std (url: https://github.com/foundry-rs/forge-std, tag: None)
Cloning into '/home/test/foundry/foundry-temple-test/foundry-temple-01/my-foundry-project/lib/forge-std'...
```

#### 更新方式

重复上述步骤，替换旧二进制文件。

#### 卸载步骤

- **全局**：
  ```bash
  sudo rm /usr/local/bin/forge /usr/local/bin/cast /usr/local/bin/anvil /usr/local/bin/chisel
  ```
- **局部**：
  ```bash
  rm -rf ./foundry-bin
  ```

> **优点**：完全控制版本和位置，适合离线或受限环境。  
> **缺点**：需手动管理更新和 PATH。

---

### 5. Docker 容器

**类型：局部（容器内）**

> **说明**：此方式不将工具安装到主机，而是在容器中临时使用。

#### 安装步骤（无需“安装”，直接运行）

```bash
# 拉取 Foundry 官方镜像
docker pull ghcr.io/foundry-rs/foundry:latest

# 为方便使用，可以重命名镜像标签
docker tag ghcr.io/foundry-rs/foundry:latest foundry:latest

# 查看镜像
docker images

示例：
ghcr.io/foundry-rs/foundry    latest    44c6957ef5e3   5 days ago     406MB
重命名后：
foundry                       latest    44c6957ef5e3   5 days ago     406MB

----------------------容器内验证Foundry-------------------------------------------------------
步骤 1：进入容器交互式环境
docker run --rm -it foundry:latest /bin/sh

步骤 2：在容器内执行以下命令（逐行复制）
# 1. 查看当前路径
echo "=== Current PATH ==="
输出：=== Current PATH ===
echo $PATH
输出：/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
# 2. 查找 forge
echo "\n=== Where is forge? ==="
输出：=== Where is forge? ===
which forge
输出：/usr/local/bin/forge
find / -name "forge" -type f 2>/dev/null
输出：/usr/local/bin/forge
# 3. 查看 /usr/local/bin/forge 是否存在
echo "\n=== ls /usr/local/bin/ ==="
输出：=== ls /usr/local/bin/ ===
ls -la /usr/local/bin/forge 2>/dev/null || echo "Not found"
输出：-rwxr-xr-x 1 root root 68003760 Oct 21 11:18 /usr/local/bin/forge
# 4. 直接运行 forge -V
echo "\n=== forge -V ==="
输出：echo "\n=== forge -V ==="
/usr/local/bin/forge -V
输出：forge 1.4.3-nightly (040be035f2 2025-10-21T11:09:42.982025220Z)
# 5. 运行 forge --version
echo "\n=== forge --version ==="
输出：=== forge --version ===
/usr/local/bin/forge --
输出:
forge Version: 1.4.3-nightly
Commit SHA: 040be035f23df51676a462e5a90b2ef087aa6470
Build Timestamp: 2025-10-21T11:09:42.982025220Z (1761044982)
Build Profile: maxperf

# 6. 运行 forge version（注意：无 -）
echo "\n=== forge version ==="
输出：=== forge version ===
/usr/local/bin/forge version
输出：
error: unrecognized subcommand 'version'

  tip: some similar subcommands exist: 'v', 'verify-contract'

Usage: forge [OPTIONS] <COMMAND>

For more information, try '--help'.
# 7. 查看 forge 是否是 shell 脚本
echo "\n=== file of forge ==="
输出：=== file of forge ===
file /usr/local/bin/forge
输出：/bin/sh: 15: file: not found
# 8. 查看 forge 是否是 symlink
echo "\n=== ls -la of forge ==="
输出：=== ls -la of forge ===
ls -la /usr/local/bin/forge
输出：
-rwxr-xr-x 1 root root 68003760 Oct 21 11:18 /usr/local/bin/forge
-----------------------------------------------------------------------------


# 查看版本
docker run --rm foundry:latest "/usr/local/bin/forge -V"

示例：
forge 1.4.3-nightly (040be035f2 2025-10-21T11:09:42.982025220Z)

# 查看详细版本信息
docker run --rm \
  --entrypoint /usr/local/bin/forge \
  foundry:latest \
  --version

示例：
forge Version: 1.4.3-nightly
Commit SHA: 040be035f23df51676a462e5a90b2ef087aa6470
Build Timestamp: 2025-10-21T11:09:42.982025220Z (1761044982)
Build Profile: maxperf

# 初始化foundry项目
mkdir my-foundry-project && cd my-foundry-project

# 方式1：挂载当前目录到容器中（常用-推荐。 文件写入宿主机）
# 挂载只是把宿主机的目录映射到容器里，你本地 并没有安装 forge。
# 你仍然需要通过 docker run ... forge build 来执行命令
docker run --rm \
  -v "$PWD":/app \
  -w /app \
  --entrypoint /usr/local/bin/forge \
  foundry:latest \
  init .

# 方式2：或者不挂载，只运行 forge 命令（不挂载目录，容器退出后一切消失）
docker run --rm \
  --entrypoint /usr/local/bin/forge \
  foundry:latest \
  init .

示例：
Warning: This is a nightly build of Foundry. It is recommended to use the latest stable version. To mute this warning set `FOUNDRY_DISABLE_NIGHTLY_WARNING` in your environment. 

Initializing /app...
Installing forge-std in /app/lib/forge-std (url: https://github.com/foundry-rs/forge-std, tag: None)
Cloning into '/app/lib/forge-std'...
    Installed forge-std tag=v1.11.0@8e40513d678f392f398620b3ef2b418648b33e89
    Initialized forge project

# 编译项目
docker run --rm \
  -v "$PWD":/app \
  -w /app \
  --entrypoint /usr/local/bin/forge \
  foundry:latest \
  build

示例：
Warning: This is a nightly build of Foundry. It is recommended to use the latest stable version. To mute this warning set `FOUNDRY_DISABLE_NIGHTLY_WARNING` in your environment. 

Compiling 23 files with Solc 0.8.30
installing solc version "0.8.30"
Successfully installed solc 0.8.30
Solc 0.8.30 finished in 10.33s
Compiler run successful!

# 运行测试
docker run --rm \
  -v "$PWD":/app \
  -w /app \
  --entrypoint /usr/local/bin/forge \
  foundry:latest \
  test

示例：
Warning: This is a nightly build of Foundry. It is recommended to use the latest stable version. To mute this warning set `FOUNDRY_DISABLE_NIGHTLY_WARNING` in your environment. 

No files changed, compilation skipped

Ran 2 tests for test/Counter.t.sol:CounterTest
[PASS] testFuzz_SetNumber(uint256) (runs: 256, μ: 28900, ~: 29289)
[PASS] test_Increment() (gas: 28783)
Suite result: ok. 2 passed; 0 failed; 0 skipped; finished in 3.76ms (2.69ms CPU time)

Ran 1 test suite in 11.96ms (3.76ms CPU time): 2 tests passed, 0 failed, 0 skipped (2 total tests)

# 如何让感觉上，体验更接近本地命令，更像直接使用forge？
# 临时方式：定义别名（当前终端有效，新打开终端就无效了）
alias forge='docker run --rm -v "$PWD":/app -w /app --entrypoint /usr/local/bin/forge foundry:latest'

# 永久方式：加入 ~/.bashrc 或 ~/.zshrc
# bash（Linux）方式
echo "alias forge='docker run --rm -v \"\$PWD\":/app -w /app --entrypoint /usr/local/bin/forge foundry:latest'" >> ~/.bashrc

# zsh（macOS）方式
echo "alias forge='docker run --rm -v \"\$PWD\":/app -w /app --entrypoint /usr/local/bin/forge foundry:latest'" >> ~/.zshrc

# 永久方式，需要重新加载配置：（不重新加载是无法生效的）
source ~/.bashrc  或 source ~/.zshrc

# 接着你就可以“像本地一样”使用 forge
forge init .
forge build
forge test
forge --version

# 如果想取消这种设置（临时方式）：unalias forge
# 如果想取消这种设置（永久方式）：或者在~/.bashrc 或 ~/.zshrc中删除

# 或者通过命令删除永久方式（清除后，需要重启终端）
# 删除 ~/.bashrc 中的 forge 别名（bash 用户）
sed -i '/alias forge/d' ~/.bashrc

# 删除 ~/.zshrc 中的 forge 别名（zsh 用户）
sed -i '' '/alias forge/d' ~/.zshrc

```

#### 验证

```bash
forge --version
```

#### 更新方式

```bash
docker pull ghcr.io/foundry-rs/foundry:latest
```

#### 卸载步骤

```bash
# 查看镜像
docker images

示例：
REPOSITORY                    TAG       IMAGE ID       CREATED        SIZE
foundry                       latest    44c6957ef5e3   5 days ago     406MB
ghcr.io/foundry-rs/foundry    latest    44c6957ef5e3   5 days ago     406MB
hello-world                   latest    1b44b5a3e06a   2 months ago   10.1kB

# 查看镜像容器
docker ps -a

示例：
CONTAINER ID   IMAGE                         COMMAND              CREATED       STATUS                     PORTS                                         NAMES
31ffe3cf7132   hello-world                   "/hello"             6 weeks ago   Exited (0) 6 weeks ago                                                   peaceful_ramanujan

# 删除容器（可选）
docker rm 31ffe3cf7132（容器ID）

# 删除镜像（可选）
docker rmi ghcr.io/foundry-rs/foundry:latest

示例：
docker rmi hello-world:latest 

Untagged: hello-world:latest
Untagged: hello-world@sha256:54e66cc1dd1fcb1c3c58bd8017914dbed8701e2d8c74d9262e26bd9cc1642d31
Deleted: sha256:1b44b5a3e06a9aae883e7bf25e45c100be0bb81a0e01b32de604f3ac44711634
Deleted: sha256:53d204b3dc5ddbc129df4ce71996b8168711e211274c785de5e0d4eb68ec3851

# 清理所有未使用的镜像（谨慎）
docker image prune -a
```

> **适用场景**：完全隔离、CI/CD 流水线、版本锁定、临时测试、避免污染本地环境。

---

## 四、安装方式对比总结
| 特性                 | foundryup | Homebrew | Cargo | 手动二进制 | Docker |
|----------------------|-----------|----------|-------|------------|--------|
| 官方推荐             | ✅         | ⚠️（次选） | ❌     | ❌           | ❌      |
| 一键安装             | ✅         | ✅         | ❌     | ❌           | ✅（运行即用） |
| 自动更新             | ✅         | ✅         | ❌     | ❌           | ❌（需 `pull`） |
| 全局可用             | ✅         | ✅         | ✅/❌   | ✅/❌         | ⚠️（需 alias） |
| 无需 Rust 环境       | ✅         | ✅         | ❌     | ✅           | ✅      |
| 支持离线安装         | ❌         | ❌         | ❌     | ✅           | ❌（需先 pull） |
| 版本精确控制         | ⚠️（最新/nightly） | ⚠️       | ✅     | ✅           | ✅（通过 tag） |
| 适合 CI/CD           | ✅         | ❌         | ⚠️     | ✅           | ✅      |
| 卸载简便性           | 中         | 高         | 高     | 中           | 高      |
| **环境隔离性**       | ❌         | ❌         | ❌     | ❌           | ✅      |
| **首次使用延迟**     | 中         | 中         | 高     | 低           | 高      |
| **磁盘占用**         | 小         | 小         | 大     | 小           | 大      |
| **跨平台一致性**     | 高         | ❌         | 高     | 高           | ✅      |

---

## 五、推荐选择建议

在安装 Foundry 工具链时，不同使用场景对易用性、可维护性、环境隔离和版本控制的需求各不相同。以下是针对各类典型使用场景的推荐安装方式，帮助开发者和团队选择最合适的方案。

| 使用场景                         | 推荐方式                     | 推荐理由                                                                 | 注意事项 |
|----------------------------------|------------------------------|--------------------------------------------------------------------------|----------|
| **普通开发者（快速上手）**        | `foundryup`                  | 官方推荐工具，安装简单，自动管理版本更新；支持一键安装 `forge`、`cast`、`anvil` 等全套工具。 | 需定期运行 `foundryup` 以获取最新版本。 |
| **macOS 用户偏好包管理**          | `Homebrew`                   | 与 macOS 生态集成良好，便于通过 `brew upgrade` 统一管理软件包；安装稳定、依赖清晰。 | 更新可能略滞后于官方发布，需等待公式更新。 |
| **Rust 开发者或项目贡献者**       | `Cargo`                      | 基于 Rust 生态，适合参与 Foundry 源码开发、调试或定制构建；可灵活指定分支/提交进行编译。 | 编译耗时较长，且需配置完整的 Rust 开发环境（`rustc`, `cargo`, `wasm` 等）。 |
| **企业级项目 / CI/CD 环境**       | **手动下载静态二进制文件 + 锁定版本号** | 实现精确的版本控制，确保构建可重现；适合与 CI 配置（如 GitHub Actions、GitLab CI）结合使用。 | 需手动管理版本升级与分发，建议配合脚本自动化。 |
| **临时使用 / 多项目隔离 / 无污染环境** | `Docker` 容器                | 环境隔离性强，避免本地污染；支持按需拉取特定版本镜像（如 `foundry:nightly-<hash>`）；适合演示、测试或并行开发多个版本项目。 | 需预先安装 Docker；构建镜像可能增加启动时间。 |

### 附加建议

- **多环境混合使用**：可在本地开发使用 `foundryup`，CI 中使用 Docker 或静态二进制，兼顾开发效率与部署一致性。
- **版本锁定实践**：无论使用哪种方式，**生产项目应明确锁定 Foundry 版本**（如通过 `foundry.toml` 中的 `profile.default.foundry_version` 字段），防止意外变更导致构建失败。
- **安全考虑**：避免在生产系统中使用自动更新机制（如 `foundryup`），推荐在受控环境中验证新版本后再升级。

> 💡 **提示**：可通过 `forge --version` 验证当前安装版本，并在项目中记录所用版本以确保团队一致性。

---