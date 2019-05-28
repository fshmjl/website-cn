<div class="tab-pane active" id="androidstudio" role="tabpanel" aria-labelledby="androidstudio-tab" markdown="1">

## 创建应用  {#create-app}

 1. 选择 **File>New Flutter Project**.
 1. 选择 **Flutter application** 作为 project 类型, 然后点击 **Next**.
 1. 确保 **Flutter SDK Path** 指向SDK的位置. 如果尚未安装SDK，请安装它.
 1. 输入项目名称 (如 `myapp`), 然后点击 **Next**.
 1. 点击 **Finish**.
 1. 等待Android Studio安装SDK并创建项目.

上述命令创建一个使用[Material 组件](https://material.io/design/),项目名为myapp的Flutter项目.

{% include_relative _main-code-note.md  %}

## 运行应用程序

 1. 定位到Android Studio 工具栏:<br>
    ![Main IntelliJ toolbar][]{:.mw-100}
 1. 在 **target selector** 中, 选择一个运行该应用的Android设备.
    如果没有列出可用，请选择 **Tools>Android>AVD Manager** 并在那里创建一个. 有关详情，请参阅 [Managing AVDs][].
 1. 在工具栏中点击 **Run图标**, 或者调用菜单项 **Run > Run**.

{% capture save_changes -%}
  : 调用 **Save All**, 或点击 **Hot Reload**
  <i class="material-icons align-bottom">offline_bolt</i>.
  {% comment %} Or, as an alternative:
    {% asset 'get-started/hot-reload-button.png' alt='looks like a lightning bolt' %}.
  {% endcomment -%}
{% endcapture %}

{% capture ide_profile -%}
  to invoke the menu item **Run > Profile** in the IDE, or
{% endcapture %}

{% include_relative _try-hot-reload.md save_changes=save_changes %}
{% include run-profile.md ide_profile=ide_profile %}

[Main IntelliJ toolbar]: {% asset tools/android-studio/main-toolbar.png @path %}
[Managing AVDs]: {{site.android-dev}}/studio/run/managing-avds
[Material Components]: {{site.material}}/guidelines
</div>
