# 工具使用
## eclipse
### 设置
1. 代码编辑器开启窗口Problems(问题)和Outline(类结构)
1. 可以暂时关闭build automatically，但要尽快开启。尽量少用Clean。
1. [Java项目导出可运行的jar文件](https://blog.csdn.net/mahoking/article/details/42871937)

### 使用
* 查找非注释中文文字的正则表达式："\w*[\u4e00-\u9fa5]+
* [eclipse无法连接到makertplace](https://blog.csdn.net/u010177899/article/details/68061624)
* [Remote System Explorer Operation卡死Eclipse解决方案 - 披萨大叔的博客 - CSDN博客](https://blog.csdn.net/qq_27258799/article/details/51682930)
* 克隆workspace：
  1. 删除目标workspace下的.metadata\.plugins目录
  1. 拷贝原始workspace下的.metadata\.plugins目录
  1. 删除目标workspace下的.metadata\.plugins\org.eclipse.core.resources目录

### 快捷键
* ctrl+shift+T //查找当前工程下的某个类
* ctrl+shift+R//查找当前工程下的某个文件

* 上下分屏 : Ctrl + Shift + -
* 左右分屏 : Ctrl + Shift + [

* ctrl+shift+x   转为大写
* ctrl+shift+y   转为小写

## IntelliJ IDEA
### 代码格式化
1. [导入格式化模板](http://blog.csdn.net/preterhuman_peak/article/details/45719985)

1. import设置
  1. 设置 -> Editor > Code Style > Java，标签Imports
  1. 选项“import with '*':”，都改成2
