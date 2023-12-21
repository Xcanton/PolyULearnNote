# SQL



```
// SQL
SELECT 
    *
FROM TABLE
WHERE
    condition A
    AND condition B
GROUP BY
    column1, column2
HAVING
    (
    Condition C
    AND Condition D
    )
ORDER BY
    column3 asc,
    column4 desc
```

## 小测-分析当前表结构有什么不足

<figure><img src="../../.gitbook/assets/image (207).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (208).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (209).png" alt=""><figcaption></figcaption></figure>

* 不能表示一个订单中有多个商品的结构，需要多次创建
* 可以额外增加订单ID，和订单与商品对应表。

## 例题-用SQL表达Query

{% hint style="info" %}
没学三元表达式，需要join多个子查询表

SQL会被实际运行，如果语法错误一点分都不给
{% endhint %}

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

```
// i
SELECT C.StationID as StationID
FROM 
    ( SELECT StationID, COUNT(*) as total
      FROM Temperature
      WHERE Date(DateTime) = '2023-11-07'
      GROUP BY StationID
    ) AS C
    JOIN
    ( SELECT StationID, COUNT(*) as valid
      FROM Temperature
      WHERE Date(DateTime) = '2023-11-07'
        AND Tvalue > 30
      GROUP BY StationID
    ) AS A on C.StationID = A.StationID
WHERE
  A.valid / C.total >= 0.7;
```

```
// ii
SELECT
    DATE(DateTime) as date,
    HOUR(DateTime) as hour,
    AVG(Tvalue) as hourlyAvgTemp
FROM Temperature
Where
    StationID = 123
    AND YEAR(DateTime) = 2023
    AND MONTH(DateTime) = 11
GROUP BY DATE(DateTime), HOUR(DateTime);
```

