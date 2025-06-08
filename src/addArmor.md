# 装備の追加

パッケージの追加`com.Light.CopperTools.item.armor`  
`armor`に装備素材の設定のクラスを作成  
    `ModArmorMaterial`

```java
package com.Light.CopperTools.item.armor;

import com.Light.CopperTools.main.CopperTools;
import net.minecraft.Util;
import net.minecraft.sounds.SoundEvent;
import net.minecraft.util.LazyLoadedValue;
import net.minecraft.world.item.ArmorItem;
import net.minecraft.world.item.ArmorMaterial;
import net.minecraft.world.item.crafting.Ingredient;

import java.util.EnumMap;
import java.util.function.Supplier;

public class ModArmorMaterial implements ArmorMaterial {

    private final String id;
    private final int durabilityMultiplier;
    private final EnumMap<ArmorItem.Type, Integer> protectionFunctionForType;
    private final int enchantmentValue;
    private final SoundEvent sound;
    private final float toughness;
    private final float knockbackResistance;
    private final LazyLoadedValue<Ingredient> repairIngredient;

    private static final EnumMap<ArmorItem.Type, Integer> HEALTH_FUNCTION_FOR_TYPE = Util.make(new EnumMap<>(ArmorItem.Type.class), (map) -> {
        map.put(ArmorItem.Type.HELMET, 11);
        map.put(ArmorItem.Type.CHESTPLATE, 16);
        map.put(ArmorItem.Type.LEGGINGS, 15);
        map.put(ArmorItem.Type.BOOTS, 13);
    });

    public ModArmorMaterial(String id, int durabilityMultiplier, EnumMap<ArmorItem.Type, Integer> protectionFunctionForType, int enchantmentValue, SoundEvent sound, float toughness, float knockbackResistance, Supplier<Ingredient> ingredient) {
        this.id = CopperTools.MOD_ID + ":" + id;
        this.durabilityMultiplier = durabilityMultiplier;
        this.protectionFunctionForType = protectionFunctionForType;
        this.enchantmentValue = enchantmentValue;
        this.sound = sound;
        this.toughness = toughness;
        this.knockbackResistance = knockbackResistance;
        this.repairIngredient = new LazyLoadedValue<>(ingredient);
    }

    @Override
    public int getDurabilityForType(ArmorItem.Type type) {
        return 0;
    }

    @Override
    public int getDefenseForType(ArmorItem.Type type) {
        return 0;
    }

    @Override
    public int getEnchantmentValue() {
        return 0;
    }

    @Override
    public SoundEvent getEquipSound() {
        return null;
    }

    @Override
    public Ingredient getRepairIngredient() {
        return null;
    }

    @Override
    public String getName() {
        return "";
    }

    @Override
    public float getToughness() {
        return 0;
    }

    @Override
    public float getKnockbackResistance() {
        return 0;
    }
}
```

`ArmorMaterial`を登録する  
`armor`に登録するクラスを作成  
    `CopperArmorMaterials`

```java
package com.Light.CopperTools.item.armor;

import net.minecraft.Util;
import net.minecraft.sounds.SoundEvents;
import net.minecraft.world.item.ArmorItem;
import net.minecraft.world.item.Items;
import net.minecraft.world.item.crafting.Ingredient;

import java.util.EnumMap;

public class CopperArmorMaterials {
    public static final ModArmorMaterial COPPER = new ModArmorMaterial(
            "copper",
            12,
            Util.make(new EnumMap<>(ArmorItem.Type.class),
                    (type)->{
                type.put(ArmorItem.Type.HELMET,2);
                type.put(ArmorItem.Type.CHESTPLATE,6);
                type.put(ArmorItem.Type.LEGGINGS,5);
                type.put(ArmorItem.Type.BOOTS,2);

                    }),
            5,
            SoundEvents.ARMOR_EQUIP_IRON,
            0.0F,
            0.0F,
            ()->{return Ingredient.of(Items.COPPER_BLOCK);}
            );
}
```

`armor`にhelmetのクラスを作成
    `ArmorCopperHelmet`

```java
package com.Light.CopperTools.item.armor;

import net.minecraft.world.item.ArmorItem;

public class ArmorCopperHelmet extends ArmorItem {
    public ArmorCopperHelmet() {
        super(CopperArmorMaterials.COPPER,Type.HELMET,new Properties());
    }
}
```

チェストプレート、レギンス、ブーツも同じように設定する。  
アイテムとして登録、クリエイティブモードタブにも登録。アイテムの画像、アイテム名も同じように設定。  
`resources/assets/coppertools/textures`にディレクトリを作成  
    `models/item`  
`item`に装備の画像を保存  
    `copper_layer_1.png`、`copper_layer_2.png`  
装備の装着音の字幕を整えるために`ja_jp.json`を編集する。  
`resources/assets/minecraft/lang`にディレクトリを作成  
`lang`にファイルを作成  
    `ja_jp.json`  

```json
{
  "subtitles.item.armor.equip_chain": "防具が装着される",
  "subtitles.item.armor.equip_diamond": "防具が装着される",
  "subtitles.item.armor.equip_gold": "防具が装着される",
  "subtitles.item.armor.equip_iron": "防具が装着される",
  "subtitles.item.armor.equip_leather": "防具が装着される",
  "subtitles.item.armor.equip_netherite": "防具が装着される"
}
```

防具の装飾を可能にするために防具をtagに追加する。  
`resources/data/minecraft/tags/items/trimmable_armor.json`を作成。  

```json
{
  "values": [
    "coppertools:copper_helmet",
    "coppertools:copper_chestplate",
    "coppertools:copper_leggings",
    "coppertools:copper_boots"
  ]
}
```

ランチャーを起動して確認  

## 参考

- [【自作Modの作り方】『アーマーの追加①』マイクラ1.20.2 (日本語解説) part.31【Minecraft Modding】](https://youtu.be/1--cnvRJkkY?si=v-ia8nF0gtkGgF9R)
- [【自作Modの作り方】『アーマーの追加②』マイクラ1.20.2 (日本語解説) part.32【Minecraft Modding】](https://youtu.be/rTB3nvH2Qz4?si=jul943ZMV_-Eqliu)
