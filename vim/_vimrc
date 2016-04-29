set nocompatible
set number
set title
set ruler
set autoindent
set smartindent
set tabstop=2
set shiftwidth=2
set expandtab
set backspace=indent,eol,start
set encoding=utf-8

" Dein
if filereadable(expand('$HOME/.vim/vimrc.dein')) " ファイルが読み込み可能かチェック
  source $HOME/.vim/vimrc.dein " .vimrcファイル読み込み
endif

" NeoBundle
"if filereadable(expand('$HOME/.vim/vimrc.neobundle')) " ファイルが読み込み可能かチェック
"  source $HOME/.vim/vimrc.neobundle " .vimrcファイル読み込み
"
"  if filereadable(expand('$HOME/.vim/vimrc.plugin'))
"    source $HOME/.vim/vimrc.plugin
"  endif
"endif

filetype plugin indent on
set t_Co=256
syntax on
colorscheme jellybeans

" Unite
let g:unite_enable_start_insert=1
let g:unite_source_history_yank_enable =1
let g:unite_source_file_mru_limit = 200
nnoremap <silent> ,uy :<C-u>Unite history/yank<CR>
nnoremap <silent> ,ub :<C-u>Unite buffer<CR>
nnoremap <silent> ,uf :<C-u>UniteWithBufferDir -buffer-name=files file<CR>
nnoremap <silent> ,ur :<C-u>Unite -buffer-name=register register<CR>
nnoremap <silent> ,uu :<C-u>Unite file_mru buffer<CR>
"noremap <C-P> :Unite buffer<CR>
"noremap <C-N> :Unite -buffer-name=file file<CR>
"noremap <C-Z> :Unite file_mru<CR>

"------------------------------------
"" Unite-rails.vim
"------------------------------------
""{{{
function! UniteRailsSetting()
  nnoremap <buffer><C-H><C-H><C-H>  :<C-U>Unite rails/view<CR>
  nnoremap <buffer><C-H><C-H>       :<C-U>Unite rails/model<CR>
  nnoremap <buffer><C-H>            :<C-U>Unite rails/controller<CR>

  nnoremap <buffer><C-H>c           :<C-U>Unite rails/config<CR>
  nnoremap <buffer><C-H>s           :<C-U>Unite rails/spec<CR>
  nnoremap <buffer><C-H>m           :<C-U>Unite rails/db -input=migrate<CR>
  nnoremap <buffer><C-H>l           :<C-U>Unite rails/lib<CR>
  nnoremap <buffer><expr><C-H>g     ':e '.b:rails_root.'/Gemfile<CR>'
  nnoremap <buffer><expr><C-H>r     ':e '.b:rails_root.'/config/routes.rb<CR>'
  nnoremap <buffer><expr><C-H>se    ':e '.b:rails_root.'/db/seeds.rb<CR>'
  nnoremap <buffer><C-H>ra          :<C-U>Unite rails/rake<CR>
  nnoremap <buffer><C-H>h           :<C-U>Unite rails/heroku<CR>
endfunction
aug MyAutoCmd
  au User Rails call UniteRailsSetting()
aug END
"}}}

"------------------------------------
"" vim-rails
"------------------------------------
"""{{{
"有効化
let g:rails_default_file='config/database.yml'
let g:rails_level = 4
let g:rails_mappings=1
let g:rails_modelines=0
" let g:rails_some_option = 1
let g:rails_statusline = 1
" let g:rails_subversion=0
" let g:rails_syntax = 1
" let g:rails_url='http://localhost:3000'
" let g:rails_ctags_arguments='--languages=-javascript'
" let g:rails_ctags_arguments = ''
function! SetUpRailsSetting()
  nnoremap <buffer><Space>r :R<CR>
  nnoremap <buffer><Space>a :A<CR>
  nnoremap <buffer><Space>m :Rmodel<Space>
  nnoremap <buffer><Space>c :Rcontroller<Space>
  nnoremap <buffer><Space>v :Rview<Space>
  nnoremap <buffer><Space>p :Rpreview<CR>
endfunction

aug MyAutoCmd
  au User Rails call SetUpRailsSetting()
aug END

aug RailsDictSetting
  au!
aug END
"}}}
"
" statusline
set laststatus=2
if filereadable(expand('$HOME/.vim/vimrc.lightline'))
  source $HOME/.vim/vimrc.lightline
end

" NERDTree
nnoremap <silent><C-e> :NERDTreeTabsToggle<CR>
let NERDTreeQuitOnOpen=1

" Split Window
nnoremap <silent><C-s>s :split<CR>
nnoremap <silent><C-s><C-s> :split<CR>
nnoremap <silent><C-s>v :vsplit<CR>
nnoremap <silent><C-h> <C-w>h<CR>
nnoremap <silent><C-j> <C-w>j<CR>
nnoremap <silent><C-k> <C-w>k<CR>
nnoremap <silent><C-l> <C-w>l<CR>

" Buffer
nnoremap <silent><Space> :bn<CR>

" 末尾の空行削除
autocmd BufWritePre * call s:remove_line_in_last_line()
function! s:remove_line_in_last_line()
  if getline('$') == ""
    $delete _
  endif
endfunction

" syntastic
let g:syntastic_mode_map = { 'mode': 'passive',
      \ 'active_filetypes': ['ruby'] }
let g:syntastic_ruby_checkers = ['rubocop']

augroup AlpacaTags
  autocmd!
  if exists(':Tags')
    autocmd BufWritePost Gemfile TagsBundle
    autocmd BufEnter * TagsSet
    " 毎回保存と同時更新する場合はコメントを外す
    autocmd BufWritePost * TagsUpdate
  endif
augroup END

" coffee
au BufRead,BufNewFile,BufReadPre *.coffee   set filetype=coffee
