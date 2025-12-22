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
- 在过老的 pip 版本（Ubuntu20.04 下）由于 pip 的依赖解析问题，jedi-language-server@0.42.0 无法正确安装 lsprotocol==2023.0.1
    > 解决方案：
    > 1. 手动进入 `~/.local/share/nvim/mason/packages/jedi-language-server/venv/` `source bin/activate && pip install lsprotocol==2023.0.1`
    > 2. 使用 pyenv 安装 python 3.11，并在 .bashrc 指定 nvim 使用新版 python
  > ```
  > curl -fsSL https://pyenv.run | bash
  > pyenv install 3.11.9
  > echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
  > echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
  > echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
  > echo alias vim='PYENV_VERSION=3.11.9 pyenv exec nvim' >> .bashrc
  > ```

