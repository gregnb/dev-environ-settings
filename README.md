# Sublime 3 

Packages to install. Tools -> Command Palette -> Type "Install Package"

    Babel
    SublimeLinter
    SublimeLinter-contrib-eslint

User Settings:

    {
        "color_scheme": "Packages/User/SublimeLinter/Monokai Phoenix (SL).tmTheme",
        "dpi_scale": 1.2,
        "font_size": 13,
        "ignored_packages":
        [
            "Vintage"
        ]
    }


# ESLint install & config

npm install eslint babel-eslint eslint-plugin-import eslint-plugin-react -g


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
