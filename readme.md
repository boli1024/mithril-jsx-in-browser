### 在浏览器环境中使用 Mithril 与 `JSX` 语法

```html
<!DOCTYPE html>
<html>

<head>
    <title>测试</title>
    <meta charset="utf-8" />
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
</head>

<body style="width: 400px">
    <div id="output"></div>
</body>

<script src="./js/babel_standalone@7.16.8.min.js"></script>
<script src="./js/mithril@2.0.4.min.js"></script>
<script type="text/babel">
    // Define a preset
    // 声明一个预设，修改 JSX 转换插件配置
    Babel.registerPreset("mithril-jsx", {
        plugins:[
            [
                Babel.availablePlugins["transform-react-jsx"],
                { decoratorsBeforeExport: true, pragma: "m" },
            ],
        ],
    });
</script>
<script type="text/babel" data-presets="mithril-jsx">
    const getMessage = () => "Hello World";
    document.getElementById('output').innerHTML = getMessage();

    var greeting = "Hello"
    var url = "http://google.com"
    var link = <a href={url}>{greeting + "!"}</a>

    m.render(document.body, link)
</script>

</html>
```

