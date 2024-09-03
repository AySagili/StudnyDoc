# 封装技巧

## 统一返回接口

### 2024/8/14

今天仿照这 SpringBoot 那边的一个封装技巧实现了 C++版类似的效果  
话不多说直接上代码

```C++
#ifndef __RESULTENUM_H__
#define __RESULTENUM_H__

#include <iostream>
#include <string>
#include <optional>

namespace ResultCode
{

    struct ResultEnum
    {
    private:
        int code = {};
        bool status = {};
        std::string message = {};
        ResultEnum() = default;
    public:
        ResultEnum(int code, bool status, const std::string &message)
            : code(code), status(status), message(message) {}
    private:
        template <typename T>
        friend class Result;
        friend std::ostream &operator<<(std::ostream &os, const ResultEnum &res)
        {
            os << "Code: " << res.code << ", Status: " << (res.status ? "true" : "false") << ", Message: " << res.message;
            return os;
        }
    };

    //
    const static ResultEnum SUCCESS(200, true, "Success");
    const static ResultEnum ERROR(500, false, "Error");
    const static ResultEnum NOT_FOUND(404, false, "Not Found");
    const static ResultEnum FORBIDDEN(403, false, "Forbidden");
    const static ResultEnum BAD_REQUEST(400, false, "Bad Request");
}
template <typename T>
class Result
{
private:
    /* data */
public:
private:
    int code = {};
    bool status = {};
    std::string message = {};
    std::optional<T> data = {};
    Result() = default;

public:
    // 使用 ResultEnum 的构造函数
    explicit Result(const ResultCode::ResultEnum &result)
        : code(result.Code()), status(result.Status()), message(result.Message()) {}

    explicit Result(const ResultCode::ResultEnum &result, const T &data) : Result(result)
    {
        this->data = data;
    }
    static Result<std::string> SUCCESS()
    {
        return Result(ResultCode::SUCCESS);
    }
    static Result<T> SUCCESS(const T &data)
    {
        return Result(ResultCode::SUCCESS, data);
    }
    static Result<std::string> ERROR()
    {
        return Result(ResultCode::ERROR);
    }
    static Result<T> ERROR(const T &data)
    {
        return Result(ResultCode::ERROR, data);
    }
    friend std::ostream &operator<<(std::ostream &os, const Result<T> &res)
    {
        os << "Code: " << res.code << ", Status: " << (res.status ? "true" : "false") << ", Message: " << res.message << ", Data: ";
        if (res.data)
            os << *res.data;
        else
            os << "null";
        return os;
    }
    ~Result() = default;
};

#endif // __RESULTENUM_H__
```

学了几个新的关键字

```C++
explicit
这个关键字貌似可以防止隐士构造函数的使用
防止有人不小心
```

```C++
std::optional
是用来解决某些情况的空值与非空值的问题
比如这里的 Data属性有几率可能是空 为了安全 使用这个关键字定义了一下
因为std::optional保存的好像是对象的引用 所以需要使用指针来获得真实值
```

## 封装统一单例父类

### 2024/8/25

做项目的时候会遇见很多地方需要用到单例模式，比如连接池以及其他各种池化技术，肯定是一个地方初始化，其他地方用就行的那种。

```C++
#ifndef __SINGLETON_H__
#define __SINGLETON_H__
#include <iostream>
#include <stdexcept>
#include <mutex>

template <typename T>
class Singleton
{
public:
    Singleton(const Singleton &) = delete;
    Singleton &operator=(const Singleton &) = delete;

public:
    static std::unique_ptr<T> instance;
    template <typename... Args>
    static T &Initalization(Args &&..._args)
    {
        static std::once_flag flag;
        std::call_once(flag, [&]()
                       { instance = std::make_unique<T>(std::forward<Args>(_args)...); });
        return *instance;
    }
    static T &GetInstance()
    {
        if (instance == nullptr)
        {
            throw std::runtime_error("Singleton instance has not been initialized");
        }
        else
        {
            return *instance;
        }
    }

    ~Singleton() {

    };

private:
protected:
    Singleton() {};
};

// 在源文件中定义静态成员变量
template <typename T>
std::unique_ptr<T> Singleton<T>::instance = nullptr; // 或者直接初始化为 nullptr

#endif // __SINGLETON_H__
```

学习的新关键字

```C++
std::call_once
```

这个官方给的是只有当第一次调用的时候才会进入，但是目前似乎好像并不是，等后续有空再研究研究，可能是我的一些变量没搞对，导致他里面的回调函数出现了问题。  
遇见的问题有以下  
当一个类内有静态成员变量时，如果不是一些字面关键字、例如 char int 这种那么就需要在类外初始化。
