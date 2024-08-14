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
