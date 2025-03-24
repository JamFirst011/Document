# 单元测试

使用JUnit进行单元测试，每个文件对应一个测试文件，测试文件名以Test结尾

### 在vscode中使用JUnit

1. 在测试模块启用java测试
1. cmd+shift+p选择java:go to test
1. 此时可以选择特定的文件来生成他的测试文件
1. 编写测试文件，用@Test修饰的方法会被用来测试，可以使用assertEquals()方法
1. 右键测试方法或类左侧的按钮并选择Run in Coverage来运行测试，并可以在左侧看到每个文件的准确率和覆盖率

### 使用Fixture

在测试类中，需要初始化一些实例进行测试，所以可以用`@BeforeEach/@AfterEach`装饰方法，这些方法会在每个测试函数之前/之后运行，或者使用`@BeforeAll/@AfterAll` 装饰静态方法，这两个方法会分别在所以函数开始前/结束后运行

### 测试异常

在测试方法中，可以使用`assertThrows`测试异常，第一个参数为异常类型，第二个参数为一个函数，包含了会触发异常的代码

### 参数化测试

指在测试时，可以对测试函数传入参数，首先用`@ParameterizedTest`需要装饰参数化测试函数，有三种方法可以指定参数：
- 使用CsvSource装饰器
- 使用CsvFileSource
- 使用MethodSource以及静态函数
具体代码如下：
```java
@ParameterizedTest
@MethodSource
void testCapitalize(String input, String result) {
    assertEquals(result, StringUtils.capitalize(input));
}

static List<Arguments> testCapitalize() {
    return List.of( // arguments:
            Arguments.of("abc", "Abc"), //
            Arguments.of("APPLE", "Apple"), //
            Arguments.of("gooD", "Good"));
}

@ParameterizedTest
@CsvSource({ "abc, Abc", "APPLE, Apple", "gooD, Good" })
void testCapitalize(String input, String result) {
    assertEquals(result, StringUtils.capitalize(input));
}

@ParameterizedTest
@CsvFileSource(resources = { "/test-capitalize.csv" })
void testCapitalizeUsingCsvFile(String input, String result) {
    assertEquals(result, StringUtils.capitalize(input));
}
```