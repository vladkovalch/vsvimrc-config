<img src="./resources/header.png">

<br/>

```vim
set clipboard=unnamed            " Sets system synchronized clipboard register
set number                       " Activates the line numbering
set relativenumber               " Sets relative line numbers. Along with `number` being set produces hybrid line number mode
set cursorline                   " Highlight the current line
set ignorecase                   " Allow case insensetive search
set smartcase                    " Case insensitive search unless the search pattern contains an uppercase character

" Sets the leader key
let mapleader="\<Space>"

" Unibinds the Space key (as it used as a leader key)
nnoremap <Space> <NOP>

" `Esc` - Remove search highlights
nnoremap <Esc> :nohl<CR>

" `<Alt> + z` - Toggle word wrap
noremap <A-z> :vsc Edit.ToggleWordWrap<CR>

" `<leader> + .` - Add a dot to the end of the current line
" `<leader> + ,` - Add a comma to the end of the current line
" `<leader> + ;` - Add a semicolumn to the end of the current line
" `<leader> + x` - Delete the last character of the current line
noremap <leader>. :A.<CR>
noremap <leader>, :s/\v\s*(;\s*)*$/;/<CR>
noremap <leader>; :s/\v\s*(,\s*)*$/,/<CR>
noremap <leader>x :s/.\{1}$//<CR>

" `<leader> + n(umber) + a(bsolute)` - Set absolute line numbers 
" `<leader> + n(umber) + r(elative)` - Set relative line numbers
noremap <leader>na :set rnu!<CR>
noremap <leader>nr :set rnu<CR>

" `<leader> + w(indow) + p(in)` - Toggle document's pin status
" `<leader> + w(indows) + c(lose) + a(ll)` - Close all unpinned documents
noremap <leader>wp :vsc Window.PinTab<CR> 
noremap <leader>wca :vsc Window.CloseAllButPinned<CR> 

" `-` - Collapse current region
" `=` - Expand current region
" `_` - Collapse all
" `+` - Expand all
noremap - :vsc Edit.CollapseCurrentRegion<CR> 
noremap = :vsc Edit.ExpandCurrentRegion<CR> 
noremap _ :vsc Edit.CollapsetoDefinitions<CR> 
noremap + :vsc Edit.ExpandAllOutlining<CR> 

" `<Alt> + j` - Navigate to the next tab
" `<Alt> + k` - Navigate to the previous tab
" You might want to change these if you prefer horizontal tabs loayout
noremap <A-j> :vsc Window.NextTab<CR>
noremap <A-k> :vsc Window.PreviousTab<CR>
"noremap <A-l> :vsc Window.NextTab<CR>
"noremap <A-h> :vsc Window.PreviousTab<CR>

" `<Alt> + <Enter>` - Show action indicators and action list
" `<Ctrl> + <Space>` - Provide a list of completions for the partial word typed by the user
noremap <A-CR> :vsc ReSharper_AltEnter<CR>
noremap <C-Space> :vsc Edit.CompleteWord<CR>
" ReSharper disabled:
" noremap <A-CR> :vsc View.QuickActions<CR>
" noremap <C-Space> :vsc Edit.CompleteWord<CR>

" `<leader> + r(emove) + s(ort)` - Remove and sorts usings
noremap <leader>rs :vsc Edit.RemoveAndSort<CR>

" `<leader> + (quic)k + i(nfo)` - Show quick info tool tip
" `<leader> + (quic)k + p(arameter)` - Show parameter info tool tip
noremap <leader>ki :vsc Edit.QuickInfo<CR>
noremap <leader>kp :vsc Edit.ParameterInfo<CR>

" `m(ark)` - Navigate forwards through bookmarks
" `M(ark)` - Navigate backwards through bookmarks
" `<leader> + m + m(ark)` - Toggle bookmarks
" `<leader> + m(arks) + r(emove)` - Remove all bookmarks
" `<leader> + m(arks) + a(ll)` - Show bookmarks list
noremap m :vsc Edit.NextBookmark<CR>
noremap M :vsc Edit.PreviousBookmark<CR>
noremap <leader>mm :vsc Edit.ToggleBookmark<CR>
noremap <leader>mr :vsc Edit.ClearBookmarks<CR>
noremap <leader>ma :vsc View.BookmarkWindow<CR>

" `]` - Navigate to the next member / type / tag
" `[` - Navigate to the previous member / type / tag
noremap ] :vsc ReSharper.ReSharper_GotoNextMember<CR>
noremap [ :vsc ReSharper.ReSharper_GotoPrevMember<CR>
" ReSharper disabled:
" noremap ] :vsc Edit.NextMethod<CR>
" noremap [ :vsc Edit.PreviousMethod<CR>

" `<Ctrl> + -` - Move backwards through the navigation history
" `<Ctrl> + =` - Move forwards through the navigation history
noremap <C>- :vsc View.NavigateBackward<CR>
noremap <C>= :vsc View.NavigateForward<CR>

" Improves navigation when wrapping
" by swapping `j` with `gj` and `k` with `gk`
nnoremap j gj
nnoremap gj j
nnoremap k gk
nnoremap gk k

" `<leader> + d(eclaration)` - Navigate to the declaration of a symbol from any symbol usage
" `<leader> + i(mplementation)` - Navigate to an actual implementations of types and members to locate the source code they execute
" `<leader> + u(sage)` - Display all usages of one or more symbols in the solution and referenced assemblies
noremap <leader>d :vsc ReSharper.ReSharper_GotoDeclaration<CR>
noremap <leader>i :vsc ReSharper.ReSharper_GotoImplementations<CR>
noremap <leader>u :vsc ReSharper.ReSharper_FindUsages<CR>
" ReSharper disabled:
" noremap <leader>d :vsc Edit.GoToDefinition<CR>
" noremap <leader>i :vsc Edit.GoToImplementation<CR>
" noremap <leader>u :vsc Edit.FindAllReferences<CR>

" `<leader> + f(ind) + f(iles)` - Find and navigate to the generic type declaration as well as to declarations of all generic parameters 
" `<leader> + f(ind) + m(ember)` - Find and navigate to a particular method, field, property in the current document
" `<leader> + f(ind) + w(ord)` - Find and navigate to any textual matches in your solution
noremap <leader>ff :vsc ReSharper.ReSharper_GotoType<CR>
noremap <leader>fm :vsc ReSharper.ReSharper_GotoFileMember<CR>
noremap <leader>fw :vsc ReSharper.ReSharper_GotoText<CR>
" ReSharper disabled:
" noremap <leader>ff :vsc Edit.GoToType<CR>
" noremap <leader>fm :vsc Edit.GoToMember<CR>
" noremap <leader>fw :vsc Edit.GoToAll<CR>

" `<leader> + e(rror)` - Navigate forwards through all issues detected in the current file
" `<leader> + E(rror)` - Navigate backwards through all issues detected in the current file
noremap <leader>e :vsc ReSharper.ReSharper_GotoNextErrorInSolution<CR>
noremap <leader>E :vsc ReSharper.ReSharper_GotoPrevErrorInSolution<CR>
" ReSharper disabled:
" noremap <leader>e :vsc View.NextError<CR>
" noremap <leader>E :vsc View.PreviousError<CR>

" `<leader> + t(est) + r(un)` - Run unit tests from the current context
" `<leader> + t(est) + a(ll)` - Run all the tests in the solution
" `<leader> + t(est) + l(ast)` - Repeat a previous test run
" `<leader> + t(est) + f(ailed)` - Run only previously failed tests
" `<leader> + t(est) + c(over) + a(ll)` - Run code coverage analysis of the solution
" `<leader> + t(est) + d(ebug)` - Start debugging selected test
" `<leader> + t(set) + s(how) + s(essions)` - Show unit test sessions window
" `<leader> + t(set) + s(how) + c(overage)` - Show unit tests coverage results browser
noremap <leader>tr :vsc ReSharper.ReSharper_UnitTestRunFromContext<CR>
noremap <leader>ta :vsc ReSharper.ReSharper_UnitTestRunSolution<CR>
noremap <leader>tl :vsc ReSharper.ReSharper_UnitTestSessionRepeatPreviousRun<CR>
noremap <leader>tf :vsc TestExplorer.RunFailedTests<CR>
noremap <leader>tca :vsc ReSharper.ReSharper_CoverAllTestsFromSolution<CR>
noremap <leader>td :vsc ReSharper.ReSharper_UnitTestDebugContext<CR>
noremap <leader>tss :vsc ReSharper.ReSharper_ShowUnitTestSessions<CR>
noremap <leader>tsc :vsc ReSharper.ReSharper_ShowCoverageResultsBrowser<CR>
" ReSharper disabled:
" noremap <leader>tr :vsc TestExplorer.RunSelectedTests<CR>
" noremap <leader>ta :vsc TestExplorer.RunAllTests<CR>
" noremap <leader>tl :vsc TestExplorer.RepeatLastRun<CR>
" noremap <leader>tf :vsc TestExplorer.RunFailedTests<CR>
" noremap <leader>td :vsc TestExplorer.DebugSelectedTests<CR>
" noremap <leader>tss :vsc TestExplorer.ShowTestExplorer<CR>
" noremap <leader>tsc :vsc View.CodeCoverageResults<CR>

" `<leader> + b + b(reakpoint)` - Toggle breakpoint 
" `<leader> + b(reakpoints) + d(isable)` - Disable all breakpoins
" `<leader> + b(reakpoints) + e(nable)` - Enable all breakpoints
" `<leader> + b(reakpoints) + r(emove)` - Remove all breakpoints
" `<leader> + b(reakpoints) + a(ll)` - Show breakpoints list
noremap <leader>bb :vsc Debug.ToggleBreakpoint<CR>
noremap <leader>bd :vsc Debug.DisableAllBreakpoints<CR>
noremap <leader>be :vsc Debug.EnableAllBreakpoints<CR>
noremap <leader>br :vsc Debug.DeleteAllBreakpoints<CR>
noremap <leader>ba :vsc Debug.Breakpoints<CR>

" `<leader> + s(tart) + b(uild)` - Build solution
" `<leader> + s(tart) + c(lean)` - Clean solution
" `<leader> + s(tart) + b(uild)` + s(election) - Build the project that is currently selected
" `<leader> + s(tart) + c(lean)` + s(election) - Clean the project that is currently selected
" `<leader> + s(tart) + d(ebug)` - Start with gebugging
" `<leader> + s(tart) + r(un)` - Run a program without gebugging
" `<leader> + s(tarted) + b(uild) + c(ancel)` - Cancel building process
" `<leader> + s(tarted) + d(ebug) + c(ancel)` - Stop debugging
noremap <leader>sb :vsc Build.BuildSolution<CR>
noremap <leader>sc :vsc Build.CleanSolution<CR>
noremap <leader>sbs :vsc Build.BuildSelection<CR>
noremap <leader>scs :vsc Build.CleanSelection<CR>
noremap <leader>sd :vsc Debug.Start<CR>
noremap <leader>sr :vsc Debug.StartWithoutDebugging<CR>
noremap <leader>sbc :vsc Build.Cancel<CR>
noremap <leader>sdc :vsc Debug.StopDebugging<CR>

" `<leader> + q(ick) + w(atch)` - Show QuickWatch dialog box
" `<Ctrl> + <Left>` - Move execution pointer to selected statement
" `<Ctrl> + <Right>` - Step over
" `<Ctrl> + <Down>` - Step into
" `<Ctrl> + <Up>` - Step out
nnoremap <Leader>qw :vsc Debug.QuickWatch<CR>
nnoremap <C-Left> :vsc Debug.SetNextStatement<CR>
nnoremap <C-Right> :vsc Debug.StepOver<CR>
nnoremap <C-Down> :vsc Debug.StepInto<CR>
nnoremap <C-Up> :vsc Debug.StepOut<CR>

" `<leader> + /` - Comment/uncomment the current line
noremap <leader>/ :vsc ReSharper.ReSharper_LineComment<CR>
" ReSharper disabled:
" noremap <leader>/ :vsc Edit.ToggleLineComment<CR>
```

<br/>
