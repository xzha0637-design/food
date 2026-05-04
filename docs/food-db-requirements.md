# 食物评分数据库需求

## 任务 A：food_db.json — 综合评分数据库

来源：`C:/Users/15460/OneDrive/Desktop/food/10_Weighted_Food_Scoring_v2.txt`

将 ~150 条食物评分记录转为 JSON 数组，每条格式：

```json
{
  "name": "中文名称",
  "aliases": ["别名1", "别名2"],
  "score": 整数(1-100),
  "category": "分类",
  "nova": "G1/G2/G3/G4",
  "level": "鼓励食用/适量食用/尽量少吃"
}
```

### 要求

- `name` 用中文，如"白米饭"、"鸡胸肉(烤去皮)"
- `aliases` 至少包含 2-3 个常见叫法，如白米饭的别名：["米饭", "蒸米饭", "大米饭"]
- `score` 是文件中 `=> XX` 后的整数（加权综合分），不是 FC2 分
- `category` 从归类中提取：浆果、柑橘、一般水果、绿叶蔬菜、十字花科、豆类、坚果、全谷物、精制谷物、禽肉、红肉、加工肉、鱼类、贝类、蛋类、牛奶、酸奶、奶酪、植物油、动物脂肪、饮料、植物基、零食、酱汁
- 凡标注"估算"的食物保留，标注"[高糖]"等备注可忽略

### 评分优先用加权综合分

文件中每行的 `=> XX` 即为加权综合分。例如：
- `蓝莓 => 100` → score: 100
- `白米饭 => 34` → score: 34

## 任务 B：nutrients.json — 营养素数据库

新建文件，覆盖 ~250 种常见食物（包括 food_db.json 中所有食物的营养素 + 更多中国常见食物）。

每条格式：

```json
{
  "name": "食物名称",
  "per100g": {
    "kcal": 热量(kcal),
    "protein": 蛋白质(g),
    "carbs": 碳水化合物(g),
    "fat": 脂肪(g),
    "fiber": 膳食纤维(g),
    "sodium": 钠(mg)
  }
}
```

### 要求

- 食物名称与 food_db.json 保持一致，确保能匹配
- 覆盖范围：常见蔬菜水果、肉禽鱼蛋、主食、豆制品、奶制品、调味品、常见中式菜肴
- 数据来源参考"中国食物成分表"或可信公开数据
- 数值精确到小数点后 1 位
- 没有确切数据的食物不要猜测，标注 `null` 留空

### 常见食物示例

```
白米饭: kcal=116, protein=2.6, carbs=25.9, fat=0.3, fiber=0.3, sodium=3
鸡胸肉(去皮): kcal=133, protein=31.0, carbs=0.0, fat=1.5, fiber=0, sodium=45
番茄: kcal=18, protein=0.9, carbs=3.9, fat=0.2, fiber=1.2, sodium=5
鸡蛋(整): kcal=144, protein=13.3, carbs=2.8, fat=8.8, fiber=0, sodium=130
```

---

## 交付

两个文件放到 `C:/Users/15460/OneDrive/Desktop/food/`：
- `food_db.json`
- `nutrients.json`

完成后告知即可。
