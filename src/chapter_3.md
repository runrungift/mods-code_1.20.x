# クリエイティブモードタブの追加

パッケージの追加`com.Light.CopperTools.regi.tab`  
`tab`にタブのmainクラスを作成(tabの中身を管理をする)  
    `CopperToolsMain`
```java
package com.Light.CopperTools.regi.tab;

import net.minecraft.world.item.Item;
import net.minecraft.world.item.ItemStack;
import net.minecraft.world.item.Items;

public class CopperToolsMain {
    public static final Item[] items = {
            Items.WATER_BUCKET,
            Items.LAVA_BUCKET
    };
}
```

`tab`にタブのmainクラスを作成(tabを登録する)  
    `CopperToolsTabs`
```java
package com.Light.CopperTools.regi.tab;

import com.Light.CopperTools.main.CopperTools;
import net.minecraft.core.registries.Registries;
import net.minecraft.network.chat.Component;
import net.minecraft.world.item.CreativeModeTab;
import net.minecraft.world.item.Item;
import net.minecraft.world.item.ItemStack;
import net.minecraft.world.item.Items;
import net.minecraftforge.registries.DeferredRegister;
import net.minecraftforge.registries.RegistryObject;

public class CopperToolsTabs {
    public static final DeferredRegister<CreativeModeTab> MOD_TABS = DeferredRegister.create(Registries.CREATIVE_MODE_TAB, CopperTools.MOD_ID);

    public static final RegistryObject<CreativeModeTab> COPPERTOOLS_MAIN = MOD_TABS.register("coppertools_main",
            ()->{return CreativeModeTab.builder()
                    .icon(()->new ItemStack(Items.WATER_BUCKET))
                    .title(Component.translatable("itemGroup.coppertools_main"))
                    .displayItems((param,output)->{
                        for (Item item:CopperToolsMain.items){
                            output.accept(item);
                        }
                    })
                    .build();
    });
}
```
`resources`にディレクトリを作成  
    `assets/coppertools/lang`  
`lang`にファイルを作成  
    `ja_jp.json`
```json
{
  "itemGroup.coppertools_main" : "CopperTools"
}
```
`CopperTools.java`にクリエイティブモードタブを登録  
```java
    public CopperTools(){
        IEventBus bus = FMLJavaModLoadingContext.get().getModEventBus();
        CopperToolsTabs.MOD_TABS.register(bus);
    }
```
ランチャーを起動してクリエイティブモードタブが登録されているか確認  

### 参考
* [【自作Modの作り方】『クリエイティブタブの追加』マイクラ1.20.1 (日本語解説) part.3【Minecraft Modding】](https://youtu.be/6aAdOeLv5bM?si=-OcJbyqaOJuwij_H)