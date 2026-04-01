configuration for neovim, test on linux, shoul working in windows



# 如何使用这个仓库？

将 `init.vim` 中的内容复制到你自己的 `init.vim`，然后访问
[vim-plug](https://github.com/junegunn/vim-plug) 按照其中
提到的方式安装 vim-plug。

_e.x. in linux_
```
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
```

接下来启动 nvim 在其中使用 `:PlugInstall` 安装所有用到的插件。

然后启动 `:Mason` 安装对应的 lsp 这样就可以使用 LSP 提供的转跳，
纠错等功能，也能搭配补全插件提供良好的补全体验。

# 值得注意

这个版本并未经过测试，但是有已知问题：
1. 现在强依赖 tree-sitter-cli，需要使用 cargo/npm 安装
2. pre-build 的 nvim 以及 tree-sitter 是 build against 新版本的 glibc，在老系统(ubuntu 20.04)上会出现兼容性问题
