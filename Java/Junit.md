# 单元测试

使用JUnit进行单元测试，每个文件对应一个测试文件，测试文件名以Test结尾

### 在vscode中使用JUnit

1. 在测试模块启用java测试
1. cmd+shift+p选择java:go to test
1. 此时可以选择特定的文件来生成他的测试文件
1. 编写测试文件，用@Test修饰的方法会被用来测试，可以使用assertEquals()方法
1. 右键测试方法或类左侧的按钮并选择Run in Coverage来运行测试，并可以在左侧看到每个文件的准确率和覆盖率