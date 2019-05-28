<div class="tab-pane" id="vscode" role="tabpanel" aria-labelledby="vscode-tab" markdown="1">

## 创建应用

  1. 调用 **View>Command Palette...**.
  1. 输入 'flutter', 然后选择 **'Flutter: New Project'**.
  1. 输入 Project 名称 (如`myapp`), 然后按回车键.
  1. 创建或选择新项目的文件夹.
  1. 等待项目创建继续，并显示main.dart文件.

上述命令创建一个使用[Material 组件](https://material.io/design/)，项目名为myapp的Flutter项目.

{% include_relative _main-code-note.md  %}

## 运行应用程序

 1. 找到VS Code状态栏（窗口底部的蓝色栏）:<br> ![status bar][]{:.mw-100}
 1. 从**Device Selector**区域中选择一个设备.
    有关详细信息,请参阅 [在Flutter设备之间快速切换](https://dartcode.org/docs/quickly-switching-between-flutter-devices/).
    - 如果没有可用的设备单击**No Devices**并启动模拟器
    - 如要设置真机, 参照您对应操作系统的[安装](/docs/get-started/install)页面特定说明进行操作.
 1. 按 <kbd>F5</kbd>键或调用**Debug>Start Debugging**.
 1. 等待应用程序启动 &mdash; **Debug Console**中会打印启动进度.

{% capture save_changes -%}
  : 调用 **Save All**, 或点击 **Hot Reload**
  <i class="material-icons align-bottom">offline_bolt</i>.
  {% comment %} Or, as an alternative:
    {% asset 'get-started/hot-reload-button.png' alt='looks like a lightning bolt' %}.
  {% endcomment -%}
{% endcapture %}

{% include_relative _try-hot-reload.md save_changes=save_changes %}
{% include run-profile.md %}

[Install]: /docs/get-started/install
[Material Components]: {{site.material}}/guidelines
[Quickly switching between Flutter devices]: https://dartcode.org/docs/quickly-switching-between-flutter-devices
[status bar]: {% asset tools/vs-code/device_status_bar.png @path %}

</div>
