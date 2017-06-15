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


# Webpack config

    var path = require('path');
    var webpack = require('webpack');
    var ExtractTextPlugin = require('extract-text-webpack-plugin');

    var config = {

        watchOptions: {
            aggregateTimeout: 300,
            poll: 1000
        },
        resolve: {
            alias: {
                "store": path.resolve(__dirname, "assets/js/libs/store.min.js"),
            },
            extensions: ['.js', '.jsx']
        },
        devtool: 'eval-cheap-source-map',
        entry: {
            app: "./src/app.jsx",
            vendor: ["react", "react-dom", "store"]
        },
        output: {
            path: path.resolve(__dirname, 'assets/'),
            filename: "js/bundle.js"
        },
        plugins: [
            new ExtractTextPlugin('css/build-styles.css'),
            new webpack.optimize.OccurrenceOrderPlugin(),
            new webpack.ProvidePlugin({
                'store' : 'store',
                'window.store' : 'store',
                'react-slick' : 'react-slick'
            }),
            new webpack.optimize.CommonsChunkPlugin({
                name: 'vendor',
                filename: 'js/vendor.bundle.js'
            }),
            new webpack.DefinePlugin({
                'process.env': {
                    'NODE_ENV': JSON.stringify('production')
                }
            })
        ],

        module: {
            rules: [
                {
                    test: /\.jsx?$/,
                    exclude: /(node_modules)/,
                    loader: 'babel-loader'
                },
                {
                    test: /\.css$/,
                    loader:  ExtractTextPlugin.extract({
                        loader: 'css-loader?-url&importLoaders=1&modules=true&localIdentName=[name]_[local]_[sha1:hash:hex:5]',
                    }),
                }
            ]
        }

    };

    if (process.env.NODE_ENV === 'production') {

        config.devtool = 'source-map';

        config.plugins.push(new webpack.optimize.UglifyJsPlugin({
            compress: {
                warnings: false,
                screw_ie8: true,
                conditionals: true,
                unused: true,
                comparisons: true,
                sequences: true,
                dead_code: true,
                evaluate: true,
                if_return: true,
                join_vars: true,
            },
            output: {
                comments: false,
            },
        }));

    }

    module.exports = config;
