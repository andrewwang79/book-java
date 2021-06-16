# 工具链和使用
## 工具链
| 项 | 软件 | 说明 |
| :-: | - | - |
| JDK | [jdk8](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html) | 自带Maven |
| git客户端 | SoureTree |  |
| 开发工具 | IntelliJ |  |
| IntelliJ插件 | mybatisx |  |

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
* [格式化模板](./s/longquan.format.xml)。继承自[google](https://github.com/google/styleguide/blob/gh-pages/intellij-java-google-style.xml)
* [导入](https://blog.csdn.net/whgyxy/article/details/88747178)：Preferences > Editor > Code Style。
