# 有时候因为需要调试Android应用中正在运行service中一些状态值是否正常

1. 先在应用代码里面重写service中的dump函数

~~~java
@Override
protected void dump(FileDescriptor fd, PrintWriter pw, String[] args) {
    super.dump(fd, pw, args);
    if (args != null) {
        for (String arg : args) {
            switch (arg) {
                case "help":
                    pw.println("help");
                    break;
            }
        }
    }
}
~~~

2. 然后通过adb命令进行调试，其中的serviceName为service的定义名称

> adb shell dumpsys activity service serviceName help
