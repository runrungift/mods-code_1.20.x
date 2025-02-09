# MODの書き出し

書き出しファイルの設定  
プロジェクトの`build.gradle`を編集 //行数  
```gradle
version = "1.20.2-48.1.0-1.0"
group = mod_group_id

base {
    archivesName = "CopperTools"
}
```
基本的に`archivesName`+`version`である。`mod_version`は`gradle.properties`の45行あたりからの情報が使用される。  
`Gradle`のリロード。`BUILD SUCCESSFUL`がでたら`Gradle-[MDKのバージョン等の名前]-Tasks-build-build`をダブルクリックで実行。  
buildされたファイルは`[MDKのバージョン等の名前]\build\libs`に保存される。  
保存された`jar`ファイルを実際に導入し、動作を確認する。

### 参考
* [【自作Modの作り方】『MODの書き出し』マイクラ1.20.2 (日本語解説) part.16【Minecraft Modding】](https://youtu.be/cWL8cTTRcp0?si=McrbJXxEULOwlYPp)