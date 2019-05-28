应用构建完成后，您将在设备上看到启动应用.

{% include app-figure.md img-class="site-mobile-screenshot border"
    path-prefix="get-started" platform="iOS" image="starter-app.png"
    caption="Starter app" %}

## 体验热重载

Flutter 可以通过 _热重载（hot reload）_ 实现快速的开发周期, 热重载就是无需重启应用程序就能实时加载修改后的代码, 并且不会丢失状态(译者语:如果是一个web开发者, 那么可以认为这和webpack的热重载是一样的). 简单的对代码进行更改, 然后告诉IDE或命令行工具你需要重新加载(点击reload按钮), 你就会在你的设备或模拟器上看到更改.

 1. 打开文件`lib/main.dart`.
 1. 将字符串

    {% prettify dart %}
      'You have [[strike]]pushed[[/strike]] the button this many times'
    {% endprettify %}

    改为

    {% prettify dart %}
      'You have [!clicked!] the button this many times'
    {% endprettify %}

    {{site.alert.important}}
      不要停止您的应用程序. 让您的应用一直运行.
    {{site.alert.end}}

 1. 保存更改{{include.save_changes}}

你会立即在运行的应用程序中看到更新的字符串
