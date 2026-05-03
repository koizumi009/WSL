# WSLの各種手順を日本語でまとめる
Windows 上で Linux 環境を構築する WSL2 の導入手順と、軽量ターミナル wsltty のセットアップ方法をまとめたガイドです。

---

# WSL2 インストール & wsltty セットアップガイド

Windows上でLinux環境を構築するWSL2のインストール手順と、軽量・高速なターミナル「wsltty」の導入手順をまとめたガイドです。

---

## 1. Windowsの機能の有効化

WSL2を動作させるために必要なシステム機能を有効化します。

1.  **[コントロール パネル]** > **[プログラム]** > **[Windows の機能の有効化または無効化]** を開きます。
2.  以下の2つの項目にチェックを入れます：
    * [x] **Linux 用 Windows サブシステム**
    * [x] **仮想マシン プラットフォーム**
3.  **[OK]** をクリックし、指示に従って **Windowsを再起動** してください。

> [!IMPORTANT]
> この設定を行わないと、WSLのインストール時にエラーが発生します。

---

## 2. WSL2 のインストール

再起動後、標準的なディストリビューション（Ubuntu）をインストールします。

1.  **PowerShell** を管理者権限で開きます。
2.  以下のコマンドを実行します：
    ```powershell
    wsl --install
    ```
3.  インストール完了後、Ubuntuのウィンドウが自動で立ち上がります。
4.  指示に従って **UNIXユーザー名** と **パスワード** を設定してください。

---

## 3. wsltty のダウンロードとインストール

標準コンソールよりも使い勝手の良いターミナル **wsltty** を導入します。

### ダウンロード
1.  [wsltty リリースページ](https://github.com/mintty/wsltty/releases) へアクセスします。
2.  最新バージョンの `wsltty-x.x.x-install.exe` をダウンロードします。

### インストール
1.  ダウンロードしたインストーラーを実行します。
2.  すべてデフォルト設定のまま進めて完了させます。
3.  インストール後、スタートメニューに **WSL Terminal** (または Ubuntu Terminal) が追加されます。

---

## 4. wsltty のおすすめ設定

wslttyを起動し、画面上を右クリック > **[Options...]** から設定を変更できます。

| 項目 | 設定内容 |
| :--- | :--- |
| **Look -> Cursor** | カーソルの形や点滅を好みで変更 |
| **Text -> Font** | `MS Gothic` や `Cascadia Code` 等の日本語対応フォント推奨 |
| **Window -> Transparency** | `Medium` 程度にすると背景が透過してモダンになります |

---

## 5. トラブルシューティング

* **エラー `0x80370102` などが出る場合**:
    * PCのBIOS/UEFI設定で **Virtualization Technology (VTx / AMD-V)** が `Enabled` になっているか確認してください。
* **WSLのバージョン確認**:
    * PowerShellで `wsl -l -v` を実行し、`VERSION` が `2` であることを確認してください。
* **wslttyの日本語表示でカーソルがずれる場合**:
    * bashを起動し以下を実行してください。
    ```bash
    echo "Charwidth=ambig-wide" >> `wslpath $APPDATA`/wsltty/config
    ```
---

## 関連リソース
* [Microsoft 公式: WSL のインストール](https://learn.microsoft.com/ja-jp/windows/wsl/install)
* [GitHub: mintty/wsltty](https://github.com/mintty/wsltty)
