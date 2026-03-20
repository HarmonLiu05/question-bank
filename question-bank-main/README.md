# question-bank

轻量版云端题库仓库。

## 文件说明

- `educoder.json`: Educoder 分类题库
- `zhihuishu.json`: 智慧树分类题库
- `leetcode.json`: LeetCode 分类题库
- `general.json`: 通用分类题库

## 数据格式

```json
{
  "version": 1,
  "name": "zhihuishu",
  "questions": [
    {
      "stem": "题干 + 选项",
      "answer": "B",
      "source": "zhihuishu.com"
    }
  ]
}
```

目前插件同步时会按分类读取对应的 `*.json` 文件。
