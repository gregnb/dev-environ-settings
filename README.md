# Sublime 3 

Packages to install. Tools -> Command Palette -> Type "Install Package"

    Babel
    Less
    Color Highlighter
    SublimeLinter
    SublimeLinter-contrib-eslint

User Settings:

    {
        "color_scheme": "Packages/User/SublimeLinter/Monokai Phoenix (SL).tmTheme",
        "dpi_scale": 1.2,
        "font_size": 13,
        "tab_size": 2,
        "translate_tabs_to_spaces": true,
        "ignored_packages":
        [
            "Vintage"
        ]
    }

Color Highlighter Settings:

    {
      "ha_style":"filled"
    }

# VIM/OH MY ZSH 

    git clone https://github.com/amix/vimrc.git ~/.vim_runtime
    sh ~/.vim_runtime/install_awesome_vimrc.sh
    
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
    Open ~/.zshrc and set theme to:
        ZSH_THEME="agnoster"
   
    git clone https://github.com/powerline/fonts.git
    ./install.sh
     
    Then if using iTerm2 make sure to update to Powerline Font
    
# GIT

    git config --global user.email gregnb@gregnb.com
    git config --global user.name "Gregory N"

    git config --global mergetool.prompt false
    git config --global mergetool.keepBackup false
    git config --global merge.conflictstyle diff3
    
    git config --global core.editor /usr/bin/vim


# ESLint install & config

    npm install eslint babel-eslint eslint-plugin-import eslint-plugin-react -g

## .eslintrc ##

    {
        "parser": "babel-eslint",
        "extends": [
          "eslint:recommended",
          "plugin:import/recommended",
          "plugin:react/recommended"
        ],
        "parserOptions": {
          "ecmaVersion": 6,
          "sourceType": "module",
          "ecmaFeatures": {
            "jsx": true,
            "experimentalObjectRestSpread": true
          },
        },
        "env": {
          "browser": true,
          "mocha": true,
          "node": true
        },
        "rules": {
          "valid-jsdoc": 2,
          "react/jsx-uses-react": 1,
          "react/jsx-no-undef": 2,
          "react/jsx-wrap-multilines": 2
        },
        "plugins": [
          "import",
          "react"
        ]
    }

