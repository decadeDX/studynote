---
tags:
  - mysql
  - 数据库
  - mybatis-plus
  - 笔记
aliases:
  - MySQL
  - 数据库学习
updated: 2026-06-17
---

# 📑 目录

- [[Mysql#Part 1：MySQL 基础|Part 1：MySQL 基础]]
  - [[Mysql#1. 数据类型|1. 数据类型]]
  - [[Mysql#2. DDL 数据定义语言|2. DDL]]
  - [[Mysql#3. DML 数据操作语言|3. DML]]
  - [[Mysql#4. DQL 数据查询语言（重点）|4. DQL（重点）]]
  - [[Mysql#5. 表设计原则（三范式）|5. 表设计原则]]
- [[Mysql#Part 2：MySQL 进阶（开发必备）|Part 2：MySQL 进阶（开发必备）]]
  - [[Mysql#6. 索引（Index）|6. 索引]]
  - [[Mysql#7. 事务（Transaction）|7. 事务]]
  - [[Mysql#8. 锁机制|8. 锁机制]]
  - [[Mysql#9. SQL 性能优化|9. SQL 性能优化]]
  - [[Mysql#10. 常用函数与语法|10. 常用函数]]
- [[Mysql#Part 3：MyBatis-Plus（开发实战）|Part 3：MyBatis-Plus]]
  - [[Mysql#11. 快速开始|11. 快速开始]]
  - [[Mysql#12. CRUD 接口|12. CRUD 接口]]
  - [[Mysql#13. 条件构造器 Wrapper（重点）|13. 条件构造器（重点）]]
  - [[Mysql#14. 分页插件|14. 分页插件]]
  - [[Mysql#15. 自动填充|15. 自动填充]]
  - [[Mysql#16. 逻辑删除|16. 逻辑删除]]
  - [[Mysql#17. 乐观锁|17. 乐观锁]]
  - [[Mysql#18. 代码生成器|18. 代码生成器]]
  - [[Mysql#19. 多数据源|19. 多数据源]]
  - [[Mysql#20. MyBatis-Plus 高级技巧（面试/实战）|20. 高级技巧]]

---

# Part 1：MySQL 基础

> 如果你是刚开始学 MySQL，这部分帮你快速入门。如果已熟悉，可以直接跳到 Part 2 进阶内容。

# 1. 数据类型

## 1.1 整数类型

|     |     类型     | 字节  |    范围（有符号）     |        常用场景        |
| :-: | :--------: | :-: | :------------: | :----------------: |
|     | `TINYINT`  |  1  |   -128 ~ 127   |  状态码、boolean（0/1）  |
|     | `SMALLINT` |  2  | -32768 ~ 32767 |     枚举值、小范围统计      |
|     |   `INT`    |  4  |   -21亿 ~ 21亿   | **主键、常规数字（开发最常用）** |
|     |  `BIGINT`  |  8  |     ±922亿亿     |    雪花ID、大数据量主键     |

> **开发建议**：主键用 `BIGINT` 或 `INT UNSIGNED`。状态字段用 `TINYINT`（0/1）。

## 1.2 字符串类型

|     |      类型      | 说明      |   最大长度   | 开发建议          |
| :-: | :----------: | :------ | :------: | :------------ |
|     | `VARCHAR(n)` | 可变长度字符串 | 65535 字节 | **最常用**，节省空间  |
|     |  `CHAR(n)`   | 固定长度字符串 |  255 字符  | 定长数据（手机号、身份证） |
|     |    `TEXT`    | 长文本     | 65535 字节 | 大段文本（文章内容）    |
|     |  `LONGTEXT`  | 超长文本    |   4GB    | 极长内容          |

> ==**VARCHAR vs CHAR 选择**：字段长度变化小用 CHAR（如性别、状态码），变化大用 VARCHAR（如用户名、地址）。==

## 1.3 日期时间类型

|     |                 类型       | 格式                  | 范围                      | 开发建议          |
| :-: | :------------: | :------------------ | :---------------------- | :------------ |
|     |           `DATETIME` | YYYY-MM-DD HH:MM:SS | 1000-01-01 ~ 9999-12-31 | **最常用，推荐**    |
|     |            `TIMESTAMP`   | YYYY-MM-DD HH:MM:SS | 1970 ~ 2038             | 受时区影响，有2038问题 |
|     |               `DATE`     | YYYY-MM-DD          | 1000-01-01 ~ 9999-12-31 | 只需要日期时使用      |
|     |               `TIME`     | HH:MM:SS            | -838:59:59 ~ 838:59:59  | 时间跨度          |

> ==**开发建议**：`DATETIME` 比 `TIMESTAMP` 范围更大，推荐所有时间字段都用 `DATETIME`。==

## 1.4 其他常用类型

```sql
DECIMAL(10, 2)       -- 精确小数（金额/价格必用，不能使用 FLOAT/DOUBLE）
JSON                 -- MySQL 5.7+，存储 JSON 数据
TINYINT(1)           -- 常用作布尔值（0/1）
BIGINT UNSIGNED      -- 自增主键（超过 INT 范围时）
```

> ==**金额字段必须用 `DECIMAL`**，`FLOAT`/`DOUBLE` 有精度损失！==


# 2. DDL（数据定义语言）

## 2.1 数据库操作

```sql
CREATE DATABASE `db_name` DEFAULT CHARSET utf8mb4 COLLATE utf8mb4_unicode_ci;
DROP DATABASE `db_name`;
USE `db_name`;
```

> ==**MySQL 8.0 之后，建库建表统一用 `utf8mb4`**（真正的 UTF-8，支持 emoji），不要再用 `utf8`（MySQL 的 utf8 最多 3 字节）。==

## 2.2 创建表（开发标准模板）

```sql
CREATE TABLE `user` (
    `id`         BIGINT UNSIGNED NOT NULL AUTO_INCREMENT COMMENT '主键',
    `username`   VARCHAR(50)     NOT NULL COMMENT '用户名',
    `password`   VARCHAR(255)    NOT NULL COMMENT '密码（加密后）',
    `email`      VARCHAR(100)    DEFAULT NULL COMMENT '邮箱',
    `phone`      VARCHAR(20)     DEFAULT NULL COMMENT '手机号',
    `age`        INT             DEFAULT 0 COMMENT '年龄',
    `status`     TINYINT         DEFAULT 1 COMMENT '状态：1正常 0禁用',
    `deleted`    TINYINT         DEFAULT 0 COMMENT '逻辑删除：0未删 1已删',
    `version`    INT             DEFAULT 0 COMMENT '乐观锁版本号',
    `create_by`  VARCHAR(50)     DEFAULT NULL COMMENT '创建人',
    `update_by`  VARCHAR(50)     DEFAULT NULL COMMENT '更新人',
    `create_time` DATETIME       DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
    `update_time` DATETIME       DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新时间',
    PRIMARY KEY (`id`) USING BTREE,
    KEY `idx_username` (`username`) USING BTREE,
    KEY `idx_email` (`email`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='用户表';
```

> ==**建表规范要点**：==
> 1. ==主键用 `BIGINT UNSIGNED AUTO_INCREMENT`==
> 2. ==所有表都要有 `create_time` 和 `update_time`（开发规范）==
> 3. ==引擎统一用 `InnoDB`（支持事务、行锁）==
> 4. ==字符集统一 `utf8mb4`==
> 5. ==字段尽量 `NOT NULL`，并给 DEFAULT 值==
> 6. ==建立合适的索引（`username`、`email` 等查询字段）==

## 2.3 修改表结构

```sql
-- 添加字段
ALTER TABLE `user` ADD COLUMN `nickname` VARCHAR(50) DEFAULT NULL COMMENT '昵称' AFTER `username`;

-- 修改字段类型
ALTER TABLE `user` MODIFY COLUMN `nickname` VARCHAR(100) NOT NULL COMMENT '昵称';

-- 修改字段名
ALTER TABLE `user` CHANGE COLUMN `nickname` `nick_name` VARCHAR(50) DEFAULT NULL COMMENT '昵称';

-- 删除字段
ALTER TABLE `user` DROP COLUMN `nickname`;

-- 添加索引
ALTER TABLE `user` ADD INDEX `idx_age` (`age`);
ALTER TABLE `user` ADD UNIQUE INDEX `idx_phone` (`phone`);

-- 删除索引
DROP INDEX `idx_age` ON `user`;
```


# 3. DML（数据操作语言）

## 3.1 插入

```sql
-- 单条插入
INSERT INTO `user` (`username`, `password`, `email`) VALUES ('张三', 'abc123', 'zhangsan@example.com');

-- 批量插入（推荐，性能远超逐条插入）
INSERT INTO `user` (`username`, `password`, `email`) VALUES
('张三', 'abc123', 'a@example.com'),
('李四', 'def456', 'b@example.com'),
('王五', 'ghi789', 'c@example.com');

-- 冲突处理：ON DUPLICATE KEY UPDATE
INSERT INTO `user` (`id`, `username`, `email`) VALUES (1, '张三', 'new@example.com')
ON DUPLICATE KEY UPDATE `username` = VALUES(`username`), `email` = VALUES(`email`);

-- 替换（先删后插，谨慎使用）
REPLACE INTO `user` (`id`, `username`, `email`) VALUES (1, '张三', 'new@example.com');
```

> ==**开发建议**：批量插入性能远高于逐条插入，但单次不要超过 1000 条。==

## 3.2 更新

```sql
-- 基础更新（WHERE 条件必加，否则全表更新！）
UPDATE `user` SET `email` = 'new@example.com' WHERE `id` = 1;

-- 多字段更新
UPDATE `user` SET `age` = 18, `status` = 1 WHERE `username` = '张三';
```

> ==**⚠️ 更新必加 WHERE 条件**，否则全表被更新！==

## 3.3 删除

```sql
-- 物理删除（慎用）
DELETE FROM `user` WHERE `id` = 1;

-- 逻辑删除（推荐：UPDATE 状态字段）
UPDATE `user` SET `deleted` = 1 WHERE `id` = 1;
```

> ==**开发规范：企业项目禁止物理删除，统一用逻辑删除！**==


# 4. DQL（数据查询语言）（==重点==）

## 4.1 基本查询

```sql
-- 查询指定字段
SELECT `id`, `username`, `email` FROM `user`;

-- 查询所有字段（开发中尽量避免，明确列出需要的字段）
-- SELECT * FROM user;  -- 不推荐

-- 别名
SELECT `username` AS `name`, `age` FROM `user`;

-- 去重
SELECT DISTINCT `status` FROM `user`;

-- 条件查询
SELECT * FROM `user` WHERE `age` > 18 AND `status` = 1;
SELECT * FROM `user` WHERE `age` BETWEEN 18 AND 30;
SELECT * FROM `user` WHERE `username` IN ('张三', '李四');
```

## 4.2 模糊查询

```sql
-- % 表示任意多个字符，_ 表示一个字符
SELECT * FROM `user` WHERE `username` LIKE '张%';    -- 以张开头的
SELECT * FROM `user` WHERE `username` LIKE '%三%';   -- 包含三的（==性能差，不走索引==）
SELECT * FROM `user` WHERE `username` LIKE '张_';    -- 张+一个字
```

> ==**LIKE 性能问题**：`LIKE '%xxx'` 以通配符开头会导致索引失效。全文搜索推荐用 `Elasticsearch` 或 MySQL 的全文索引。==

## 4.3 排序与分页

```sql
-- 排序（ASC 升序 / DESC 降序）
SELECT * FROM `user` ORDER BY `create_time` DESC;
SELECT * FROM `user` ORDER BY `age` ASC, `create_time` DESC;

-- 分页（LIMIT 偏移量, 条数）
SELECT * FROM `user` ORDER BY `id` DESC LIMIT 0, 10;    -- 第1页，每页10条
SELECT * FROM `user` ORDER BY `id` DESC LIMIT 10, 10;   -- 第2页

-- 分页优化（深分页问题：偏移量大时性能差）
-- ❌ 深分页性能差（OFFSET 大）
SELECT * FROM `user` ORDER BY `id` LIMIT 100000, 10;

-- ✅ 优化方案：子查询用覆盖索引
SELECT * FROM `user` 
WHERE `id` > (SELECT `id` FROM `user` ORDER BY `id` LIMIT 100000, 1) 
ORDER BY `id` LIMIT 10;
```

> ==**深分页优化**：偏移量大时 `LIMIT 100000, 10` 需要扫描前 100010 行。优化方案是先用子查询定位起始 ID，再取数据。==

## 4.4 聚合与分组

```sql
-- 聚合函数
SELECT COUNT(*) FROM `user`;                     -- 总数
SELECT COUNT(DISTINCT `status`) FROM `user`;     -- 去重统计
SELECT MAX(`age`), MIN(`age`), AVG(`age`) FROM `user`;
SELECT SUM(`score`) FROM `user` WHERE `status` = 1;

-- 分组统计
SELECT `status`, COUNT(*) AS `count` FROM `user` GROUP BY `status`;

-- HAVING：对分组结果过滤（WHERE 在分组前过滤，HAVING 在分组后过滤）
SELECT `status`, COUNT(*) AS `count` 
FROM `user` 
GROUP BY `status` 
HAVING COUNT(*) > 10;

-- 分组后排序
SELECT `status`, COUNT(*) AS `count` 
FROM `user` 
GROUP BY `status` 
ORDER BY `count` DESC;
```

> ==**WHERE vs HAVING**：`WHERE` 先过滤后分组（减少分组数据量），`HAVING` 后过滤分组结果。能用 WHERE 的优先用 WHERE。==

## 4.5 多表连接（==重中之重==）

```sql
-- INNER JOIN（内连接：两表匹配的数据）
SELECT u.`username`, o.`order_no`, o.`amount`
FROM `user` u
INNER JOIN `order` o ON u.`id` = o.`user_id`;

-- LEFT JOIN（左连接：左表全部 + 右表匹配的数据，不匹配的用 NULL）
SELECT u.`username`, o.`order_no`
FROM `user` u
LEFT JOIN `order` o ON u.`id` = o.`user_id`;

-- RIGHT JOIN（右连接：右表全部 + 左表匹配的数据）
SELECT u.`username`, o.`order_no`
FROM `user` u
RIGHT JOIN `order` o ON u.`id` = o.`user_id`;

-- 多表连接
SELECT u.`username`, o.`order_no`, oi.`product_name`
FROM `user` u
INNER JOIN `order` o ON u.`id` = o.`user_id`
INNER JOIN `order_item` oi ON o.`id` = oi.`order_id`;
```

> ==**JOIN 选择规则**：==
> - ==`INNER JOIN`：只要两表都有的数据==
> - ==`LEFT JOIN`：主表数据必须全部保留（最常用）==
> - ==**多表 JOIN 时，不要超过 3 张表**，否则考虑冗余字段或 ES==
> - ==**JOIN 的字段必须建索引**，否则性能极差==

## 4.6 子查询

```sql
-- WHERE 子查询
SELECT * FROM `user` WHERE `id` IN (SELECT `user_id` FROM `order` WHERE `amount` > 100);

-- EXISTS 子查询（性能通常优于 IN）
SELECT * FROM `user` u 
WHERE EXISTS (SELECT 1 FROM `order` o WHERE o.`user_id` = u.`id` AND o.`amount` > 100);

-- FROM 子查询（派生表）
SELECT `dept_id`, AVG(`salary`) AS `avg_salary`
FROM (SELECT * FROM `employee` WHERE `status` = 1) AS `active_emp`
GROUP BY `dept_id`;
```

> ==**IN vs EXISTS**：==
> - ==**子表数据量大**时用 `EXISTS`（`EXISTS` 只返回 true/false，不用查全部）==
> - ==**主表数据量大**时用 `IN`==
> - ==MySQL 5.6+ 对 `IN` 有优化（半连接），差距缩小了==

## 4.7 UNION 合并查询

```sql
-- UNION（去重合并）
SELECT `username` FROM `user_a`
UNION
SELECT `username` FROM `user_b`;

-- UNION ALL（不去重合并，性能优于 UNION）
SELECT `username` FROM `user_a`
UNION ALL
SELECT `username` FROM `user_b`;
```


# 5. 表设计原则（三范式）

## 三范式速记

|     |           范式 | 核心要求 | 通俗解释 | 反例 |
| :-: |:----:|:--------|:--------|:----:|
|     |           **1NF** | 字段不可再分 | 每个字段存一个值 | "爱好"字段存"篮球,游泳" |
|     |           **2NF** | 非主键字段完全依赖于主键 | 联合主键时，不要只依赖部分主键 | (学生,课程) → 成绩合理，但→ 学生姓名不合理 |
|     |           **3NF** | 非主键字段不传递依赖于主键 | 不要有A→B→C的传递依赖 | 订单表中有"用户所属部门"（应从用户表关联） |

> ==**实际开发不要死守三范式**：适当冗余字段可以避免 JOIN 查询，提高性能（空间换时间）。==

## 字段设计规范

```sql
-- 推荐
CREATE TABLE `order` (
    `id`           BIGINT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    `order_no`     VARCHAR(64)     NOT NULL COMMENT '订单号（唯一）',
    `user_id`      BIGINT UNSIGNED NOT NULL COMMENT '用户ID',
    `user_name`    VARCHAR(50)     DEFAULT NULL COMMENT '用户名（冗余字段）',
    `total_amount` DECIMAL(10, 2)  NOT NULL COMMENT '总金额',
    `status`       TINYINT         NOT NULL DEFAULT 0 COMMENT '状态',
    `create_time`  DATETIME        NOT NULL DEFAULT CURRENT_TIMESTAMP,
    `update_time`  DATETIME        NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    UNIQUE KEY `uk_order_no` (`order_no`),
    KEY `idx_user_id` (`user_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='订单表';
```

> ==**冗余字段技巧**：在 `order` 表中冗余 `user_name`，查询订单时不用 JOIN `user` 表，性能提升明显。适合数据不频繁变化的字段。==


---

# Part 2：MySQL 进阶（==开发必备==）

# 6. 索引（Index）

## 6.1 索引类型

|     |           索引类型 | 特点 | 使用场景 |
| :-: |:--------:|:----|:--------|
|     |           **B+Tree 索引** | MySQL 默认索引结构，有序 | **绝大多数场景** |
|     |           HASH 索引 | 等值查询极快，不支持范围查询 | Memory 引擎专用 |
|     |           FULLTEXT 索引 | 全文检索 | 大文本搜索 |
|     |           **聚簇索引** | InnoDB 主键索引，叶子节点存整行数据 | 主键（自动创建） |
|     |           **二级索引** | 非主键索引，叶子节点存主键值 | 普通索引 |

## 6.2 B+Tree 索引原理（==面试高频==）

```
MySQL InnoDB B+Tree 特点：
┌─────────────────────────────────────────┐
│ 1. 只有叶子节点存数据，非叶子节点只存索引     │
│ 2. 叶子节点之间通过双向链表连接，支持范围查询   │
│ 3. 所有数据都在叶子节点，查询任何数据都走相同    │
│    的 IO 次数（树高度，一般 3-4 层）         │
│ 4. 一个节点 = 一个数据页（默认 16KB）        │
│ 5. 主键建议用自增 BIGINT（页分裂少）         │
│ 6. 非主键索引的叶子节点存的是主键值（回表）     │
└─────────────────────────────────────────┘
```

> ==**B+Tree vs B-Tree 核心区别**：B+Tree 非叶子节点不存数据，能存放更多索引，树更矮，查询更稳定。==

## 6.3 索引操作

```sql
-- 单列索引
CREATE INDEX `idx_username` ON `user` (`username`);

-- 联合索引（==最左前缀原则==）
CREATE INDEX `idx_name_age_status` ON `user` (`username`, `age`, `status`);

-- 唯一索引
CREATE UNIQUE INDEX `uk_email` ON `user` (`email`);

-- 查看索引
SHOW INDEX FROM `user`;

-- 删除索引
DROP INDEX `idx_username` ON `user`;

-- EXPLAIN 查看是否走索引（重点）
EXPLAIN SELECT * FROM `user` WHERE `username` = '张三';
```

## 6.4 联合索引最左前缀原则

```sql
-- 索引：(username, age, status)

-- ✅ 走索引
WHERE `username` = '张三'                          -- 第一列
WHERE `username` = '张三' AND `age` = 18           -- 第一、二列
WHERE `username` = '张三' AND `age` = 18 AND `status` = 1  -- 全部
WHERE `username` LIKE '张%'                        -- 范围匹配（走索引）

-- ❌ 不走索引
WHERE `age` = 18                                  -- 跳过了第一列
WHERE `status` = 1                                -- 跳过了第一、二列
WHERE `username` = '张三' AND `status` = 1         -- 跳过了第二列
```

> ==**联合索引核心：最左前缀原则**——查询条件必须从索引最左列开始，跳过任何一列，后面的列就走不了索引。==

## 6.5 索引失效场景（==开发避坑==）

```sql
-- ❌ 索引失效常见场景
-- 1. LIKE 以 % 开头
SELECT * FROM `user` WHERE `username` LIKE '%三%';

-- 2. 对索引列做函数操作
SELECT * FROM `user` WHERE SUBSTR(`username`, 1, 1) = '张';

-- 3. 类型隐式转换（phone 是 VARCHAR 类型，传入数字）
SELECT * FROM `user` WHERE `phone` = 13800138000;  -- 数字→字符串不走索引

-- 4. OR 条件中有非索引列
--    假设只有 username 有索引
SELECT * FROM `user` WHERE `username` = '张三' OR `age` = 18;

-- 5. != 或 <> 操作（大部分情况下不走索引）
SELECT * FROM `user` WHERE `status` != 1;

-- 6. IS NULL / IS NOT NULL（可能不走索引）
SELECT * FROM `user` WHERE `email` IS NULL;

-- 7. NOT IN / NOT EXISTS
SELECT * FROM `user` WHERE `id` NOT IN (1, 2, 3);
```

## 6.6 EXPLAIN 执行计划分析

```sql
EXPLAIN SELECT u.`username`, o.`order_no` 
FROM `user` u 
LEFT JOIN `order` o ON u.`id` = o.`user_id` 
WHERE u.`status` = 1 \G
```

**EXPLAIN 关键字段解读：**

|      字段 | 值 | 含义 |
| :-: |:----:|:--:|:------|
|      `type` | `const` | 唯一索引等值查找（最快） |
|      | `ref` | 非唯一索引等值查找（很快） |
|      | `range` | 范围查找（可接受） |
|      | `index` | 扫描全索引（一般） |
|      | `ALL` | 全表扫描（需要优化！） |
|      `possible_keys` | — | 可能用到的索引 |
|      `key` | — | **实际用到的索引（重点看这个）** |
|      `key_len` | — | 索引使用的字节数（越长越精确） |
|      `rows` | — | **扫描行数（越小越好）** |
|      `Extra` | `Using index` | 覆盖索引，不回表（最优） |
|      | `Using where` | 回表后在内存过滤 |
|      | `Using filesort` | 需要额外排序（性能差，需优化） |
|      | `Using temporary` | 需要临时表（性能很差，需优化） |

> ==**EXPLAIN 开发建议**：==
> - ==type 至少到 `range`，最好 `ref` 或 `const`==
> - ==避免 `ALL`（全表扫描）==
> - ==Extra 尽量避免 `filesort` 和 `temporary`==
> - ==rows 越小越好，说明扫描的数据量少==

## 6.7 覆盖索引与回表

```sql
-- 表有联合索引 idx_name_age (username, age)

-- ❌ 回表查询：select 了索引中没有的字段
SELECT `username`, `age`, `email` FROM `user` WHERE `username` = '张三';
-- 先查二级索引找到主键ID，再根据ID回主键索引查email

-- ✅ 覆盖索引：查询字段全在索引中，不用回表
SELECT `username`, `age` FROM `user` WHERE `username` = '张三';
-- 直接在二级索引中就能拿到所有数据（Extra: Using index）
```

> ==**覆盖索引优化**：尽量让 SELECT 的字段都在索引中，避免回表。Extra 显示 `Using index` 说明是覆盖索引，性能最优。==


# 7. 事务（Transaction）（==面试高频==）

## 7.1 ACID 特性

|     |           特性 | 含义 | 实现机制 |
| :-: |:----:|:----|:--------|
|     |           **A**tomicity（原子性） | 事务要么全成功要么全回滚 | undo log（回滚日志） |
|     |           **C**onsistency（一致性） | 数据始终满足约束规则 | 应用层 + 数据库约束 |
|     |           **I**solation（隔离性） | 并发事务互不干扰 | 锁 + MVCC |
|     |           **D**urability（持久性） | 提交后数据永久保存 | redo log（重做日志） |

## 7.2 隔离级别

|     |           隔离级别 | 脏读 | 不可重复读 | 幻读 | 说明 |
| :-: |:---------:|:----:|:----------:|:----:|:------|
|     |           READ UNCOMMITTED | ✅ | ✅ | ✅ | 能读到未提交数据（基本不用） |
|     |           **READ COMMITTED** | ❌ | ✅ | ✅ | 只能读已提交（**Oracle 默认**） |
|     |           **REPEATABLE READ** | ❌ | ❌ | ✅ | **MySQL 默认隔离级别** |
|     |           SERIALIZABLE | ❌ | ❌ | ❌ | 串行化，性能极差 |

```sql
-- 查看当前隔离级别
SELECT @@transaction_isolation;  -- MySQL 8.0
SELECT @@tx_isolation;           -- MySQL 5.x

-- 设置隔离级别（当前会话）
SET SESSION TRANSACTION ISOLATION LEVEL READ COMMITTED;
```

> ==**MySQL 默认是 REPEATABLE READ**，但很多互联网公司改为 **READ COMMITTED**（性能更好，配合 binlog row 模式可避免很多问题）。==

## 7.3 MVCC（多版本并发控制，==面试重难点==）

```
MVCC 核心组件：
┌─────────────────────────────────────┐
│ 1. 隐藏字段：                         │
│    - DB_TRX_ID：最后修改这个行的事务ID   │
│    - DB_ROLL_PTR：回滚指针（指向 undo log）│
│    - DB_ROW_ID：行ID（如果没主键时）    │
│                                      │
│ 2. undo log：记录数据的历史版本         │
│                                      │
│ 3. Read View（读视图）：               │
│    - m_ids：活跃事务ID列表             │
│    - min_trx_id：最小活跃事务ID         │
│    - max_trx_id：最大事务ID            │
│    - creator_trx_id：创建该视图的事务ID │
└─────────────────────────────────────┘
```

**MVCC 判断规则（当前事务能否看到某个版本）：**

```
数据行的 DB_TRX_ID ⊆ Read View：

1. DB_TRX_ID < min_trx_id   → ✅ 可见（已提交的老事务）
2. DB_TRX_ID > max_trx_id   → ❌ 不可见（未来的事务）
3. DB_TRX_ID == creator_trx_id → ✅ 可见（自己改的）
4. DB_TRX_ID ∈ m_ids        → ❌ 不可见（未提交的活跃事务）
```

> ==**MVCC + 间隙锁解决了 REPEATABLE READ 的幻读问题**（InnoDB 在 RR 级别下基本不会出现幻读）。==

## 7.4 事务操作

```sql
-- 开启事务
START TRANSACTION;
-- 或
BEGIN;

-- 执行 SQL
UPDATE `account` SET `balance` = `balance` - 100 WHERE `id` = 1;
UPDATE `account` SET `balance` = `balance` + 100 WHERE `id` = 2;

-- 提交
COMMIT;

-- 回滚
ROLLBACK;

-- 设置保存点
SAVEPOINT sp1;
ROLLBACK TO sp1;
```

## 7.5 Spring 事务使用

```java
// 在 Service 层使用 @Transactional
@Service
public class OrderService {
    
    @Autowired
    private AccountMapper accountMapper;
    
    @Transactional(rollbackFor = Exception.class)  // 所有异常都回滚
    public void transfer(Long fromId, Long toId, BigDecimal amount) {
        accountMapper.deduct(fromId, amount);      // 扣钱
        accountMapper.add(toId, amount);           // 加钱
        // 任何一步抛出异常，事务回滚
    }
    
    @Transactional(readOnly = true)                // 只读事务（优化查询）
    public Account getById(Long id) {
        return accountMapper.selectById(id);
    }
}
```

> ==**@Transactional 要点**：==
> - ==默认只回滚 `RuntimeException`，`rollbackFor = Exception.class` 使所有异常都回滚==
> - ==`readOnly = true` 优化查询性能==
> - ==事务必须通过代理对象调用才能生效（同类方法直接调用无效！）==


# 8. 锁机制

## 8.1 行锁（Row Lock）

```sql
-- 行锁是 InnoDB 默认锁机制，只锁住被操作的行
-- 锁是加在索引上的，不走索引的行锁会退化为表锁！

-- 共享锁（S锁）：允许其他事务读，不允许写
SELECT * FROM `user` WHERE `id` = 1 LOCK IN SHARE MODE;

-- 排他锁（X锁）：不允许其他事务读和写
SELECT * FROM `user` WHERE `id` = 1 FOR UPDATE;
```

> ==**行锁依赖索引**：如果 WHERE 条件不走索引，行锁会升级为表锁！==

## 8.2 表锁（Table Lock）

```sql
-- 手动加表锁
LOCK TABLES `user` READ;   -- 读锁（共享）
LOCK TABLES `user` WRITE;  -- 写锁（排他）

UNLOCK TABLES;             -- 释放表锁
```

## 8.3 间隙锁（Gap Lock）

```
间隙锁锁定一个范围（不包含记录本身），防止幻读。

例如：表中有 id = 1, 5, 10 三条记录

SELECT * FROM user WHERE id BETWEEN 3 AND 8 FOR UPDATE;

→ 间隙锁会锁住 (1,5) 和 (5,10) 这两个区间
→ 其他事务无法在 id=3 和 id=7 插入新记录
→ 这就是为什么 RR 级别下能防幻读
```

> ==**间隙锁只在 REPEATABLE READ 级别有效**，RC 级别没有间隙锁。==

## 8.4 死锁

```sql
-- 死锁排查（重要）
-- 1. 查看最近死锁
SHOW ENGINE INNODB STATUS \G

-- 2. 查看当前运行的事务
SELECT * FROM information_schema.INNODB_TRX \G

-- 3. 查看锁等待
SELECT * FROM information_schema.INNODB_LOCK_WAITS;

-- 4. 杀掉阻塞事务
KILL <trx_mysql_thread_id>;
```

> ==**死锁预防**：==
> 1. ==所有事务按相同顺序访问资源（统一先 user 后 order 顺序）==
> 2. ==尽量缩短事务时间==
> 3. ==大事务拆小事务==
> 4. ==合理设计索引，让行锁更精确==


# 9. SQL 性能优化（==实战重点==）

## 9.1 慢查询日志

```sql
-- 查看是否开启慢查询日志
SHOW VARIABLES LIKE 'slow_query%';
SHOW VARIABLES LIKE 'long_query_time';

-- 开启慢查询日志（生产环境谨慎）
SET GLOBAL slow_query_log = ON;
SET GLOBAL long_query_time = 1;       -- 超过 1 秒的 SQL
SET GLOBAL log_queries_not_using_indexes = ON;  -- 没走索引的也记录

-- 分析慢查询日志
mysqldumpslow -s t -t 10 /var/lib/mysql/slow.log  -- 按时间排序取前10
```

## 9.2 SQL 优化原则

```sql
-- ✅ 1. 避免 SELECT *，只查需要的字段
-- ❌ 不推荐
SELECT * FROM `user`;
-- ✅ 推荐
SELECT `id`, `username`, `email` FROM `user`;

-- ✅ 2. 分页查询不要 OFFSET 太大（深分页优化）
-- ❌ 不推荐（OFFSET 1000000 扫描大量数据）
SELECT * FROM `user` ORDER BY `id` LIMIT 1000000, 10;
-- ✅ 推荐（通过子查询先定位起始 ID）
SELECT * FROM `user` 
WHERE `id` > (SELECT `id` FROM `user` ORDER BY `id` LIMIT 1000000, 1) 
ORDER BY `id` LIMIT 10;

-- ✅ 3. WHERE 条件中避免函数操作
-- ❌ 不推荐
SELECT * FROM `user` WHERE DATE(`create_time`) = '2026-06-17';
-- ✅ 推荐（可走索引）
SELECT * FROM `user` WHERE `create_time` >= '2026-06-17 00:00:00' 
  AND `create_time` < '2026-06-18 00:00:00';

-- ✅ 4. 用 UNION ALL 替代 UNION（如果不需要去重）
-- ✅ 5. JOIN 字段必须建索引
-- ✅ 6. 用 EXISTS 替代 IN（当子表数据量大时）
```

## 9.3 优化口诀

```
全值匹配我最爱，最左前缀要遵守；
带头大哥不能死，中间兄弟不能断；
索引列上少计算，范围之后全失效；
LIKE百分写最右，覆盖索引不写星；
不等空值还有OR，索引失效要少用；
VAR引号不可丢，SQL优化有诀窍。
```

## 9.4 分表策略

```sql
-- 水平分表：按某个字段取模分表（按 user_id 分 16 张表）
-- 表名：user_0, user_1, ..., user_15
-- 路由规则：user_id % 16 = 表编号

-- 垂直分表：将大字段拆分到另一张表
-- user 表：id, username, email, password, status
-- user_detail 表：id, user_id, avatar, intro, address
```

> ==**分表场景**：单表超过 1000 万行或超过 50GB 时考虑分表。优先考虑索引优化、读写分离，最后才分表。==


# 10. 常用函数与语法

## 10.1 字符串函数

```sql
SELECT CONCAT('Hello', ' ', 'World');          -- 字符串拼接
SELECT CONCAT_WS(',', 'a', 'b', 'c');          -- 带分隔符拼接 → a,b,c
SELECT LENGTH('你好');                          -- 字节数（utf8mb4: 6）
SELECT CHAR_LENGTH('你好');                     -- 字符数（2）
SELECT UPPER('hello'), LOWER('HELLO');          -- 大小写转换
SELECT TRIM('  hello  ');                       -- 去除首尾空格
SELECT REPLACE('hello world', 'world', 'mysql');-- 替换
SELECT SUBSTRING('hello', 1, 2);                -- 截取 → he（下标从1开始！）
```

## 10.2 日期函数

```sql
SELECT NOW();                                   -- 当前日期时间
SELECT CURDATE();                               -- 当前日期
SELECT CURTIME();                               -- 当前时间
SELECT DATE_ADD(NOW(), INTERVAL 1 DAY);         -- 加一天
SELECT DATE_SUB(NOW(), INTERVAL 1 MONTH);       -- 减一月
SELECT DATEDIFF('2026-06-17', '2026-01-01');    -- 相差天数
SELECT DATE_FORMAT(NOW(), '%Y-%m-%d %H:%i:%s'); -- 格式化
SELECT UNIX_TIMESTAMP(NOW());                   -- 转时间戳
SELECT FROM_UNIXTIME(1718612345);               -- 时间戳转日期
```

## 10.3 条件与流程控制

```sql
-- IF 函数
SELECT `username`, IF(`status` = 1, '正常', '禁用') AS `status_name` FROM `user`;

-- CASE WHEN
SELECT `username`,
    CASE 
        WHEN `age` < 18 THEN '未成年'
        WHEN `age` BETWEEN 18 AND 60 THEN '成年'
        ELSE '老年'
    END AS `age_group`
FROM `user`;

-- IFNULL（处理 NULL）
SELECT `username`, IFNULL(`email`, '未填写') AS `email` FROM `user`;
```

## 10.4 窗口函数（MySQL 8.0+，==面试加分项==）

```sql
-- ROW_NUMBER()：排名（无重复）
SELECT `username`, `score`,
    ROW_NUMBER() OVER (ORDER BY `score` DESC) AS `rank`
FROM `exam`;

-- RANK()：排名（相同分数并列，会跳过排名）
SELECT `username`, `score`,
    RANK() OVER (ORDER BY `score` DESC) AS `rank`
FROM `exam`;

-- DENSE_RANK()：排名（相同分数并列，不跳过排名）
SELECT `username`, `score`,
    DENSE_RANK() OVER (ORDER BY `score` DESC) AS `rank`
FROM `exam`;

-- 分组排名
SELECT `dept_id`, `username`, `salary`,
    RANK() OVER (PARTITION BY `dept_id` ORDER BY `salary` DESC) AS `dept_rank`
FROM `employee`;

-- LAG/LEAD：前后行数据
SELECT `username`, `salary`,
    LAG(`salary`, 1) OVER (ORDER BY `id`) AS `prev_salary`,      -- 前一行
    LEAD(`salary`, 1) OVER (ORDER BY `id`) AS `next_salary`      -- 后一行
FROM `employee`;
```

> ==**窗口函数 vs GROUP BY**：GROUP BY 分组后每组只剩一行，窗口函数保留每行数据并在行上做计算。==


---

# Part 3：MyBatis-Plus（==开发实战==）

# 11. 快速开始

## 11.1 依赖引入（Spring Boot 3.x）

```xml
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-spring-boot3-starter</artifactId>
    <version>3.5.7</version>
</dependency>
```

```xml
<!-- Spring Boot 2.x -->
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-boot-starter</artifactId>
    <version>3.5.7</version>
</dependency>
```

## 11.2 配置 application.yml

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/db_name?useUnicode=true&characterEncoding=utf-8&serverTimezone=Asia/Shanghai
    username: root
    password: 123456
    driver-class-name: com.mysql.cj.jdbc.Driver
    # HikariCP 连接池配置（Spring Boot 2.0+ 默认连接池）
    hikari:
      minimum-idle: 5
      maximum-pool-size: 20
      idle-timeout: 300000
      max-lifetime: 1200000
      connection-timeout: 30000

mybatis-plus:
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl  # 开发时打印 SQL（生产去掉）
    map-underscore-to-camel-case: true       # 驼峰命名映射（默认开启）
  global-config:
    db-config:
      logic-delete-field: deleted            # 逻辑删除字段名
      logic-delete-value: 1                  # 逻辑已删除值
      logic-not-delete-value: 0              # 逻辑未删除值
      id-type: auto                          # 主键自增
  mapper-locations: classpath*:mapper/**/*.xml  # Mapper XML 路径
```

## 11.3 Spring Boot 启动类

```java
@SpringBootApplication
@MapperScan("com.example.demo.mapper")  // 扫描 Mapper 接口
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

## 11.4 实体类与 Mapper

```java
@Data
@TableName("user")           // 指定数据库表名
public class User {
    @TableId(type = IdType.AUTO)                   // 主键自增
    private Long id;
    
    @TableField("username")                        // 字段映射（驼峰自动转下划线可不写）
    private String username;
    
    private String password;
    private String email;
    private Integer age;
    private Integer status;
    
    @TableLogic                                     // 逻辑删除注解
    private Integer deleted;
    
    @Version                                        // 乐观锁
    private Integer version;
    
    @TableField(fill = FieldFill.INSERT)            // 插入时自动填充
    private LocalDateTime createTime;
    
    @TableField(fill = FieldFill.INSERT_UPDATE)     // 插入+更新时自动填充
    private LocalDateTime updateTime;
}

// === Mapper 接口：继承 BaseMapper 即可拥有 CRUD ===
@Mapper
public interface UserMapper extends BaseMapper<User> {
    // 无需写任何方法，BaseMapper 已经提供了常用的 CRUD
}
```

> ==**BaseMapper 内置方法**：`insert`、`deleteById`、`updateById`、`selectById`、`selectList`、`selectPage` 等，无需手写 SQL。==


# 12. CRUD 接口

## 12.1 Insert

```java
// 基础插入
User user = new User();
user.setUsername("张三");
user.setPassword("abc123");
user.setEmail("zhangsan@example.com");
int rows = userMapper.insert(user);          // 返回影响行数
Long id = user.getId();                      // 插入后主键自动回填到对象
```

## 12.2 Delete

```java
// 根据 ID 删除
userMapper.deleteById(1L);

// 根据条件删除
userMapper.delete(new QueryWrapper<User>()
    .eq("username", "张三"));

// 批量删除
userMapper.deleteBatchIds(Arrays.asList(1L, 2L, 3L));

// 逻辑删除（@TableLogic 注解后，delete 操作变成 UPDATE）
userMapper.deleteById(1L);   // 实际执行：UPDATE user SET deleted=1 WHERE id=1
```

## 12.3 Update

```java
// 根据 ID 更新
User user = new User();
user.setId(1L);
user.setEmail("new@example.com");
userMapper.updateById(user);  // 只更新非 null 字段

// 条件更新
userMapper.update(
    new User().setEmail("new@example.com"),
    new QueryWrapper<User>().eq("username", "张三")
);
```

> ==**updateById 特点**：只更新非 null 字段，配合 `@Version` 乐观锁时能防并发覆盖。==

## 12.4 Select

```java
// === 单个查询 ===
User user = userMapper.selectById(1L);

// 条件查询单条
User user = userMapper.selectOne(new QueryWrapper<User>()
    .eq("username", "张三"));

// === 列表查询 ===
// 查询全部
List<User> list = userMapper.selectList(null);

// 条件查询列表
List<User> list = userMapper.selectList(new QueryWrapper<User>()
    .eq("status", 1)
    .orderByDesc("create_time"));

// === 批量查询 ===
List<User> list = userMapper.selectBatchIds(Arrays.asList(1L, 2L, 3L));

// === 数量统计 ===
Long count = userMapper.selectCount(new QueryWrapper<User>()
    .eq("status", 1));

// === 分页查询 ===
Page<User> page = userMapper.selectPage(
    new Page<>(1, 10),                              // 第1页，每页10条
    new QueryWrapper<User>().eq("status", 1)
);
List<User> records = page.getRecords();             // 当前页数据
long total = page.getTotal();                       // 总记录数
long pages = page.getPages();                       // 总页数
```


# 13. 条件构造器 Wrapper（==重点==）

## 13.1 QueryWrapper（基本条件）

```java
// === 基础条件 ===
QueryWrapper<User> qw = new QueryWrapper<>();

qw.eq("username", "张三");         // = 等于
qw.ne("status", 0);               // <> 不等于
qw.gt("age", 18);                 // > 大于
qw.ge("age", 18);                 // >= 大于等于
qw.lt("age", 60);                 // < 小于
qw.le("age", 60);                 // <= 小于等于

// === 模糊查询 ===
qw.like("username", "张");        // LIKE '%张%'
qw.likeLeft("username", "张");    // LIKE '%张'
qw.likeRight("username", "张");   // LIKE '张%'

// === 范围查询 ===
qw.between("age", 18, 60);        // BETWEEN 18 AND 60
qw.notBetween("age", 18, 60);
qw.in("status", 0, 1, 2);         // IN (0,1,2)
qw.notIn("status", 0, 1);

// === NULL 处理 ===
qw.isNull("email");               // IS NULL
qw.isNotNull("email");            // IS NOT NULL

// === 排序 ===
qw.orderByAsc("age");             // ORDER BY age ASC
qw.orderByDesc("create_time");    // ORDER BY create_time DESC

// === 其他 ===
qw.exists("SELECT 1 FROM order WHERE user_id = user.id");
qw.notExists("...");
qw.groupBy("status");
qw.having("count(*) > 10");

// === 链式调用（推荐） ===
QueryWrapper<User> qw = new QueryWrapper<User>()
    .eq("status", 1)
    .like("username", "张")
    .orderByDesc("create_time")
    .last("LIMIT 10");            // 追加原生 SQL 片段
```

## 13.2 LambdaQueryWrapper（类型安全，推荐）

```java
// 使用 Lambda 表达式，不写字符串字段名（避免拼写错误）
LambdaQueryWrapper<User> lqw = new LambdaQueryWrapper<>();

lqw.eq(User::getUsername, "张三");          // username = '张三'
lqw.like(User::getEmail, "@example.com");   // email LIKE '%@example.com%'
lqw.ge(User::getAge, 18);                   // age >= 18
lqw.eq(User::getStatus, 1);                 // status = 1
lqw.orderByDesc(User::getCreateTime);       // ORDER BY create_time DESC

// 复杂条件
lqw.and(w -> 
    w.eq(User::getStatus, 1)
     .or()
     .eq(User::getStatus, 2)
);
```

> ==**开发推荐**：优先使用 `LambdaQueryWrapper`，避免写字符串字段名，编译期就能发现错误。==

## 13.3 UpdateWrapper（更新用）

```java
// 更新时使用 Wrapper 指定条件
UpdateWrapper<User> uw = new UpdateWrapper<>();

// set 部分字段
uw.set("email", "new@example.com")
  .set("status", 1)
  .eq("username", "张三");

userMapper.update(null, uw);  // 第一个参数为 null，用 wrapper 中的 set

// Lambda 写法
LambdaUpdateWrapper<User> lu = new LambdaUpdateWrapper<>();
lu.set(User::getEmail, "new@example.com")
  .set(User::getStatus, 1)
  .eq(User::getUsername, "张三");
userMapper.update(null, lu);
```

## 13.4 复杂查询示例

```java
// === 多条件组合查询 ===
LambdaQueryWrapper<User> lqw = new LambdaQueryWrapper<>();

// (status = 1 AND age > 18) OR (status = 2 AND username LIKE '张%')
lqw.and(w1 -> w1.eq(User::getStatus, 1).gt(User::getAge, 18))
   .or(w2 -> w2.eq(User::getStatus, 2).like(User::getUsername, "张"));

// === 指定查询字段（避免查所有字段） ===
LambdaQueryWrapper<User> lqw = new LambdaQueryWrapper<User>()
    .select(User::getId, User::getUsername, User::getEmail)  // 只查这几个字段
    .eq(User::getStatus, 1);

// === 子查询 ===
QueryWrapper<User> qw = new QueryWrapper<>();
qw.inSql("id", "SELECT user_id FROM `order` WHERE amount > 100");
```

## 13.5 Wrapper 方法速查表

|     |           方法 | SQL 片段 | 说明 |
| :-: |:----:|:---------|:----|
|     |           `eq` | `=` | 等于 |
|     |           `ne` | `<>` | 不等于 |
|     |           `gt` / `ge` | `>` / `>=` | 大于 / 大于等于 |
|     |           `lt` / `le` | `<` / `<=` | 小于 / 小于等于 |
|     |           `between` | `BETWEEN ... AND ...` | 范围查询 |
|     |           `like` | `LIKE '%值%'` | 模糊匹配 |
|     |           `likeLeft` | `LIKE '%值'` | 左模糊 |
|     |           `likeRight` | `LIKE '值%'` | 右模糊（走索引） |
|     |           `in` | `IN (v1, v2)` | 包含 |
|     |           `isNull` | `IS NULL` | 为空 |
|     |           `orderByAsc/Desc` | `ORDER BY` | 排序 |
|     |           `groupBy` | `GROUP BY` | 分组 |
|     |           `having` | `HAVING` | 分组后过滤 |
|     |           `last` | 追加原生 SQL | 拼接到 SQL 末尾 |
|     |           `apply` | 原生 SQL 片段 | 拼接任意 SQL |


# 14. 分页插件

## 14.1 配置分页插件

```java
@Configuration
public class MyBatisPlusConfig {
    
    @Bean
    public MybatisPlusInterceptor mybatisPlusInterceptor() {
        MybatisPlusInterceptor interceptor = new MybatisPlusInterceptor();
        
        // 分页插件（必须添加）
        PaginationInnerInterceptor pagination = new PaginationInnerInterceptor(DbType.MYSQL);
        pagination.setOverflow(false);                // 超出总页数是否回第一页
        pagination.setMaxLimit(500L);                  // 单页最大条数（防攻击）
        interceptor.addInnerInterceptor(pagination);
        
        // 乐观锁插件（建议添加）
        interceptor.addInnerInterceptor(new OptimisticLockerInnerInterceptor());
        
        return interceptor;
    }
}
```

## 14.2 分页使用

```java
// === 基本分页 ===
Page<User> page = userMapper.selectPage(
    new Page<>(1, 10),      // 第1页，每页10条
    new LambdaQueryWrapper<User>().eq(User::getStatus, 1)
);

page.getRecords();           // 当前页数据
page.getTotal();             // 总条数
page.getPages();             // 总页数
page.getCurrent();           // 当前页
page.getSize();              // 每页条数
page.hasNext();              // 是否有下一页
page.hasPrevious();          // 是否有上一页

// === 自定义 XML 分页（复杂查询用） ===
// Mapper 接口
Page<UserVO> selectUserPage(Page<UserVO> page, @Param("param") UserQueryParam param);

// XML
// <select id="selectUserPage" resultType="com.example.vo.UserVO">
//     SELECT u.*, o.order_count 
//     FROM user u 
//     LEFT JOIN (SELECT user_id, COUNT(*) order_count FROM `order` GROUP BY user_id) o 
//         ON u.id = o.user_id
//     WHERE u.status = #{param.status}
// </select>
```

> ==**分页注意**：自定义 XML 分页时，参数中必须有 `Page` 对象且为第一个参数，MP 会自动拦截 SQL 加 `LIMIT`。==


# 15. 自动填充

## 15.1 实现 MetaObjectHandler

```java
@Component
public class MyMetaObjectHandler implements MetaObjectHandler {
    
    @Override
    public void insertFill(MetaObject metaObject) {
        this.strictInsertFill(metaObject, "createTime", LocalDateTime.class, LocalDateTime.now());
        this.strictInsertFill(metaObject, "updateTime", LocalDateTime.class, LocalDateTime.now());
        this.strictInsertFill(metaObject, "createBy", String.class, getCurrentUser());
    }
    
    @Override
    public void updateFill(MetaObject metaObject) {
        this.strictUpdateFill(metaObject, "updateTime", LocalDateTime.class, LocalDateTime.now());
        this.strictUpdateFill(metaObject, "updateBy", String.class, getCurrentUser());
    }
    
    private String getCurrentUser() {
        // 从 Spring Security 或 Shiro 中获取当前用户
        // return SecurityUtils.getCurrentUsername();
        return "system";
    }
}
```

## 15.2 实体类配置

```java
@Data
public class User {
    // ... 其他字段
    
    @TableField(fill = FieldFill.INSERT)          // 插入时填充
    private LocalDateTime createTime;
    
    @TableField(fill = FieldFill.INSERT_UPDATE)   // 插入+更新时填充
    private LocalDateTime updateTime;
    
    @TableField(fill = FieldFill.INSERT)
    private String createBy;
    
    @TableField(fill = FieldFill.INSERT_UPDATE)
    private String updateBy;
}
```

> ==**自动填充 vs 数据库 DEFAULT**：推荐用 MP 自动填充（`MetaObjectHandler`）而非数据库的 `CURRENT_TIMESTAMP`。代码层面更可控，且能填充操作人字段。==


# 16. 逻辑删除

## 16.1 配置

```yaml
mybatis-plus:
  global-config:
    db-config:
      logic-delete-field: deleted         # 逻辑删除字段（实体类字段名）
      logic-delete-value: 1               # 已删除的值（默认 1）
      logic-not-delete-value: 0           # 未删除的值（默认 0）
```

## 16.2 实体类

```java
@Data
public class User {
    // ...
    @TableLogic
    @TableField("deleted")
    private Integer deleted;
}
```

## 16.3 使用效果

```java
// 删除→自动变成 UPDATE 逻辑删除
userMapper.deleteById(1L);
// 执行：UPDATE user SET deleted=1 WHERE id=1 AND deleted=0

// 查询→自动带上 deleted=0 条件
userMapper.selectList(null);
// 执行：SELECT * FROM user WHERE deleted=0

// 查全部（包含已删除的）
userMapper.selectList(new QueryWrapper<User>().last("AND deleted=1"));
// 注意：需要使用 last 覆盖自动条件
```

> ==**逻辑删除注意**：==
> - ==唯一索引要联合 `deleted` 字段（否则逻辑删除后不能新建相同值的记录）==
> - ==JOIN 时也要注意加上 `AND deleted=0`==
> - ==逻辑删除的字段也建议建索引==


# 17. 乐观锁

## 17.1 配置

```java
// 在 MybatisPlusInterceptor 中添加乐观锁插件
interceptor.addInnerInterceptor(new OptimisticLockerInnerInterceptor());
```

## 17.2 实体类

```java
@Data
public class User {
    // ...
    @Version
    @TableField("version")
    private Integer version;
}
```

## 17.3 使用效果

```java
// 先查询
User user = userMapper.selectById(1L);   // version = 0
// 修改
user.setEmail("new@example.com");
// 更新时自动带上 version 条件
userMapper.updateById(user);
// 执行：UPDATE user SET email='...', version=1 WHERE id=1 AND version=0
// 如果 version 不匹配（被其他线程改了），更新 0 行 → 重试或报错

// 更新失败处理
boolean success = userMapper.updateById(user) > 0;
if (!success) {
    // 乐观锁冲突，数据已被修改，需要重新查询再更新
    throw new BusinessException("数据已被他人修改，请刷新后重试");
}
```

> ==**乐观锁最佳实践**：==
> - ==适用于读多写少场景（如商品库存更新）==
> - ==写冲突频繁的场景用**悲观锁**（`FOR UPDATE`）==
> - ==更新时必须带上 `@Version` 字段的旧值==


# 18. 代码生成器

## 18.1 依赖

```xml
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-generator</artifactId>
    <version>3.5.7</version>
</dependency>
<dependency>
    <groupId>org.apache.velocity</groupId>
    <artifactId>velocity-engine-core</artifactId>
    <version>2.3</version>
</dependency>
```

## 18.2 自动生成代码

```java
public class CodeGenerator {
    
    public static void main(String[] args) {
        FastAutoGenerator.create("jdbc:mysql://localhost:3306/db_name", "root", "123456")
            .globalConfig(builder -> builder
                .author("开发者")                     // 作者
                .outputDir("src/main/java")          // 输出目录
                .enableSwagger()                     // 开启 Swagger
            )
            .packageConfig(builder -> builder
                .parent("com.example.demo")          // 父包名
                .entity("entity")                    // 实体类包名
                .service("service")                  // Service 包名
                .controller("controller")            // Controller 包名
                .mapper("mapper")                    // Mapper 包名
            )
            .strategyConfig(builder -> builder
                .addInclude("user", "order")          // 要生成的表名
                .addTablePrefix("t_")                 // 表前缀过滤（t_user → User）
                .entityBuilder()
                    .enableLombok()                   // 使用 Lombok
                    .enableTableFieldAnnotation()     // 开启字段注解
                    .versionColumnName("version")     // 乐观锁字段
                    .logicDeleteColumnName("deleted") // 逻辑删除字段
                .controllerBuilder()
                    .enableRestStyle()                // @RestController
                .serviceBuilder()
                    .formatServiceFileName("%sService")  // UserService
                    .formatServiceImplFileName("%sServiceImpl")
            )
            .execute();
    }
}
```

> ==**生成器是提效神器**：数据库建好表后直接生成 Entity、Mapper、Service、Controller，几分钟就能完成基础 CRUD。==


# 19. 多数据源

## 19.1 依赖

```xml
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>dynamic-datasource-spring-boot3-starter</artifactId>
    <version>4.3.1</version>
</dependency>
```

## 19.2 配置

```yaml
spring:
  datasource:
    dynamic:
      primary: master                   # 默认数据源
      strict: false                     # 未匹配到数据源是否抛异常
      datasource:
        master:
          url: jdbc:mysql://localhost:3306/db_master
          username: root
          password: 123456
          driver-class-name: com.mysql.cj.jdbc.Driver
        slave_1:
          url: jdbc:mysql://localhost:3307/db_slave
          username: root
          password: 123456
          driver-class-name: com.mysql.cj.jdbc.Driver
```

## 19.3 使用

```java
// Service 或 Mapper 上指定数据源
@Service
@DS("master")                    // 默认走主库
public class UserServiceImpl implements UserService {
    
    @Autowired
    private UserMapper userMapper;
    
    @DS("slave_1")               // 该方法走从库
    public List<User> list() {
        return userMapper.selectList(null);
    }
    
    @Transactional
    public void save(User user) {  // 默认走主库
        userMapper.insert(user);
    }
}
```


# 20. MyBatis-Plus 高级技巧（面试/实战）

## 20.1 Service 层 CRUD 封装

```java
// 继承 IService，直接获得更多封装好的 CRUD 方法
public interface UserService extends IService<User> {
    // 自定义业务方法
}

@Service
public class UserServiceImpl extends ServiceImpl<UserMapper, User> implements UserService {
    // 无需写基础 CRUD，ServiceImpl 已提供
    
    public List<User> getActiveUsers() {
        return lambdaQuery()                    // ServiceImpl 的快捷方法
            .eq(User::getStatus, 1)
            .orderByDesc(User::getCreateTime)
            .list();
    }
    
    public boolean batchSave(List<User> users) {
        return saveBatch(users, 1000);           // 批量插入，每批 1000 条
    }
    
    public User getOrFail(Long id) {
        return getById(id);                     // 如果不存在返回 null
    }
}
```

## 20.2 自定义 SQL + MyBatis-Plus 条件

```java
// Mapper 接口
@Mapper
public interface UserMapper extends BaseMapper<User> {
    // 自定义分页查询
    Page<UserVO> selectUserPage(Page<UserVO> page, @Param(Constants.WRAPPER) Wrapper<User> wrapper);
}

// XML 中：${ew.customSqlSegment} 直接拼接 Wrapper 条件
// <select id="selectUserPage" resultType="com.example.vo.UserVO">
//     SELECT u.*, o.order_count
//     FROM user u
//     LEFT JOIN (SELECT user_id, COUNT(*) order_count FROM `order` GROUP BY user_id) o
//         ON u.id = o.user_id
//     ${ew.customSqlSegment}
// </select>
```

## 20.3 类型处理器（TypeHandler）

```java
// 场景：JSON 字段自动序列化/反序列化
@TableName(value = "product", autoResultMap = true)
public class Product {
    private Long id;
    private String name;
    
    @TableField(typeHandler = JacksonTypeHandler.class)  // JSON 自动转换
    private List<String> tags;
}

// 依赖：mybatis-plus-extension 已内置 JacksonTypeHandler
// MySQL 字段类型：JSON
```

## 20.4 常见问题 FAQ

```java
// ❌ 问题1：updateById 更新 null 字段无效
// 解决方法：给实体字段设置值，MP 默认只更新非 null 字段
// 或使用 UpdateWrapper.set() 强制更新 null

// ❌ 问题2：分页查询不生效，返回数据不对
// 检查是否配置了 PaginationInnerInterceptor

// ❌ 问题3：逻辑删除后，唯一索引冲突
// 解决方法：唯一索引联合 deleted 字段，或改用唯一键+deleted 做唯一约束

// ❌ 问题4：@TableField(exist = false) 忽略实体中非数据库字段
@Data
public class User {
    @TableField(exist = false)      // 非数据库字段
    private String extraInfo;
}

// ✅ 总结：非数据库字段一定加 @TableField(exist = false) 注解
```


# 关联笔记

> [!info] 关联笔记
> - [[常用注解]] —— Spring 注解大全（@Transactional、JPA 持久化注解等）
> - [[java高级]] —— CompletableFuture 异步查询、Stream API
> - [[java基础]] —— ThreadLocal 连接管理、反射实现 ORM
> - [[java学习]] —— Java 学习索引
> - [[笔记规范]] —— 笔记格式规范（表格最左边添加一列等）
