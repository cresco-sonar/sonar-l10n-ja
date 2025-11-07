# SonarQube 日本語翻訳パック リリースガイド

[English](https://github.com/cresco-sonar/sonar-l10n-ja/blob/master/RELEASE_GUIDE_ja.md)

このドキュメントでは、SonarQube 日本語翻訳パック（sonar-l10n-ja）のリリース手順について説明します。

## 1. 前提条件

- Git がインストール済みであること
- Maven がインストール済みであること
- GitHub リポジトリの書き込み権限があること

## 2. リリース前の準備

### 2.1. コードの確認

リリースする前に、以下の内容を確認してください：

- 翻訳内容の確認
- テストが正常に通過すること
- `pom.xml` のバージョン番号が適切であること（例：`1.1-SNAPSHOT`）　<!-- TODO なおす-->

### 2.2. ビルドのテスト

リリース処理を開始する前に、正常にビルドできることを確認します：

```bash
mvn clean package
```

このコマンドが成功すると、`target/sonar-l10n-ja-plugin-1.1-SNAPSHOT.jar` というプラグインファイルが生成されます。

## 3. リリースの実行

### 3.1. Maven リリースの実行

以下のコマンドでリリース処理を実行します：

```bash
mvn release:prepare release:perform
```

このコマンドは以下のことを行います：

1. バージョン番号から `-SNAPSHOT` サフィックスを削除する（例：`1.1-SNAPSHOT` → `1.1`）
2. リリースタグを作成する（例：`sonar-l10n-ja-plugin-1.1`）
3. コミットしてタグをリポジトリにプッシュする
4. 次の開発バージョンのバージョン番号を設定する（例：`1.2-SNAPSHOT`）
5. リリースビルドを実行する
6. 成果物を `target/checkout/target/releases` に生成する

### 3.2. 生成された JAR ファイルの確認

リリース処理が成功したら、以下のファイルを確認できます：

- `target/sonar-l10n-ja-plugin-1.1.jar`（リリースバージョンの JAR）

## 4. GitHub リリースの作成

### 4.1. GitHub リリースページへの移動

1. ブラウザで GitHub のリポジトリページを開きます：https://github.com/cresco-sonar/sonar-l10n-ja
2. 「Releases」セクションに移動します（リポジトリページの右側）
3. 「Draft a new release」または「Create a new release」ボタンをクリックします

### 4.2. リリース情報の入力

1. 「Choose a tag」で、Maven リリース時に作成したタグを選択します（例：`sonar-l10n-ja-plugin-1.1`）
2. リリースタイトルを入力します（例：「Japanese Localization Pack v1.1」）
3. リリースノートを記述します（変更内容や改善点など）

### 4.3. JAR ファイルの添付

1. ビルドで生成された JAR ファイル（`target/sonar-l10n-ja-plugin-1.1.jar`）をドラッグ＆ドロップまたは「Attach binaries」ボタンからアップロードします
2. チェックサムファイルは通常不要ですが、必要に応じて添付することもできます

### 4.4. リリースの公開

入力内容を確認し、「Publish release」ボタンをクリックしてリリースを公開します。

## 5. リリース後の作業

### 5.1. SonarQube への投稿（オプション）

SonarQube マーケットプレイスに登録するには、SonarSource チームに連絡する必要があります。

### 5.2. リリース情報の確認

リリース後、以下の点を確認してください：

- GitHub のリリースページに JAR ファイルが正常に添付されていること
- ダウンロードリンクが機能すること
- 次の開発バージョンの準備ができていること

---

## 参考コマンド

### シンプルなビルド（テスト目的）

```bash
mvn clean package
```
