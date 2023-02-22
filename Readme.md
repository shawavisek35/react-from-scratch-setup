npm init -y
npm install react react-dom
npm install @babel/core @babel/preset-env @babel/preset-react babel-loader

setup the babel file
add a file .babelrc
add {
  "presets": ["@babel/preset-react", "@babel/preset-env"]
}

npm install webpack webpack-cli webpack-dev-server

create a webpack.config.js file

add this following lines
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");

module.exports = {
  entry: "./src/index.js",
  output: {
    filename: "bundle.[hash].js",
    path: path.resolve(__dirname, "dist"),
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/index.html",
    }),
  ],
  resolve: {
    modules: [__dirname, "src", "node_modules"],
    extensions: ["*", ".js", ".jsx", ".tsx", ".ts"],
  },
  module: {
    rules: [
      {
        test: /\.jsx?$/,
        exclude: /node_modules/,
        loader: require.resolve("babel-loader"),
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.png|svg|jpg|gif$/,
        use: ["file-loader"],
      },
    ],
  },
};

npm i html-webpack-plugin path

npm i file-loader css-loader style-loader

Add src/index.js src/App.js src/App.css and test your react app

Hurrah!!!!!!!!!!!