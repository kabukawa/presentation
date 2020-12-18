---
title: "現場で使うVS Code"
theme : "white"
---

# 現場で使うVS Code

2020年12月18日(金)

![](img/VisualStudioCode.png)

---

## 今日話すこと

* 拡張機能については話しません。 {.fragment .fade-right}
* Windows環境を想定してます。 {.fragment .fade-right}
* 特定範囲の人にとってはあるあるだと思います。 {.fragment .fade-right}

---

## 自己紹介

![](img/slide-summary.png)

---

## VS Code使ってますか

* 拡張機能便利ですよね {.fragment .fade-right}
* 様々な機能が追加できて、色々な目的で使える {.fragment .fade-right}
* 単なるエディタというより環境 {.fragment .fade-right}
* ナウい {.fragment .fade-right}

![](img/now.png) {.fragment .fade-right}

---

## だがしかし

* 客先で開発をしていると、VS Code入れられない場合もある {.fragment .fade-right}
* 拡張機能を入れられない場合もある {.fragment .fade-right}
    * 勝手にインストール禁止 {.fragment .fade-right}
    * そもそもネットに繋がってない {.fragment .fade-right}

![](img/dame.jpg) {.fragment .fade-right}

---

## VS Codeの無い世界

* せめて、VS Codeだけでも入れたいんじゃ！ {.fragment .fade-right}
* 拡張機能は、、、入れたいけど無理。 {.fragment .fade-right}
* バージョン管理のために git も入れたいんじゃ！ {.fragment .fade-right}

![](img/beam.jpg) {.fragment .fade-right}

---

## 現場で説得

* お金かかりません。エディタです。 {.fragment .fade-right}
    * マイクロソフト製なの？じゃぁいっか。 {.fragment .fade-right}
* Gitも必要なんっすよね。 {.fragment .fade-right}
    * VS Code入れるとgitも必要になるので。 {.fragment .fade-right}

![](img/okusuri.jpg) {.fragment .fade-right}

---

## 拡張を入れなくてもできること

* ファイルの新規作成/更新/削除/名前変更など  {.fragment .fade-right}
* Gitによるバージョン管理(要gitコマンド) {.fragment .fade-right}
* 高機能な編集機能(マルチカーソル等も使える) {.fragment .fade-right}
* 画面分割、タブ切り替えによる複数ファイル編集 {.fragment .fade-right}
* ファイル内検索/grep {.fragment .fade-right}
* 統合ターミナル {.fragment .fade-right}
* Markdownのプレビュー {.fragment .fade-right}
* Javascriptのデバッグ {.fragment .fade-right}

などなど {.fragment .fade-right}

---

## あれ？

結構素のVS Codeでも色々できるじゃん。 {.fragment .fade-right}

* 色々不自由のある現場でも活かせる {.fragment .fade-right}
* 単純に便利 {.fragment .fade-right}
* これって最高では？ {.fragment .fade-right}

![](img/yoshi.jpg) {.fragment .fade-right}

---

## 実際に使っている設定

デフォルトから設定を変えているものを紹介。 {.fragment .fade-right}

* [設定] 画面の開き方 {.fragment .fade-right}
    * Ctrl + ,のショートカット {.fragment .fade-right}
    * File > Preferences > Settings {.fragment .fade-right}
    * サイドメニューの歯車アイコンから「設定」を選択 {.fragment .fade-right}

---

### 文字コード自動判定

* VS Codeのデフォルトは utf-8。 {.fragment .fade-right}
* だけどWindowsではShift-JISのファイルもあるので文字化けせずに編集したい。 {.fragment .fade-right}

1. 検索欄に files.autoGuessEncoding  を打ち込み、チェックボックスを ON にする。 {.fragment .fade-right}
2. もしくはsettings.jsonで以下の項目を記述する。 {.fragment .fade-right}

```json {.fragment .fade-right}
"files.autoGuessEncoding": true,
```

---

### 自動判定だけど

