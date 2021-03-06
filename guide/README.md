# 介绍

:::tip 提示
如果在阅读本文档时遇到难以理解的词汇，请随时查阅 [术语表](/glossary.md)、[酷Q文库](https://docs.cqp.im/) 或 [Google 搜索](https://www.google.com/ncr)。
:::

CoolQ C++ SDK（或称 cqcppsdk、CQCPPSDK）是为了方便使用 C++ 开发 酷Q 应用而生的一个开发框架，封装了 酷Q 提供的 DLL 接口，对外提供更现代的 C++ 接口，从而提高应用开发效率，与此同时保持 C++ native 的性能优势。

## 特点

- 使用 CMake 构建，可方便地集成各类包管理器（如 vcpkg、conan 等）
- 支持跨平台开发、测试和打包
- 全程使用 UTF-8，并自动在与 酷Q 交换数据时转码到 GB18030
- 无需安装任何第三方库，即开即用
- 将 酷Q 事件数据封装为对象，API 封装为 C++ 函数，减少出错的可能
- 使用 C++17 标准，可利用智能指针、lambda 表达式、auto 类型推断等新特性提高开发效率

## 一瞥

```cpp
#include <cqcppsdk/cqcppsdk.hpp>

using namespace cq;

CQ_INIT {
    on_private_message([](const auto &event) {
        try {
            send_message(event.target, event.message);
        } catch (ApiError &err) {
            logging::warning("私聊", "复读失败");
        }
    });
}
```
