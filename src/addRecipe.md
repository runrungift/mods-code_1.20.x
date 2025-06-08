# レシピの追加

`resources/assets/coppertools/`にディレクトリを作成  
    `recipes`
`recipes`にファイルを作成  
    `copper_pickaxe.json`  

```json
{
  "type": "minecraft:crafting_shaped",
  "category": "equipment",
  "key": {
    "#": {
      "item": "minecraft:stick"
    },
    "X": {
      "item": "minecraft:copper_ingot"
    }
  },
  "pattern": [
    "XXX",
    " # ",
    " # "
  ],
  "result": {
    "item": "coppertools:copper_pickaxe"
  },
  "show_notification": true
}
```

各アイテムのレシピを登録する  
> [https://crafting.thedestruc7i0n.ca/](https://crafting.thedestruc7i0n.ca/)  
> このサイトを利用したり、既存のアイテムのレシピのファイルの中身を書き換えるなどで楽をする。  
ランチャーを起動して確認  

## 参考

- [Item -応用-](https://zenn.dev/boson/books/b83a4a1c0611d0/viewer/102dbc)
- [Crafting](https://crafting.thedestruc7i0n.ca/)
