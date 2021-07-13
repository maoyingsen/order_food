[toc]

## 查询餐谱



<img src="住院订餐.PNG" alt="image" style="zoom:30%;" />

**接口说明**：APP查看当前的餐别信息

**接口地址**：/checkFoodType

**请求参数**：（无）

**响应参数**：

| 参数名称  | 类型           | 参数说明     |
| --------- | -------------- | ------------ |
| code      | integer(int32) | 状态码       |
| date      | array          | 返回的实体类 |
| message   | string         | 返回信息     |
| timestamp | integer(int64) | 时间戳       |

**响应参数实例**

```json
{
    "code": 0,
    "message": "成功获取餐别分类",
    "data": [
        {
            "foodType": "早餐"
        },
        {
            "foodType": "上午加餐"
        },
        {
            "foodType": "中餐"
        },
        {
            "foodType": "下午加餐"
        },
        {
            "foodType": "晚餐"
        },
        {
            "foodType": "晚加餐"
        }
    ],
    "timestamp": 1626157035
}
```



**接口说明**：查看菜单信息

**接口地址**：/checkMenuInfo

**请求参数**：

| 参数名称 | 类型   | 参数说明                                                     |
| -------- | ------ | ------------------------------------------------------------ |
| foodType | string | 订餐类型, 1早餐、2午餐、3晚餐，4上午餐、5下午餐、6夜餐(晚加餐),可用值:早餐，中餐，晚餐，上午加餐，下午加餐，晚加餐 |

**请求参数实例**

```JSON
{
	"foodType": "早餐"
}
```

**响应参数**：

| 参数名称  | 参数说明                   | 类型           | schema          |
| :-------- | :------------------------- | :------------- | :-------------- |
| code      | 状态码                     | integer(int32) | integer(int32)  |
| data      | 返回的实体类               | array          | CheckMenuInfoVO |
| foodItem  | 订餐详细信息               | array          | object          |
| foodTitle | 餐别，表示是否为主食，流食 | string         |                 |
| message   | 返回信息                   | string         |                 |
| timestamp | 时间戳                     | integer(int64) | integer(int64)  |

**响应参数实例**

```json
{
    "code": 0,
    "message": "成功",
    "data": [
        {
            "foodTitle": "主食",
            "foodItem": [
                {
                    "foodPrice": 1.0,
                    "foodName": "米饭",
                    "foodType": 1,
                    "isVegetarian": 0,
                    "foodClass": "普通",
                    "imgSrc": "https://file-stage.aksofy.com/order-food/gongbaojiding.jpeg",
                    "foodCode": "1000",
                    "zaoBie": "普通"
                },
                {
                    "foodPrice": 1.0,
                    "foodName": "馒头",
                    "foodType": 1,
                    "isVegetarian": 0,
                    "foodClass": "普通",
                    "imgSrc": "https://file-stage.aksofy.com/order-food/gongbaojiding.jpeg",
                    "foodCode": "1001",
                    "zaoBie": "普通"
                },
                {
                    "foodPrice": 1.0,
                    "foodName": "花卷",
                    "foodType": 1,
                    "isVegetarian": 1,
                    "foodClass": "普通",
                    "imgSrc": "https://file-stage.aksofy.com/order-food/gongbaojiding.jpeg",
                    "foodCode": "1002",
                    "zaoBie": "普通"
                }
            ]
        }
    ],
    "timestamp": 1626161665
}
```



**接口说明**：查询第三方系统某天食谱信息

**接口地址**：dcst_cookbook（存储过程）

**请求参数**：日期（“YYYY-MM-DD”）

**响应参数**：

| 中文字段名   | 英文字段名 | 字段类型 | 字段长度 |
| ------------ | ---------- | -------- | -------- |
| 餐别代码     | Cbbh       | varchar  | 10       |
| 食谱类别     | Sort       | varchar  | 10       |
| 食谱代码     | code       | varchar  | 4        |
| 食谱名称     | name       | varchar  | 20       |
| 单价         | price      | numeric  | 6        |
| 菜品功效     | Gx         | varchar  | 200      |
| 热量         | rl         | Numeric  | 10       |
| 蛋白质       | dbz        | Numeric  | 10       |
| 脂肪         | zf         | Numeric  | 10       |
| 碳水化合物   | ts         | numeric  | 10       |
| 图片         | tp         | varchar  | 200      |
| 最大订餐数量 | dcsl       | numeric  | 10       |
| 灶别代码     | Zh         | varchar  | 2        |

**响应参数实例**

```json
[
	{
        'cbbh': '1 ', 'sort': '主食', 'code': '1000', 'name': '米饭', 'price':
	 	Decimal('1.00'), 'gx': '普通', 'rl': Decimal('0.00'), 'dbz': Decimal('0.00'), 
        'ts': Decimal('0.00'), 'dcsl': Decimal('999.00'), 'zh': '01'
    }, 
	{
        'cbbh': '1 ', 'sort': '主食', 'code': '1001', 'name': '馒头', 'price': 			
	 	Decimal('1.00'), 'gx': '普通', 'rl': Decimal('0.00'), 'dbz': Decimal('0.00'), 
        'ts': Decimal('0.00'), 'dcsl': Decimal('999.00'), 'zh':'01'
    },
    {
        'cbbh': '2 ', 'sort': '副食', 'code': '2004', 'name': '黄豆芽粉丝', 'price': 				Decimal('1.00'), 'gx': '普通', 'rl': Decimal('0.00'), 'dbz': Decimal('0.00'), 	
        'ts':Decimal('0.00'), 'dcsl': Decimal('999.00'), 'zh': '03'
    },
    {
        'cbbh': '4 ', 'sort': '汤粥', 'code': '3006', 'name': '苹果汁',
		'price': Decimal('1.00'), 'gx': '清流', 'rl': Decimal('0.00'), 'dbz': 	
        Decimal('0.00'), 'ts': Decimal('0.00'), 'dcsl': Decimal('999.00'), 'zh': '01'
    }
]
```

