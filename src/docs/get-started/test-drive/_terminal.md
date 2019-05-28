<div class="tab-pane" id="terminal" role="tabpanel" aria-labelledby="terminal-tab" markdown="1">

## 创建应用

使用 `flutter create` 命令创建一个新project.

```terminal
$ flutter create myapp
$ cd myapp
```

上述命令创建一个使用[Material 组件](https://material.io/design/),项目名为myapp的Flutter项目.

{% include_relative _main-code-note.md  %}

## Run the app

 1. 检查Android设备是否正在运行。如果没有显示, 参照您对应操作系统的[安装](/docs/get-started/install)页面特定说明进行操作.

    ```terminal
    $ flutter devices
    ```

 2. 运行 `flutter run` 命令来运行应用程序:

    ```terminal
    $ flutter run
    ```

{% capture save_changes -%}
.
1. 在终端窗口中输入<kbd>r</kbd>.
{% endcapture %}

{% include_relative _try-hot-reload.md save_changes=save_changes %}
{% include run-profile.md %}

[Install]: /docs/get-started/install
</div>
