## Profile 运行

{{site.alert.important}}
  不要在debug模式和启用热重载的情况下测试应用程序的性能.
{{site.alert.end}}

到目前为止, 您运行的应用程序都处于deubg模式, 在较大的性能开销下实现更快的开发(例如, 热重新加载). janky动画正是在此模式下运行. 使用以下终端命令查看应用程序在profile模式下运行的性能.

```terminal
$ flutter run --profile
```

与debug模式下的动画相比, 动画应该更加平滑.
