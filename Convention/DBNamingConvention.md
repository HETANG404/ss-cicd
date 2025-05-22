## 🧱 SQL 数据库命名（如 MySQL / PostgreSQL）

### ✅ 推荐命名风格：**snake\_case + 小写 + 复数表名**

| 类型  | 命名风格            | 示例                      |
| --- | --------------- | ----------------------- |
| 表名  | `snake_case`、复数 | `users`, `order_items`  |
| 字段名 | `snake_case`、单数 | `user_id`, `created_at` |

#### 📌 说明：

* 表名通常使用 **复数名词**（因为代表“多个记录”）

  * ✅ `products`，❌ `product`
* 字段名使用 **单数名词**，带上下文前缀

  * ✅ `user_id`, ~~`order_total`~~

*当下理解：为了在中间表中或引用中区分不同不同表中的同名字段，因此只有id带前缀就可以*

#### ✅ 表 + 字段 示例：

```sql
CREATE TABLE order_items (
  id SERIAL PRIMARY KEY,
  order_id INT,
  product_id INT,
  quantity INT,
  created_at TIMESTAMP
);
```

---

## 🍃 MongoDB 命名（NoSQL）

### ✅ 推荐命名风格：**集合名用 snake\_case 或 camelCase，字段用 camelCase**

| 类型  | 命名风格                       | 示例                                  |
| --- | -------------------------- | ----------------------------------- |
| 集合名 | `snake_case` 或 `camelCase` | `userProfiles` 或 `user_profiles`    |
| 字段名 | `camelCase`（更 JS 友好）       | `createdAt`, `userId`, `orderTotal` |

#### 📌 说明：

* 集合名没有大小写限制，但建议 **统一风格**，避免混用
* 字段名建议用 `camelCase`，因为多数 MongoDB 项目由 JS/Node.js 驱动

#### ✅ MongoDB 文档示例：

```json
{
  "_id": ObjectId("..."),
  "userId": "abc123",
  "createdAt": "2025-05-22T08:00:00Z",
  "items": [
    { "productId": "xyz789", "quantity": 2 }
  ]
}
```

---

## 📊 命名方式对比总结

| 类型    | SQL 推荐            | MongoDB 推荐                 |
| ----- | ----------------- | -------------------------- |
| 表/集合名 | `snake_case` + 复数 | `snake_case` 或 `camelCase` |
| 字段名   | `snake_case` + 单数 | `camelCase`                |
| 主键    | `id`, `user_id`   | `_id`（MongoDB默认字段）         |
| 时间字段  | `created_at`      | `createdAt`                |

---

## 🚨 小贴士：避免这些错误命名方式

* ❌ `getUsers`, `tbl_user` → 太冗余、带行为或前缀
* ❌ `UserProfiles`（大写驼峰）→ 不符合 SQL 规范
* ❌ `order-date`（带短横线）→ SQL 和 MongoDB 都不允许