* うまく判定できないこともある。 {.fragment .fade-right}
* JIS(iso-2022-jp)は変換できない。 {.fragment .fade-right}
    * 今どきJISのファイルなんて無いでしょ？
    (いや、有るんですよ。。。) {.fragment .fade-right}
    * GitBashに付属のvimで！(本末転倒) {.fragment .fade-right}
    * GitBashに付属のiconv(だ～か～ら～)  {.fragment .fade-right}
 
![](img/dousite.jpg) {.fragment .fade-right}

---

### 改行コード

* サーバーとのやり取りもあるので、改行コードは LF に。 {.fragment .fade-right}

1. 検索欄に files.eol を打ち込み、ドロップダウンリストで "\n" を選択してデフォルトの改行コードをLFに変更する。 {.fragment .fade-right}
2. もしくはsettings.jsonで以下の項目を記述する。 {.fragment .fade-right}

```json {.fragment .fade-right}
"files.eol": "\n",
```

---

### 別に改行コードは変えなくても

* サーバーにファイルを持っていったときに ^M を見たくない。 {.fragment .fade-right}
* 今どき、メモ帳でも 改行コード LF のファイルを扱える。 {.fragment .fade-right}
* だったらどっちかに統一したほうが安心。 {.fragment .fade-right}

![](img/ha.jpg) {.fragment .fade-right}

---

### 統合シェル

* VS Codeの統合ターミナルをGitBashに。 {.fragment .fade-right}

* 検索欄に terminal.integrated.shell.windows を打ち込み、settings.jsonで編集 で編集画面表示。以下の内容を記述する。 {.fragment .fade-right}

```json {.fragment .fade-right}
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
```

---

### PowerShellじゃないの？

* Git for Windowsをインストールすると一緒に入る。 {.fragment .fade-right}
* WSLが使えない32bit Windows環境でbash使いたいなら {.fragment .fade-right}
* WSL環境と設定ファイルを共用できる(俺得) {.fragment .fade-right}
* 俺はbashが使いたい。 {.fragment .fade-right}

![](img/hansei.jpg) {.fragment .fade-right}

---

## コマンドライン

[コマンドライン起動オプション](https://code.visualstudio.com/docs/getstarted/tips-and-tricks#_command-line) {.fragment .fade-right}

* 現在のディレクトリでコードを開く {.fragment .fade-right}

``` {.fragment .fade-right}
code .
```

* 特定の行と列でファイルを開く file：line [：character] {.fragment .fade-right}

``` {.fragment .fade-right}
code --goto package.json:10:5
```

---

### 差分

* 差分エディタを開く {.fragment .fade-right}

``` {.fragment .fade-right}
code --diff <file1> <file2>
```

* .gitconfigに登録して、gitコマンドのdiffのときにVS Codeを使う。 {.fragment .fade-right}

```ini {.fragment .fade-right}
[diff]
    tool = vscode
[difftool "vscode"]
    cmd = code --wait --diff $LOCAL $REMOTE
```

---

### リセット

* すべての拡張機能を無効にして起動 {.fragment .fade-right}

``` {.fragment .fade-right}
code --disable-extensions .
```

* 設定などを全て削除 {.fragment .fade-right}
    1. %APPDATA%\Code を削除 {.fragment .fade-right}
    2. %HOMEDRIVE%%HOMEPATH%.vscode を削除 {.fragment .fade-right}

---

## まとめ

* VS Code、拡張機能が無くても結構できる子
* GitBashと組み合わせるとWSLが無くてもそれなりに使える。
* VS Codeを導入することで、少しでも現場の開発が楽しくなると良いですね。

![](img/yoshi.jpg) {.fragment .fade-right}

---

## 謝辞

* 本日の発表資料は [vscode-reveal](https://marketplace.visualstudio.com/items?itemName=evilz.vscode-reveal) で作成しました。
* 現場猫画像は からあげのるつぼ(@karaage_rutsubo)さんのツイートから拝借しました。
* わたしの使っている拡張機能などについては [この辺](https://github.com/kabukawa/settings/blob/master/README_ja.md) に書いてあります。