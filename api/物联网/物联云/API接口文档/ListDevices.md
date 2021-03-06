### 1. 接口描述
本接口 (ListDevices) 用于查询物联云设备的设备列表。

接口请求域名：`iotcloud.api.qcloud.com`

### 2. 输入参数

以下请求参数列表仅列出了接口请求参数，其它参数见 [公共请求参数](https://cloud.tencent.com/document/api/213/6976) 页面。

| 参数名称      | 必选   | 类型     | 描述                |
| --------- | ---- | ------ | ----------------- |
| pageSize  | 是    | Int    | 分页的大小，数值范围 10-250 |
| pageNum   | 是    | Int    | 请求的页数             |
| productID | 是    | String | 需要查看设备列表的产品ID     |

### 3. 输出参数

| 参数名称     | 类型              | 描述                                       |
| -------- | --------------- | ---------------------------------------- |
| code     | Int             | 公共错误码。0 表示成功，其他值表示失败，详见[公共错误码](https://cloud.tencent.com/document/product/634/12279)页面。 |
| message  | String          | 模块错误信息描述，格式为 "(模块错误码)模块错误信息" 详见本页面的[模块错误码](#module_error_info) |
| codeDesc | String          | 模块错误码的英文描述                               |
| totalCnt | Int             | 设备总数                                     |
| devices  | Array of Device | 设备对象的数组                                  |

Device 的结构如下

| 参数名称       | 类型     | 描述   |
| ---------- | ------ | ---- |
| deviceName | String | 设备名称 |
| productID  | String | 产品ID |

### 4. 示例

输入
<pre>
  https://iotcloud.api.qcloud.com/index.php?Action=ListDevices
  &productID=ABCDE12345&pageSize=10&pageNum=1
  &<<a href="https://cloud.tencent.com/document/api/213/6976">公共请求参数</a>>
</pre>

输出
```
{
    "totalCnt": 2, 
    "devices": [
        {
            "deviceName": "device22", 
            "productID": "ABCDE12345"
        }, 
        {
            "deviceName": "device21", 
            "productID": "ABCDE12345"
        }
    ],
    "message": "",
    "codeDesc": "Success",
    "code": 0
}
```

<span id = "module_error_info"></span>
### 5. 模块错误码

| 模块错误码 | 描述              |
| ----- | --------------- |
| 2004  | 分页参数非法          |
| 2100  | 内部服务器错误，请联系技术人员 |
| 2101  | 请求参数非法          |



