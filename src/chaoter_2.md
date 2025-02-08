# MODの説明欄とファイルの基本設定

`IJ`

プロジェクトの不要ファイルを全て削除
    `changelog.txt`、`CREDITS.txt`、`LiCENSE.txt`、`README.txt`、`src/main/java/com/example`(txtファイルとexampleフォルダを削除)
`com`に新しいパッケージを作成
    `com.Light.CopperTools.main`
`main`にmainクラスを作成する
    `CopperTools`
```java
package com.Light.CopperTools.main;

import net.minecraftforge.fml.common.Mod;

@Mod("coppertools")
//@Mod("半角英字のみ")

public class CopperTools {
    // MOD_IDの定義
    public static final String MOD_ID = "coppertools";

    public CopperTools(){
        
    }
}
```
`resources/META-INF/mods.toml`を編集 #行数
```toml
modId="coppertools" #18
version="1.20.2-1.0" #20
displayName="CopperTools" #22
authors="Light" #32
description='''add cooper tools'''　#42
[[dependencies.coppertools]] #44
[[dependencies.coppertools]] #58
```
ランチャーを起動して情報が登録されているか確認