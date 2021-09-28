# BingLingGroup.github.io
This blog is powered by [Hexo][Hexodocs] and [hexo-theme-material][HTM].

These are the necessary files which can generate the blog of BingLingFanSub. Remember to replace [style.css](themes/material/source/css/style.css) and  [style.min.css](themes/material/source/css/style.min.css) after you finished using these commands below. These 2 .css files are changed specifically to highlight code using hexo-prism-plugin successfully.

The commands you need to rebuild the blog like mine are the following:

```bash
npm install -g hexo-cli
hexo init
npm install
npm install hexo-material
cp -r node_modules/hexo-material themes/material
npm install hexo-helper-qrcode --save
npm install hexo-prism-plugin --save
npm install hexo-generator-feed --save
npm install hexo-generator-search --save
npm install hexo-math@^2.0.1 --save
npm install hexo-math@^3.0.4 --save
```

Install hexo-math twice due to this [troubleshooting][hexo-math_troubleshooting]

[Hexodocs]: https://neko-dev.github.io/material-theme-docs/
[HTM]: https://github.com/viosey/hexo-theme-material
[hexo-math_troubleshooting]: https://godshen.github.io/2017/10/31/exploreMathjax/