Front-End JSON(P) API Specification
===================================

## HTTP 接口返回格式 (Scheme)

  接口状态码 (HTTP Code): => 200

  接口输出 (Response): JSON => {error, msg, data, ver}

  ```javascript
  {
    "error": ${error_code},        // {String} api status code, defaults to '0',
    "msg": ${api_status_message},  // {String} api status message
    "data": ${api_data},           // {Mixed} Generic type for api data response, can be null, empty "", 0, {}, [] etc,.
    "ver": ${api_version}          // {String} version identify, defaults to '1.0'
  }
  ```

  **`error` 字段状态码定义**

  * 状态码为字符串类型 (String). eg. "0" (注意有双引号)
  * 0 ~ 100 为系统保留状态
  * "-100" -  session timeout (登陆验证)
  * "0"    -  api success (default value)
  * "1"    -  internal error (后端接口未知错误)
  * "2"    -  redirect url (页面跳转响应)
  * **业务状态码建议使用 100以后的数值 (>100)**. eg: 0x101F, 0x1013

  示例:

  ```javascripton
  {"error": "2", "msg": "user session timeout", "data": "http://login.yunhou.com/login.php?t", "ver": "1.0"}
  ```

## 其他

  * 本规范适用所有前后端数据接口规范，json, jsonp
  * 接口输出**必须是规范的 JSON 字符串**, 拒绝手动拼接 json 字符串返回，请参考 <http://json.org/>
