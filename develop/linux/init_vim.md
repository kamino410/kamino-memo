# init.vim

```vimrc
"ディレクトリ設定---------
let g:cache_home = empty($XDG_CACHE_HOME) ? expand('$HOME/.cache') : $XDG_CACHE_HOME
let g:config_home = empty($XDG_CONFIG_HOME) ? expand('$HOME/.config') : $XDG_CONFIG_HOME
let s:dein_cache_dir = g:cache_home . '/dein'

"deinのインストール-------
if &runtimepath !~# '/dein.vim'
  let s:dein_repo_dir = s:dein_cache_dir . '/repos/github.com/Shougo/dein.vim'

  if !isdirectory(s:dein_repo_dir)
      call system('git clone https://github.com/Shougo/dein.vim ' . shellescape(s:dein_repo_dir))
  endif

  execute 'set runtimepath^=' . s:dein_repo_dir
endif

" dein設定--------------
let g:dein#install_max_processes = 16
let g:dein#install_progress_type = 'title'
let g:dein#install_message_type = 'none'
let g:dein#enable_notification = 1

if dein#load_state(s:dein_cache_dir)
    call dein#begin(s:dein_cache_dir)

    let s:toml_dir = g:config_home . '/dein'

    call dein#load_toml(s:toml_dir . '/plugins.toml', {'lazy': 0})
    call dein#load_toml(s:toml_dir . '/lazy.toml', {'lazy': 1})
    if has('nvim')
        call dein#load_toml(s:toml_dir . '/neovim.toml', {'lazy': 1})
    endif

    call dein#end()
    call dein#save_state()
endif

if has('vim_starting') && dein#check_install()
    call dein#install()
endif

"tab/indent設定----------
set tabstop=4     "tabの幅
set expandtab     "tabを半角スペースに置換
set autoindent    "改行時に前の行のインデントを引き継ぐ
set shiftwidth=4  "自動インデントで下げる幅
set smartindent   "改行時、括弧などに応じてインデントを自動で増減する

"ビープ音を消す設定--------
set visualbell    "ビープ音をすべて視覚表示に置き換え
set t_vb=         "エラーメッセージ（何も出さない）

```
