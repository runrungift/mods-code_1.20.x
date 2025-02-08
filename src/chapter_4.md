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