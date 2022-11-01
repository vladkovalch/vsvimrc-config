<img src="./resources/header.png">

<br/>

&nbsp; &nbsp; Here's a compilation of my personal preferences using Visual Studio's VsVim plugin, mainly focused on .NET development using ReSharper.

```vim
set ignorecase                   " Allows case insensetive search
set clipboard=unnamed            " Sets system synchronized clipboard register
set number                       " Activates the line numbering
set relativenumber               " Sets relative line numbers. Along with 'number' being set produces hybrid line number mode
set smartcase                    " Case insensitive search unless the search pattern contains an uppercase character
set cursorline                   " Highlights the current line

" Hides all glyph margin marks
set vsvim_hidemarks=<>[]^.'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ

" Disables recording feature
map q <NOP>

" Unbinds the Space key (as it used as a modificator in other mappings)
map <Space> <NOP>

" Space + w(indow) + p(in) - Toggles document's pin status
" Space + w(indows) + c(lose) + a(ll) - Closes all unpinned documents
noremap <Space>wp :vsc Window.PinTab<CR> 
noremap <Space>wc :vsc Window.CloseAllButPinned<CR> 

" Alt + j - Navigates to the next tab
" Alt + k - Navigates to the previous tab
" You might want to change these if you're using horizontal layout
noremap <A-j> :vsc Window.NextTab<CR>
noremap <A-k> :vsc Window.PreviousTab<CR>
noremap <C-T> :vsc Window.RestoreClosedTab<CR>

" Alt + Enter - Shows action indicators and action list
" Ctrl + Space - Provides a list of completions for the partial word typed by the user
noremap <A-CR> :vsc ReSharper_AltEnter<CR>
noremap <C-Space> :vsc Edit.CompleteWord<CR>
" ReSharper disabled:
" noremap <A-CR> :vsc View.QuickActions<CR>
" noremap <C-Space> :vsc Edit.CompleteWord<CR>

" Space + k + i(nfo) - Shows quick info tool tip
" Space + k + p(arameter) - Shows parameter info tool tip
noremap <Space>ki :vsc Edit.QuickInfo<CR>
noremap <Space>kp :vsc Edit.ParameterInfo<CR>

" Space + m(ark) + t(oggle) - Toggles bookmarks
" Space + m(arks) + a(ll) - Shows bookmarks list
noremap <Space>mt :vsc Edit.ToggleBookmark<CR>
noremap <Space>ma :vsc View.BookmarkWindow<CR>

" ] - Navigates to the next member / type / tag
" [ - Navigates to the previous member / type / tag
noremap ] :vsc ReSharper.ReSharper_GotoNextMember<CR>
noremap [ :vsc ReSharper.ReSharper_GotoPrevMember<CR>
" ReSharper disabled:
" noremap ] :vsc Edit.NextMethod<CR>
" noremap [ :vsc Edit.PreviousMethod<CR>

" [-] - Moves backwards through the navigation history
" [=] - Moves forwards through the navigation history
noremap - :vsc View.NavigateBackward<CR>
noremap = :vsc View.NavigateForward<CR>

" Improves navigation when wrapping
" by swapping 'j' with 'gj' and 'k' with 'gk'
nnoremap j gj
nnoremap gj j
nnoremap k gk
nnoremap gk k

" Alt + z - Toggles word wrap
noremap <A-z> :vsc Edit.ToggleWordWrap<CR>

" Space + d(eclaration) - Navigates to the declaration of a symbol from any symbol usage
" Space + i(mplementation) - Navigates to an actual implementations of types and members to locate the source code they execute
" Space + u(sage) - Displays all usages of one or more symbols in the solution and referenced assemblies
noremap <Space>d :vsc ReSharper.ReSharper_GotoDeclaration<CR>
noremap <Space>i :vsc ReSharper.ReSharper_GotoImplementations<CR>
noremap <Space>u :vsc ReSharper.ReSharper_FindUsages<CR>
" ReSharper disabled:
" noremap <Space>d :vsc Edit.GoToDefinition<CR>
" noremap <Space>i :vsc Edit.GoToImplementation<CR>
" noremap <Space>u :vsc Edit.FindAllReferences<CR>

" Space + f(ind) + t(ype) - Helps you find and navigate to the generic type declaration as well as to declarations of all generic parameters 
" Space + f(ind) + m(ember) - Helps you find and navigate to a particular method, field, property in the current document
" Space + f(ind) + e(xact) - Helps you find and navigate to any textual matches in your solution
noremap <Space>ff :vsc ReSharper.ReSharper_GotoType<CR>
noremap <Space>fm :vsc ReSharper.ReSharper_GotoFileMember<CR>
noremap <Space>fw :vsc ReSharper.ReSharper_GotoText<CR>
" ReSharper disabled:
" noremap <Space>ff :vsc Edit.GoToType<CR>
" noremap <Space>fm :vsc Edit.GoToMember<CR>
" noremap <Space>fw :vsc Edit.GoToAll<CR>

" Space + e(rror) - Navigates forwards through all issues detected in the current file
" Space + E(rror) - Navigates backwards through all issues detected in the current file
noremap <Space>e :vsc ReSharper.ReSharper_GotoNextErrorInSolution<CR>
noremap <Space>E :vsc ReSharper.ReSharper_GotoPrevErrorInSolution<CR>
" ReSharper disabled:
" noremap <Space>e :vsc View.NextError<CR>
" noremap <Space>E :vsc View.PreviousError<CR>

" Space + t(est) + r(un) - Runs unit tests from the current context
" Space + t(est) + a(ll) - Runs all the tests in the solution
" Space + t(est) + l(ast) - Repeats a previous test run
" Space + t(est) + f(ailed) - Runs only previously failed tests
" Space + t(est) + c(over) + a(ll) - Runs code coverage analysis of the solution
" Space + t(est) + d(ebug) - Starts debugging selected test
" Space + t(set) + s(how) + s(essions) - Shows unit test sessions window
" Space + t(set) + s(how) + c(overage) - Shows unit tests coverage results browser
noremap <Space>tr :vsc ReSharper.ReSharper_UnitTestRunFromContext<CR>
noremap <Space>ta :vsc ReSharper.ReSharper_UnitTestRunSolution<CR>
noremap <Space>tl :vsc ReSharper.ReSharper_UnitTestSessionRepeatPreviousRun<CR>
noremap <Space>tf :vsc TestExplorer.RunFailedTests<CR>
noremap <Space>tca :vsc ReSharper.ReSharper_CoverAllTestsFromSolution<CR>
noremap <Space>td :vsc ReSharper.ReSharper_UnitTestDebugContext<CR>
noremap <Space>tss :vsc ReSharper.ReSharper_ShowUnitTestSessions<CR>
noremap <Space>tsc :vsc ReSharper.ReSharper_ShowCoverageResultsBrowser<CR>
" ReSharper disabled:
" noremap <Space>tr :vsc TestExplorer.RunSelectedTests<CR>
" noremap <Space>ta :vsc TestExplorer.RunAllTests<CR>
" noremap <Space>tl :vsc TestExplorer.RepeatLastRun<CR>
" noremap <Space>tf :vsc TestExplorer.RunFailedTests<CR>
" noremap <Space>td :vsc TestExplorer.DebugSelectedTests<CR>
" noremap <Space>tss :vsc TestExplorer.ShowTestExplorer<CR>
" noremap <Space>tsc :vsc View.CodeCoverageResults<CR>

" Space + b(reakpoint) + t(oggle) - Toggles breakpoint 
" Space + b(reakpoints) + d(elete) - Disables all breakpoins
" Space + b(reakpoints) + e(nable) - Enables all breakpoints
" Space + b(reakpoints) + r(emove) - Removes all breakpoints
" Space + b(reakpoints) + a(ll) - Shows breakpoints list
noremap <Space>bt :vsc Debug.ToggleBreakpoint<CR>
noremap <Space>bd :vsc Debug.DisableAllBreakpoints<CR>
noremap <Space>be :vsc Debug.EnableAllBreakpoints<CR>
noremap <Space>br :vsc Debug.DeleteAllBreakpoints<CR>
noremap <Space>ba :vsc Debug.Breakpoints<CR>

" Space + s(tart) + b(uild) - Builds solution
" Space + s(tart) + c(lean) - Cleans solution
" Space + s(tart) + b(uild) + s(election) - Builds the project that is currently selected
" Space + s(tart) + c(lean) + s(election) - Cleans the project that is currently selected
" Space + s(tart) + d(ebug) - Starts with gebugging
" Space + s(tart) + r(un) - Runs a program without gebugging
" Space + s(tarted) + b(uild) + c(ancel) - Cancels building process
" Space + s(tarted) + d(ebug) + c(ancel) - Stops debugging
noremap <Space>sb :vsc Build.BuildSolution<CR>
noremap <Space>sc :vsc Build.CleanSolution<CR>
noremap <Space>sbs :vsc Build.BuildSelection<CR>
noremap <Space>scs :vsc Build.CleanSelection<CR>
noremap <Space>sd :vsc Debug.Start<CR>
noremap <Space>sr :vsc Debug.StartWithoutDebugging<CR>
noremap <Space>sbc :vsc Build.Cancel<CR>
noremap <Space>sdc :vsc Debug.StopDebugging<CR>

" Space + q(ick) + w(atch) - Shows QuickWatch dialog box
" Ctrl + Left - Moves execution pointer to selected statement
" Ctrl + Right - Steps over
" Ctrl + Down - Steps into
" Ctrl + Up - Steps out
nnoremap <Space>qw :vsc Debug.QuickWatch<CR>
nnoremap <C-Left> :vsc Debug.SetNextStatement<CR>
nnoremap <C-Right> :vsc Debug.StepOver<CR>
nnoremap <C-Down> :vsc Debug.StepInto<CR>
nnoremap <C-Up> :vsc Debug.StepOut<CR>

" Space + r(emove) + s(ort) - Removes and sorts usings
noremap <Space>rs :vsc Edit.RemoveAndSort<CR>

" Space + [/] - Comments/uncomments the current line
noremap <Space>/ :vsc ReSharper.ReSharper_LineComment<CR>
" ReSharper disabled:
" noremap <Space>/ :vsc Edit.ToggleLineComment<CR><ESC>

" Space + [.] - Adds a dot to the end of the current line
" Space + [,] - Adds a comma to the end of the current line
" Space + [;] - Adds a semicolumn to the end of the current line
" Space + x - Deletes the last character of the current line
noremap <Space>. A.
noremap <Space>, :s/\v\s*(,\s*)*$/,/<CR>
noremap <Space>; :s/\v\s*(;\s*)*$/;/<CR>
noremap <Space>x :s/.\{1}$//<CR>

" Space + n(umber) + a(bsolute) - Sets absolute line numbers 
" Space + n(umber) + r(elative) - Sets relative line numbers
noremap <Space>na :set rnu!<CR>
noremap <Space>nr :set rnu<CR>
```

<br/>

&nbsp; &nbsp; When composing this config file, I've been trying to come up with some abstract meanings behind the mappings so they could be more easily remembered. If you find some of them a bit off, feel free to adjust them to your taste. Also, I'm open to any suggestion on improving the config and bringing some new stuff in, so don't be shy to contact me.

ℹ️ If you're seeking a more detailed explanation of settings, see: https://github.com/VsVim/VsVim/wiki/Settings-Reference
