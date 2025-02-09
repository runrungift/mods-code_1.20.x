# Itemの追加

パッケージの追加`com.Light.CopperTools.item`  
`item`にitemのクラスを作成
    `ItemCopperNugget`
```java
package com.Light.CopperTools.item;

import net.minecraft.world.item.Item;
import net.minecraft.world.item.Rarity;

public class ItemCopperNugget extends Item {
    public ItemCopperNugget() {
        super(new Properties()
                .stacksTo(64)
                .rarity(Rarity.COMMON)
        );
    }
}
```
`regi`にitemを登録するクラスを作成する  
    `CopperToolsItems`
```java
package com.Light.CopperTools.regi;

import com.Light.CopperTools.item.ItemCopperNugget;
import com.Light.CopperTools.main.CopperTools;
import net.minecraft.world.item.Item;
import net.minecraftforge.registries.DeferredRegister;
import net.minecraftforge.registries.ForgeRegistries;
import net.minecraftforge.registries.RegistryObject;

public class CopperToolsItems {
    public static final DeferredRegister<Item> ITEMS = DeferredRegister.create(ForgeRegistries.ITEMS, CopperTools.MOD_ID);
    public static final RegistryObject<Item> COPPER_NUGGET = ITEMS.register("copper_nugget", ItemCopperNugget::new);
}
```
`CopperTools.java`にItemを登録
```java
    public CopperTools(){
        IEventBus bus = FMLJavaModLoadingContext.get().getModEventBus();
        CopperToolsItems.ITEMS.register(bus);
        CopperToolsTabs.MOD_TABS.register(bus);
    }
```
Itemをクリエイティブモードタブに追加  
`CopperToolsMain.java`
```java
    public static final Item[] items = {
            CopperToolsItems.COPPER_NUGGET.get()
    };
```
クリエイティブモードタブのアイコンを変更  
`CopperToolsTabs.java`
```java
                    .icon(()->new ItemStack(CopperToolsItems.COPPER_NUGGET.get()))
```
ランチャーを起動してクリエイティブモードタブが登録されているか確認  

Itemのテクスチャーを設定  
注意事項
* 16の倍数の正方形(16px*16pxなど)
* png形式(PNGファイル)
* 余白がアルファチャンネルになっていること
* ファイルの名前がitemIDと同じであること

`resources/assets/coppertools/`にディレクトリを作成  
    `textures\item`
`item`にアイテムの画像を保存  
`resources/assets/coppertools/`にディレクトリを作成  
    `models\item`
`item`にファイルを作成  
    `copper_nugget.json`
```json
{
  "parent": "minecraft:item/generated",
  "textures": {
    "layer0": "coppertools:item/copper_nugget"
  }
}
```

Itemの名前を設定  
`ja_jp.json`を編集
```json
{
  "itemGroup.coppertools_main" : "CopperTools",

  "item.coppertools.copper_nugget" : "銅塊"
}
```
ランチャーを起動して確認  

### 参考
* [【自作Modの作り方】『アイテムの追加①』マイクラ1.20.1 (日本語解説) part.4【Minecraft Modding】](https://youtu.be/F0Mf8GX4eGY?si=hNwL5vOyRmOM7od-)
* [【自作Modの作り方】『アイテムの追加②』マイクラ1.20.1 (日本語解説) part.5【Minecraft Modding】](https://youtu.be/QUrFbDntnjU?si=SqzT_WoSnjdmrwvM)