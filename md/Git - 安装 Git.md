> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [git-scm.com](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)

> 在你开始使用 Git 前，需要将它安装在你的计算机上。 即便已经安装，最好将它升级到最新的版本。 你可以通过软件包或者其它安装程序来安装，或者下载源码编译安装。

安装 Git
------

在你开始使用 Git 前，需要将它安装在你的计算机上。 即便已经安装，最好将它升级到最新的版本。 你可以通过软件包或者其它安装程序来安装，或者下载源码编译安装。

<table><tbody><tr><td><p>Note</p></td><td><p>本书写作时使用的 Git 版本为 <strong>2.8.0</strong>。 我们使用的大部分命令仍然可以在很古老的 Git 版本上使用，但也有少部分命令不好用或者在旧版本中的行为有差异。 因为 Git 在保持向后兼容方面表现很好，本书使用的这些命令在 2.8 之后的版本应该有效。</p></td></tr></tbody></table>

### 在 Linux 上安装

如果你想在 Linux 上用二进制安装程序来安装基本的 Git 工具，可以使用发行版包含的基础软件包管理工具来安装。 以 Fedora 为例，如果你在使用它（或与之紧密相关的基于 RPM 的发行版，如 RHEL 或 CentOS），你可以使用 `dnf`：

```
$ sudo dnf install git-all

```

如果你在基于 Debian 的发行版上，如 Ubuntu，请使用 `apt`：

```
$ sudo apt install git-all

```

### 在 macOS 上安装

在 Mac 上安装 Git 有多种方式。 最简单的方法是安装 Xcode Command Line Tools。 Mavericks （10.9） 或更高版本的系统中，在 Terminal 里尝试首次运行'git' 命令即可。

如果没有安装过命令行开发者工具，将会提示你安装。

![](https://git-scm.com/book/en/v2/images/git-osx-installer.png)

Figure 7. Git macOS Installer.

你也可以将它作为 GitHub for macOS 的一部分来安装。 它们的图形化 Git 工具有一个安装命令行工具的选项。 你可以从 GitHub for macOS 网站下载该工具，网址为 [https://mac.github.com](https://mac.github.com/)。

### 在 Windows 上安装

另一个简单的方法是安装 GitHub Desktop。 该安装程序包含图形化和命令行版本的 Git。 它也能支持 Powershell，提供了稳定的凭证缓存和健全的换行设置。 稍后我们会对这方面有更多了解，现在只要一句话就够了，这些都是你所需要的。 你可以在 GitHub for Windows 网站下载，网址为 [GitHub Desktop 网站](https://desktop.github.com/)。

### 从源代码安装

有人觉得从源码安装 Git 更实用，因为你能得到最新的版本。 二进制安装程序倾向于有一些滞后，当然近几年 Git 已经成熟，这个差异不再显著。

如果你想从源码安装 Git，需要安装 Git 依赖的库：autotools、curl、zlib、openssl、expat 和 libiconv。 如果你的系统上有 `dnf` （如 Fedora）或者 `apt`（如基于 Debian 的系统）， 可以使用对应的命令来安装最少的依赖以便编译并安装 Git 的二进制版：

```
$ sudo dnf install dh-autoreconf curl-devel expat-devel gettext-devel \
  openssl-devel perl-devel zlib-devel
$ sudo apt-get install dh-autoreconf libcurl4-gnutls-dev libexpat1-dev \
  gettext libz-dev libssl-dev

```

为了添加文档的多种格式（doc、html、info），需要以下附加的依赖：

```
$ sudo dnf install asciidoc xmlto docbook2X
$ sudo apt-get install asciidoc xmlto docbook2x

```

<table><tbody><tr><td><p>Note</p></td><td><p>使用 RHEL 和 RHEL 衍生版，如 CentOS 和 Scientific Linux 的用户需要 <a href="https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F">开启 EPEL 库</a> 以便下载 <code>docbook2X</code> 包。</p></td></tr></tbody></table>

如果你使用基于 Debian 的发行版（Debian/Ubuntu/Ubuntu-derivatives），你也需要 `install-info` 包：

```
$ sudo apt-get install install-info

```

如果你使用基于 RPM 的发行版（Fedora/RHEL/RHEL 衍生版），你还需要 `getopt` 包 （它已经在基于 Debian 的发行版中预装了）：

```
$ sudo dnf install getopt

```

此外，如果你使用 Fedora/RHEL/RHEL 衍生版，那么你需要执行以下命令：

```
$ sudo ln -s /usr/bin/db2x_docbook2texi /usr/bin/docbook2x-texi

```

以此来解决二进制文件名的不同。

接着，编译并安装：

```
$ tar -zxf git-2.8.0.tar.gz
$ cd git-2.8.0
$ make configure
$ ./configure --prefix=/usr
$ make all doc info
$ sudo make install install-doc install-html install-info

```

完成后，你可以使用 Git 来获取 Git 的更新：

```
$ git clone git://git.kernel.org/pub/scm/git/git.git

```