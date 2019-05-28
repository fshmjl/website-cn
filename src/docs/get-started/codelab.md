---
title: 编写您的第一个 Flutter App, 第1部分
short-title: Write your first app
prev:
  title: 体验
  path: /docs/get-started/test-drive
next:
  title: 了解更多
  path: /docs/get-started/learn-more
diff2html: true
---

{% assign code-url = 'https://raw.githubusercontent.com/flutter/codelabs/master' -%}

{% asset get-started/startup-namer-part-1 alt="The app that you'll be building" class='site-image-right' %}

{%- comment %}
  Code highlights in this page are green, to match diff additions.
{% endcomment -%}
<style>pre .highlight { background-color: #dfd; }</style>

这是创建您的第一个Flutter应用程序的指南. 如果您熟悉面向对象和基本编程概念(如变量、循环和条件控制), 则可以完成本教程, 您无需要了解Dart或拥有移动开发的经验.

本指南是codelab两部分中的第1部分. 您可以在[Google Developers]({{site.codelabs}})上找到
[第2部分]({{site.codelabs}}/codelabs/first-flutter-app-pt2).
[第1部分]({{site.codelabs}}/codelabs/first-flutter-app-pt1)
同样也可以在[Google Developers]({{site.codelabs}})上找到.

## 您将在第1部分中构建的内容
{:.no_toc}

您将完成一个简单的移动应用程序, 功能是:为一个创业公司生成建议的名称.用户可以选择和取消选择的名称、保存(收藏)喜欢的名称. 该代码一次生成十个名称, 当用户滚动时, 会生成一新批名称. 用户可以点击导航栏右边的列表图标, 以打开到仅列出收藏名称的新页面.

这个 GIF 图展示了第一部分最终实现的效果.

{{site.alert.secondary}}
  <h4 class="no_toc">您将在第1部分学到什么</h4>

  * 如何在iOS和Android上编写看起来像原生的Flutter应用程序.
  * Flutter应用程序的基本结构.
  * 查找和使用包来扩展功能.
  * 使用热重载加快开发周期.
  * 如何实现有状态widget.
  * 如何创建一个无限的，懒加载的list.

  在codelab的[第2部分中]({{site.codelabs}}/codelabs/first-flutter-app-pt2),
  您将添加交互, 修改应用程序的主题, 并添加导航到新屏幕的功能(在Flutter中称为route).
{{site.alert.end}}

{{site.alert.secondary}}
  <h4 class="no_toc">您将用到什么</h4>

  您将需要两个软件来完成本实验:
  [Flutter SDK](/docs/get-started/install) 和 [一个编辑器](/docs/get-started/editor).
  此codelab采用Android Studio，但您可以使用您喜欢的编辑器.

  您可以使用以下任何设备运行此codelab：

  * 一台连接到计算机并设置为开发人员模式的真机([Android](install/macos#set-up-your-android-device)
    或 [iOS](install/macos#deploy-to-ios-devices)).
  * [iOS 模拟器](install/macos#set-up-the-ios-simulator).
  * [Android 模拟器](install/macos#set-up-the-android-emulator).
{{site.alert.end}}

## 第1步: 创建 Flutter app

<?code-excerpt path-base="codelabs/startup_namer/step1_base"?>

创建一个简单的、基于模板的Flutter应用程序, 按照[创建您的第一个Flutter应用中.](/docs/get-started/test-drive#create-app)的指南的步骤,
后将项目命名为startup_namer（而不是myapp).

{{site.alert.tip}}
  如果您没有在IDE中看到“New Flutter Project”作为选项, 请确认您已 [安装 Flutter 和
  Dart 插件](/docs/get-started/editor).
{{site.alert.end}}

在codelab中, Dart代码主要存在于**lib/main.dart**文件中, 您将主要编辑它.

 1. 替换 lib/main.dart.<br>
    删除lib / main.dart中的所有代码，然后替换为下面的代码，它将在屏幕的中心显示“Hello World”.

    <?code-excerpt "lib/main.dart" title?>
    ```dart
    import 'package:flutter/material.dart';

    void main() => runApp(MyApp());

    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Welcome to Flutter',
          home: Scaffold(
            appBar: AppBar(
              title: Text('Welcome to Flutter'),
            ),
            body: Center(
              child: Text('Hello World'),
            ),
          ),
        );
      }
    }
    ```

    {{site.alert.tip}}

       将代码粘贴到应用程序中时, 缩进可能会出现偏差. 您可以使用Flutter工具自动修复此问题:

      * Android Studio / IntelliJ IDEA：右键单击代码,
        然后选择 **Reformat Code with dartfmt**.
      * VS Code: 右键然后选择 **Format Document**.
      * 终端: 运行 `flutter format <filename>`.
    {{site.alert.end}}

 2. [按照您IDE描述的方式](/docs/get-started/test-drive)运行程序.
    您应该看到Android或iOS输出, 具体取决于您的设备.

    {% indent %}
      {% include android-ios-figure-pair.md image="hello-world.png" alt="Hello world app" %}
    {% endindent %}

    {{site.alert.tip}}
    第一次在物理设备上运行时, 可能需要一段时间才能加载. 在此之后, 您可以使用热重新加载进行快速更新. 如果应用程序正在运行, Save也会执行热重新加载.
    {{site.alert.end}}

### 分析
{:.no_toc}

* 本示例创建一个Material APP.
  [Material]({{site.material}}/guidelines)是一种标准的移动端和web端的视觉设计语言. Flutter提供了一套丰富的Material widgets.
* main函数使用了(=>)符号, 这是Dart中单行函数或方法的简写.
* 该应用程序继承了 StatelessWidget, 这将会使应用本身也成为一个widget. 在Flutter中, 大多数东西都是widget, 包括对齐(alignment)、填充(padding)和布局(layout).
* Scaffold 是 Material library 中提供的一个widget, 它提供了默认的导航栏、标题和包含主屏幕widget树的body属性. widget树可以很复杂.
* widget的主要工作是提供一个build()方法来描述如何根据其他较低级别的widget来显示自己
* 本示例中的body的widget树中包含了一个Center widget, Center widget又包含一个 Text 子widget. Center widget可以将其子widget树对其到屏幕中心.

## 第2步: 使用外部包(package)

在这一步中，您将开始使用一个名为english_words的开源软件包 ，其中包含数千个最常用的英文单词以及一些实用功能.

您可以 在[pub.dartlang.org](https://pub.dartlang.org/flutter/)上找到[english_words](https://pub.dartlang.org/packages/english_words)软件包以及其他许多开源软件包

 1. pubspec文件管理Flutter应用程序的assets(资源，如图片、package等)。
    在pubspec.yaml中，将english_words（3.1.0或更高版本）添加到依赖项列表，如下面高亮显示的行：

    <?code-excerpt path-base="codelabs/startup_namer"?>
    <?code-excerpt "{step1_base,step2_use_package}/pubspec.yaml" diff-u="4" from="dependencies" to="english"?>
    ```diff
    --- step1_base/pubspec.yaml
    +++ step2_use_package/pubspec.yaml
    @@ -5,4 +5,5 @@
     dependencies:
       flutter:
         sdk: flutter
       cupertino_icons: ^0.1.2
    +  english_words: ^3.1.0
    ```

 2. 在Android Studio的编辑器视图中查看pubspec时，单击右上角的 **Packages get**，这会将依赖包安装到您的项目。您可以在控制台中看到以下内容：

    ```terminal
    $ flutter pub get
    Running "flutter pub get" in startup_namer...
    Process finished with exit code 0
    ```

    执行`Packages get`还可以自动生成pubspec.lock文件，其中包含项目中所有包的列表及其版本号。

 3. 在**lib/main.dart** 中, 引入 `english_words`, 如高亮显示的行所示:

    <?code-excerpt path-base="codelabs/startup_namer/step2_use_package"?>
    <?code-excerpt "lib/main.dart" title retain="/^import/" replace="/import.*?english.*/[!$&!]/g" indent-by="2"?>
    ```dart
      import 'package:flutter/material.dart';
      [!import 'package:english_words/english_words.dart';!]
    ```

    在您输入时，Android Studio会为您提供有关库导入的建议。然后它将呈现灰色的导入字符串，让您知道导入的库尚未使用（到目前为止）

 4. 使用 English words 包生成文本来替换字符串“Hello World”.

    <?code-excerpt path-base="codelabs/startup_namer"?>
    <?code-excerpt "{step1_base,step2_use_package}/lib/main.dart" from="class"?>
    ```diff
    --- step1_base/lib/main.dart
    +++ step2_use_package/lib/main.dart
    @@ -5,6 +6,7 @@
     class MyApp extends StatelessWidget {
       @override
       Widget build(BuildContext context) {
    +    final wordPair = WordPair.random();
         return MaterialApp(
           title: 'Welcome to Flutter',
           home: Scaffold(
    @@ -12,7 +14,7 @@
               title: Text('Welcome to Flutter'),
             ),
             body: Center(
    -          child: Text('Hello World'),
    +          child: Text(wordPair.asPascalCase),
             ),
           ),
         );
    ```

    {{site.alert.note}}
      “驼峰命名法” (称为 “upper camel case” 或 “Pascal case” ), 表示字符串中的每个单词（包括第一个单词）都以大写字母开头。所以，“uppercamelcase” 变成 “UpperCamelCase”
    {{site.alert.end}}

 5. 如果应用程序正在运行，请重新加载以更新正在运行的应用程序。每次单击热重新加载或保存项目时，您应该在正在运行的应用程序中看到随机选择的不同单词对。这是因为单词配对是在构建方法中生成的，构建方法在每次MaterialApp需要渲染时运行，或者在Flutter Inspector中切换平台时运行。

    {% indent %}
      {% include android-ios-figure-pair.md image="step2.png" alt="App at completion of second step" %}
    {% endindent %}

### 遇到问题?

{:.no_toc}

  如果您的应用程序运行不正常，请查找是否有拼写错误。如果需要，使用下面链接中的代码来对比更正。

* [pubspec.yaml]({{code-url}}/startup_namer/step2_use_package/pubspec.yaml)
* [lib/main.dart]({{code-url}}/startup_namer/step2_use_package/lib/main.dart)

## 第3步: 添加一个 有状态的部件（Stateful widget）

<?code-excerpt path-base="codelabs/startup_namer/step3_stateful_widget"?>

Stateless widgets 是不可变的, 这意味着它们的属性不能改变 - 所有的值都是不变的.

State<em>ful</em> widgets 持有的状态可能在widget生命周期中发生变化. 实现一个 stateful
widget 至少需要两个类:

 1. 一个 StatefulWidget类。
 2. 一个 State类。 StatefulWidget类本身是不变的，但是 State类在widget生命周期中始终存在.

在这一步中，您将添加一个有状态的widget-RandomWords，它创建其State类RandomWordsState。State类将最终为widget维护建议的和喜欢的单词对。

 1. 创建一个最小的状态类。将以下内容添加到`main.dart`底部：

    <?code-excerpt "lib/main.dart (RandomWordsState)" title region="RWS-class-only" plaster="// TODO Add build() method" indent-by="2"?>
    ```dart
      class RandomWordsState extends State<RandomWords> {
        // TODO Add build() method
      }
    ```

    注意 `State<RandomWords>`的声明. 该应用程序的大部分代码都在该类中，
    该类持有RandomWords widget的状态。这个类将保存随着用户滚动而无限增长的生成的单词对，
    以及喜欢的单词对，用户通过重复点击心形 ❤️ 图标来将它们从列表中添加或删除。

    `RandomWordsState` 依赖于 `RandomWords` 类. 你接下来会添加它.

 2. 将有状态的`RandomWords` widget添加到`main.dart`.
    `RandomWords` widget 除了创建State 类之外， 几乎没有其他功能:

    <?code-excerpt "lib/main.dart (RandomWords)" title indent-by="2"?>
    ```dart
      class RandomWords extends StatefulWidget {
        @override
        RandomWordsState createState() => RandomWordsState();
      }
    ```

    在添加状态类后，IDE会提示该类缺少build方法。 接下来，您将添加一个基本的build方法，该方法通过将生成单词对的代码从MyApp移动到RandomWordsState来生成单词对。

 3. 将`build()` 方法 添加到 `RandomWordsState`中:

    <?code-excerpt "lib/main.dart (RandomWordsState)" title indent-by="2" replace="/(\n  )(.*)/$1[!$2!]/g"?>
    ```dart
      class RandomWordsState extends State<RandomWords> {
        [!@override!]
        [!Widget build(BuildContext context) {!]
        [!  final wordPair = WordPair.random();!]
        [!  return Text(wordPair.asPascalCase);!]
        [!}!]
      }
    ```

 4. 从 `MyApp` 中删除以下单词生成代码:

    <?code-excerpt path-base="codelabs/startup_namer"?>
    <?code-excerpt "{step2_use_package,step3_stateful_widget}/lib/main.dart" to="}"?>
    ```diff
    --- step2_use_package/lib/main.dart
    +++ step3_stateful_widget/lib/main.dart
    @@ -6,7 +6,6 @@
     class MyApp extends StatelessWidget {
       @override
       Widget build(BuildContext context) {
    -    final wordPair = WordPair.random();
         return MaterialApp(
           title: 'Welcome to Flutter',
           home: Scaffold(
    @@ -14,8 +13,8 @@
               title: Text('Welcome to Flutter'),
             ),
             body: Center(
    -          child: Text(wordPair.asPascalCase),
    +          child: RandomWords(),
             ),
           ),
         );
       }
    ```

 5. Restart the app.
    The app should behave as before, displaying a word
    pairing each time you hot reload or save the app.

{{site.alert.tip}}
  如果您在热重载时看到以下警告，请考虑重新启动应用程序：

  **Reloading...<br>
  Some program elements were changed during reload but did not run when
  the view was reassembled; you may need to restart the app (by pressing "R")
  for the changes to have an effect.**

  这可能是误报，但重新启动可确保您的更改反映在应用程序的UI中。
{{site.alert.end}}


### 遇到问题?
{:.no_toc}

如果您的应用程序运行不正常，可以使用下面链接中的代码来对比更正。

* [lib/main.dart]({{code-url}}/startup_namer/step3_stateful_widget/lib/main.dart)

## 第4步: 创建一个无限滚动ListView

<?code-excerpt path-base="codelabs/startup_namer/step4_infinite_list"?>

在这一步中，您将扩展（继承）RandomWordsState类，以生成并显示单词对列表。
当用户滚动时，ListView中显示的列表将无限增长。
ListView的`builder`工厂构造函数允许您按需建立一个懒加载的列表视图。

 1. 向RandomWordsState类中添加一个`_suggestions`列表以保存建议的单词对。
    该变量以下划线（_）开头，在Dart语言中使用下划线前缀标识符，会强制其变成私有的。
    另外，添加一个`biggerFont`变量来增大字体大小

    <?code-excerpt "lib/main.dart" title region="RWS-var" indent-by="2" replace="/final .*/[!$&!]/g"?>
    ```dart
      class RandomWordsState extends State<RandomWords> {
        [!final _suggestions = <WordPair>[];!]
        [!final _biggerFont = const TextStyle(fontSize: 18.0);!]
        // ···
      }
    ```

    {{site.alert.note}}
      在Dart语言中使用下划线标识符前缀会[强制私有]({{site.dart-site}}/guides/language/language-tour).
    {{site.alert.end}}

    接下来， 您将向RandomWordsState类添加一个 `_buildSuggestions()` 函数.
    此方法构建显示建议单词对的ListView。

    ListView类提供了一个builder属性，`itemBuilder` 值是一个匿名回调函数，
    接受两个参数- BuildContext和行迭代器`i`。迭代器从0开始，
    每调用一次该函数，`i`就会自增1，对于每个建议的单词对都会执行一次。该模型允许建议的单词对列表在用户滚动时无限增长。

 2. 将_buildSuggestions（）函数添加到RandomWordsState类：

    <?code-excerpt "lib/main.dart (_buildSuggestions)" title indent-by="2"?>
    ```dart
      Widget _buildSuggestions() {
        return ListView.builder(
            padding: const EdgeInsets.all(16.0),
            itemBuilder: /*1*/ (context, i) {
              if (i.isOdd) return Divider(); /*2*/

              final index = i ~/ 2; /*3*/
              if (index >= _suggestions.length) {
                _suggestions.addAll(generateWordPairs().take(10)); /*4*/
              }
              return _buildRow(_suggestions[index]);
            });
      }
    ```

    {:.numbered-code-notes}
     1. 对于每个建议的单词对都会调用一次itemBuilder，然后将单词对添加到ListTile行中在偶数行，该函数会为单词对添加一个ListTile row.在奇数行，该函数会添加一个分割线widget，来分隔相邻的词对。注意，在小屏幕上，分割线看起来可能比较吃力。
     2. 在每一列之前，添加一个1像素高的分隔线widget
     3. 语法 "i ~/ 2" 表示i除以2，但返回值是整形（向下取整），比如i为：1, 2, 3, 4, 5 时，结果为0, 1, 1, 2, 2， 这可以计算出ListView中减去分隔线后的实际单词对数量
     4. 如果是建议列表中最后一个单词对， 接着再生成10个单词对，然后添加到建议列表

    对于每一个单词对，`_buildSuggestions`函数都会调用一次`_buildRow`。
    这个函数在ListTile中显示每个新词对，这使您在下一步中可以生成更漂亮的显示行。

 3. 向`RandomWordsState`类中添加一个`_buildRow()` 函数:

    <?code-excerpt "lib/main.dart (_buildRow)" title indent-by="2"?>
    ```dart
      Widget _buildRow(WordPair pair) {
        return ListTile(
          title: Text(
            pair.asPascalCase,
            style: _biggerFont,
          ),
        );
      }
    ```

 4. 更新RandomWordsState的build方法以使用`_buildSuggestions()`，而不是直接调用单词生成库。
    更改后如下面高亮部分：
    ([Scaffold]({{site.api}}/flutter/material/Scaffold-class.html)
    implements the basic Material Design visual layout.)
    更改后如下面高亮部分：

    <?code-excerpt "lib/main.dart (build)" title region="RWS-build" replace="/(\n  )(return.*|  .*|\);)/$1[!$2!]/g" indent-by="2"?>
    ```dart
      @override
      Widget build(BuildContext context) {
        [!return Scaffold(!]
        [!  appBar: AppBar(!]
        [!    title: Text('Startup Name Generator'),!]
        [!  ),!]
        [!  body: _buildSuggestions(),!]
        [!);!]
      }
    ```

 5. 在MyApp类中，通过更改标题并将home更改为`RandomWords` widget来更新build（）方法：

    <?code-excerpt path-base="codelabs/startup_namer"?>
    <?code-excerpt "{step3_stateful_widget,step4_infinite_list}/lib/main.dart" diff-u="4" from="class MyApp" to="}"?>
    ```diff
    --- step3_stateful_widget/lib/main.dart
    +++ step4_infinite_list/lib/main.dart
    @@ -6,15 +6,8 @@
     class MyApp extends StatelessWidget {
       @override
       Widget build(BuildContext context) {
         return MaterialApp(
    -      title: 'Welcome to Flutter',
    -      home: Scaffold(
    -        appBar: AppBar(
    -          title: Text('Welcome to Flutter'),
    -        ),
    -        body: Center(
    -          child: RandomWords(),
    -        ),
    -      ),
    +      title: 'Startup Name Generator',
    +      home: RandomWords(),
         );
       }
    ```

 6. 重新启动应用程序。你应该看到一个单词对列表。尽可能地向下滚动，您将继续看到新的单词对。

    {% indent %}
      {% include android-ios-figure-pair.md image="step4-infinite-list.png" alt="App at completion of fourth step" %}
    {% endindent %}

### 遇到问题?
{:.no_toc}

如果你的应用没有正常运行，你可以使用一下链接中的代码对比更正。


* [lib/main.dart]({{code-url}}/startup_namer/step4_infinite_list/lib/main.dart)

{% include run-profile.md %}

## 下一步
{:.no_toc}

{% include app-figure.md class="site-image-right" img-class="border"
    image="get-started/startup-namer.gif" caption="The app from part 2" %}

恭喜!

你已经编写了一个可以在iOS和Android上运行的交互式Flutter应用程序。在这个codelab例子中，你已经做了下面这些事

* 从头开始创建一个Flutter应用程序.
* 编写 Dart 代码.
* 利用外部的第三方库.
* 使用热重载加快开发周期.
* 实现一个有状态的widget，为你的应用增加交互.
* 用ListView和ListTiles创建一个延迟加载的无限滚动列表.

如果您想继续扩展此应用程序, 请转到[Google Developers Codelabs]({{site.codelabs}})网站的
[第2部分]({{site.codelabs}}/codelabs/first-flutter-app-pt2)， 继续添加以下功能

* 通过添加可点击的爱心图标来保存最喜欢的配对。
* 通过添加包含已保存收藏的新页面，实现导航到新页面的路由。
* 修改主题颜色，制作全白应用程序。
.
