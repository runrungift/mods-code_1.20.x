# はじめに
### 必要なもの
* IntelliJ IDEA Community Edition [site](https://www.jetbrains.com/ja-jp/idea/download/?section=windows)
* JDK [site](https://adoptium.net/temurin/)
* MDK [site](https://files.minecraftforge.net/net/minecraftforge/forge/index_1.20.2.html)

1. 必要なものをすべてダウンロード
2. 任意の場所に`mods`フォルダを作成
3. `MDK`を展開
4. `JDK`のインストーラーを実行
5. `Intellij IDEA`のインストーラーを実行
6. `IJ(Intellij IDEA)`を開きOPNEから展開したMDKを選択し、プロジェクトを開く
7. `BUILD SUCCESSFUL`が出るまで待機
8. 右のバーの像マークの`Gradle-[MDKのバージョン等の名前]-Tasks-forgegradle runs-genIntellijRuns`をダブルクリックで実行
9. `BUILD SUCCESSFUL`がでたら`Gradle`のリロード
10. 終わったら上の実行ボタンのとなりの実行構成の編集
11. `アプリケーション-runClient-ビルドと実行`のJDKをインストールしたJDKに変更
    > Default Pathは`C:\Program Files\Eclipse Adoptium`
12. `ok-実行`
13. ランチャーの起動後、`Mod`から`Example Mod`があることを確認
14. 確認後終了