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

## 转换脚本

仓库内提供了一个可复用的转换脚本，用于把智拓导出的题库 JSON 转成当前仓库使用的数据格式。

最常用的命令：

```bash
python convert_zhituo_to_zhihuishu.py -i zhituo-question-bank-2026-03-20.json -o zhihuishu.json
```

也可以自定义输出的 `name` 字段：

```bash
python convert_zhituo_to_zhihuishu.py -i input.json -o output.json --name zhihuishu
```

脚本规则：

- 从输入文件顶层的 `questionBank` 读取题目
- `stem` 优先使用 `statementPreview`，为空时回退到 `title`
- `answer` 直接使用原题答案
- `source` 优先使用原题 `source`，缺失时回退为 `local`
- 保留 `choice` 和 `code` 两类题目
- 跳过空答案题目
- 按 `stem + answer` 去重，保留首次出现的记录

脚本执行后会输出统计信息，包括源题数量、跳过的空答案数量、去重后的题目数量和输出文件路径。
