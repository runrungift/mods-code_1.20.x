# ピッケルの追加

パッケージの追加`com.Light.CopperTools.item.tool`  
`tool`にピッケルのクラスを作成  
    `ToolCopperPickaxe`

```java
package com.Light.CopperTools.item.tool;

import net.minecraft.world.item.PickaxeItem;
import net.minecraft.world.item.Tier;
import net.minecraft.world.item.Tiers;

public class ToolCopperPickaxe extends PickaxeItem {
    public ToolCopperPickaxe() {
        super(Tiers.IRON,1,-2.8F,new Properties().durability(200));
    }
}
```

`CopperToolsItems.java`にピッケルを登録  

```java
    public CopperTools(){
        IEventBus bus = FMLJavaModLoadingContext.get().getModEventBus();
        CopperToolsItems.ITEMS.register(bus);
        CopperToolsTabs.MOD_TABS.register(bus);
    }
```

ピッケルをクリエイティブモードタブに追加  
`CopperToolsMain.java`

```java
    public static final Item[] items = {
            CopperToolsItems.COPPER_NUGGET.get(),
            CopperToolsItems.COPPER_PICKAXE.get()
    };
```

クリエイティブモードタブのアイコンを変更  
`CopperToolsTabs.java`

```java
                    .icon(()->new ItemStack(CopperToolsItems.COPPER_NUGGET.get()))
```

ピッケルのテクスチャーを設定  
`textures/item`  
`item`にピッケルの画像を保存  
`models/item`  
`item`にファイルを作成  
    `copper_pickaxe.json`

```json
{
  "parent": "minecraft:item/handheld",
  "textures": {
    "layer0": "coppertools:item/copper_pickaxe"
  }
}
```

Itemの名前を設定  
`ja_jp.json`を編集

```json
{
  "item.coppertools.copper_nugget" : "銅塊",
  "item.coppertools.copper_pickaxe" : "銅のツルハシ"
}
```

ランチャーを起動して確認  

## 参考

- [【自作Modの作り方】『ツルハシの追加|ツールの追加②』マイクラ1.20.2 (日本語解説) part.12【Minecraft Modding】](https://youtu.be/Vf96HV-EAk8?si=kzdKkeffCN3qAE84)
