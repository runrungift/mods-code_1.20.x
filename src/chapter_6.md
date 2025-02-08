# 装備の追加

パッケージの追加`com.Light.CopperTools.item.armor`  
`armor`にhelmetのクラスを作成
    `ArmorCopperHelmet`
```java
package com.Light.CopperTools.item.armor;

import net.minecraft.world.item.ArmorItem;
import net.minecraft.world.item.ArmorMaterial;
import net.minecraft.world.item.ArmorMaterials;

public class ArmorCopperHelmet extends ArmorItem {
    public ArmorCopperHelmet() {
        super(ArmorMaterials.IRON,Type.HELMET,new Properties().durability(200));
    }
}
```
チェストプレート、レギンス、ブーツも同じように設定する。  
アイテムとして登録、クリエイティブモードタブにも登録。アイテムの画像、アイテム名も同じように設定。  
`resources/assets/coppertools/textures`にディレクトリを作成  
    `models\item`  
`item`に装備の画像を保存  
    `copper_layer_1.png`、`copper_layer_2.png`  
ランチャーを起動して確認 