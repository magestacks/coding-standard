[👉 《小马哥的代码实战课》官方知识星球来啦！！！](https://xiaomage.info/knowledge-planet/)

每一位程序都应该有自己的代码开发规范。

此仓库记录我在代码开发中，对自己的代码约束，仅供参考。这个仓库会一直维护，不断补充自己正在遵守以及好的代码约束。

## 文档排版

1）[中文文案排版指北](https://github.com/sparanoid/chinese-copywriting-guidelines)

## 注释规范

1）【强制】Class、Interface、Enum、@interface 等文件类型，类上注释仅需说明类的意图即可。

```java
/**
 * 适配第三方框架的线程池
 */
public interface ThreadPoolAdapter {

}
```

2）【强制】方法上需添加注释，并说明清楚方法的意图（接口实现类无需注释）；必要时描述 `@param` `@return`。

```java
/**
 * 适配第三方框架的线程池
 */
public interface ThreadPoolAdapter {

    /**
     * 修改框架线程池的核心参数
     *
     * @param threadPoolBaseInfo  修改线程池的基础参数
     * @return  线程池核心参数修改结果
     */
    boolean updateThreadPool(ThreadPoolBaseInfo threadPoolBaseInfo);
}
```

3）【强制】方法内部的注释，应该新起一行，而不是跟在代码后面。

```java
正例：
// 刷新动态线程池参数
refreshDynamicPool(parameter, executor);

反例：
refreshDynamicPool(parameter, executor); // 刷新动态线程池参数
```

4）【建议】私有方法尽量通过方法命名说明方法语义。

## 代码开发规约

1）【强制】类、方法和变量的命名要做到顾名思义，避免使用缩写。

2）【强制】静态变量使用大写，多个单词使用下划线连接。示例：MESSAGE_CENTER_SEND_TYPR。

3）【强制】捕获的异常名称命名为 ex ；捕获异常且不做任何事情，异常名称命名为 ignored。

4）【强制】返回值变量使用 result 命名；循环中使用 each 命名循环变量；map 中使用 entry 代替 each。

```java
result 命名示范：
private void parseDate(String data) {
    Result result = JSONUtil.parseObject(data, Result.class);
    return result;
}
或采用 result 为前缀：
private void parseDate(String data) {
    Result resultDate = JSONUtil.parseObject(data, Result.class);
    return resultDate;
}

each 命名示范：
appNameLeaseMap.values().forEach(each -> appNameLeaseList.add(each));
或是 for 循环：
for (Lease<InstanceInfo> each : appNameLeaseMap.values()) {
    appNameLeaseList.add(each);
}
```

5）【强制】业务系统中优先使用 Guava、HuTool、Common3 等工具类中的方法，不存在指定方法时再创建自定义工具类，禁止创建相同语义方法的工具类。

备注：定义组件项目时，尽量使用自定义工具类，避免因版本问题导致不确定的异常。

6）【建议】优先使用卫语句替换嵌套判断，提高代码简洁度。

## 代码格式规约

TODO

## 日志打印规约

TODO

## 参考资料

[ShardingSphere 开发规范](https://shardingsphere.apache.org/community/cn/contribute/code-conduct/)
