Git Log Recipes
===============
Collection of git log formatting aliases found on the interwebs (mostly from stackoverflow)

Super basic git log
---------------
    git log --graph --oneline

Styles
---------------
*[Pavel Shved](http://coldattic.info)*

    git log --graph --full-history --all --pretty=format:"%h%x09%d%x20%s"

    git log --graph --full-history --all --color --pretty=format:"%x1b[31m%h%x09%x1b[32m%d%x1b[0m%x20%s""]]]"

    git log --graph --full-history --all --color --date=short --pretty=format:"%x1b[31m%h%x09%x1b[32m%d%x1b[0m%x20%ad %s""]]]"

*[Yeo](http://blog.eugene-yeo.in/)*

    git log --graph --pretty=format:'%Cred%h%Creset %ad %s %C(yellow)%d%Creset %C(bold blue)<%an>%Creset' --date=short

    git log --graph --full-history --all --pretty=format:'%Cred%h%Creset %ad %s %C(yellow)%d%Creset %C(bold blue)<%an>%Creset' --date=short

*[Slipp D. Thompson](http://slippyd.com)*

    git log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all

    git log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all

*[kaoru](http://d.hatena.ne.jp/coiledcoil)*

    git log --graph --date-order -C -M --pretty=format:"<%h> %ad [%an] %Cgreen%d%Creset %s" --all --date=short

    git log --graph --format = format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(bold white)— %an%C(reset)%C(bold yellow)%d%C(reset)' --abbrev-commit --date = relative

    git log --graph --format =format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(white)%s%C(reset) %C(bold white)— %an%C(reset)' --abbrev-commit


*gospes*

    git log --all --graph --decorate=short --color --format=format:'%C(bold blue)%h%C(reset) %C(auto)%d%C(reset)\n         %C(black)[%cr]%C(reset)  %x09%C(black)%an: %s %C(reset)'`

    [alias]
        logx = log --all --graph --decorate=short --color --format=format:'%C(bold blue)%h%C(reset)+%C(dim black)(%cr)%C(reset)+%C(auto)%d%C(reset)++\n+++       %C(bold black)%an%C(reset)%C(black): %s%C(reset)'
        stree = !bash -c '"                                                                             \
        while IFS=+ read -r hash time branch message; do                                            \
            timelength=$(echo \"$time\" | sed -r \"s:[^ ][[]([0-9]{1,2}(;[0-9]{1,2})?)?m::g\");     \
            timelength=$(echo \"16+${#time}-${#timelength}\" | bc);                                 \
            printf \"%${timelength}s    %s %s %s\n\" \"$time\" \"$hash\" \"$branch\" \"\";          \
        done < <(git logx && echo);"'

    [alias]
        logx = log --all --graph --decorate=short --color --format=format:'%C(bold blue)%h%C(reset)+%C(dim black)(%cr)%C(reset)+%C(auto)%d%C(reset)++\n+++       %C(bold black)%an%C(reset)%C(black): %s%C(reset)'
        vtree = !bash -c '"                                                                             \
        while IFS=+ read -r hash time branch message; do                                            \
        timelength=$(echo \"$time\" | sed -r \"s:[^ ][[]([0-9]{1,2}(;[0-9]{1,2})?)?m::g\");     \
        timelength=$(echo \"16+${#time}-${#timelength}\" | bc);                                 \
        printf \"%${timelength}s    %s %s %s\n\" \"$time\" \"$hash\" \"$branch\" \"$message\";  \
        done < <(git logx && echo);"'

*albfan*

    [alias]
        #quick look at all repo
        loggsa = log --color --date-order --graph --oneline --decorate --simplify-by-decoration --all

        #quick look at active branch (or refs pointed)
        loggs  = log --color --date-order --graph --oneline --decorate --simplify-by-decoration

        #extend look at all repo
        logga  = log --color --date-order --graph --oneline --decorate --all

        #extend look at active branch
        logg   = log --color --date-order --graph --oneline --decorate

        #Look with date
        logda  = log --color --date-order --graph --format=\"%C(yellow bold)%h%Creset %C(blue bold)%ad%Creset %Cred%d%Creset %s\" --all
        logd   = log --color --date-order --graph --format=\"%C(yellow bold)%h%Creset %C(blue bold)%ad%Creset %Cred%d%Creset %s\"        

        #Look with relative date
        logdar = log --color --date-order --graph --format=\"%C(yellow bold)%h%Creset %C(blue bold)%ar%Creset %Cred%d%Creset %s\" --all
        logdr = log --color --date-order --graph --format=\"%C(yellow bold)%h%Creset %C(blue bold)%ar%Creset %Cred%d%Creset %s\"  

Source links
---------------
- https://www.kernel.org/pub/software/scm/git/docs/git-log.html
- https://stackoverflow.com/q/1838873
- https://stackoverflow.com/q/1057564

 To-Do
---------------
- Add images.
