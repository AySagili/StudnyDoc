# 实用的封装技巧

## 统一返回接口

### 2024/8/14

今天看到了一个有趣的统一返回结果的封装，很轻巧的感觉

```java
public enum ResultEnum {
    SUCCESS(200, true, "Success"),
    ERROR(500, false, "Error"),
    NOT_FOUND(404, false, "Not Found"),
    FORBIDDEN(403, false, "Forbidden"),
    BAD_REQUEST(400, false, "Bad Request");

    int code;
    boolean status;
    String message;

    ResultEnum(int code, boolean status, String message) {
        this.code = code;
        this.status = status;
        this.message = message;
    }

    public int Code() {
        return code;
    }

    public String Message() {
        return message;
    }

    public boolean Status() {
        return status;
    }

    public void SetCode(int code) {
        this.code = code;
    }

    public void SetMessage(String message) {
        this.message = message;
    }

    public void SetStatus(boolean status) {
        this.status = status;
    }
}
```

```java
public class Result<T> {
    int code;
    boolean status;
    String message;
    T data;

    public Result(ResultEnum resultEnum) {
        this.code = resultEnum.code;
        this.message = resultEnum.message;
        this.status = resultEnum.status;
    }

    public Result(ResultEnum resultEnum, T data) {
        this.code = resultEnum.code;
        this.message = resultEnum.message;
        this.status = resultEnum.status;
        this.data = data;
    }

    public static Result<String> SUCCESS() {
        return new Result<String>(ResultEnum.SUCCESS);
    }

    public static <T> Result<T> SUCCESS(T data) {
        return new Result<T>(ResultEnum.SUCCESS, data);
    }

    public static Result<String> ERROR() {
        return new Result<String>(ResultEnum.ERROR);
    }

    public static <T> Result<T> ERROR(T data) {
        return new Result<T>(ResultEnum.ERROR, data);
    }

    private Result() {

    }
}

```
