# kongo_materials

株式会社メガネの金剛／MOCA関連の配布物（WB・POP・DM・掲示HTML等）を集約する器。GitHub Pages で公開する静的サイトリポジトリ。

## 目的

- 施策ごとに生成される配布用HTML（Working Backwards資料・店頭掲示物・DM/POP素材のWeb版 等）を、GAS WebApp（clasp deploy）に依存せず**静的ファイルとして自立**させ、GitHub Pages上に集約する。
- 元々 `90_Built/gas/*_wb_webapp/` 配下で GAS スクリプトレット付きのWebAppとして個別デプロイされていたものを、GAS依存を切った素のHTMLとしてこのリポジトリへ移す。

## URL規約

```
/年-施策slug/ターゲットslug/
```

例：

- `/2026-natsuobi/m3-henko/` — 2026年夏帯施策・M3偏光（RARTS）ターゲット向けWB
- `/2026-natsuobi/0307-chokou/` — 2026年夏帯施策・03/07調光（HOYA SENSITY）ターゲット向けWB

**改訂は同一パス上書き**を原則とする。バージョン違いのURLを都度発行しない（リンクを配布した後にURLが変わるとアクセス不能になるため）。改訂履歴はgit historyで追う。

## 監査（audit trail）

- 変更履歴は **git log** を正とする。個別ファイルへの改訂メモの二重記載はしない。
- commit時は**施策slugを明記**する（例：`2026-natsuobi/m3-henko: 目標母数の数値を修正`）。誰が・いつ・どの施策のどこを直したかをgit historyだけで追跡できる状態を維持する。

## Scope（対象範囲）

- **対象**: 株式会社メガネの金剛／MOCAグループ関連の配布物のみ
- **対象外**: マップパートナーの他院（こはる眼科・あいはら歯科・appleK・佐藤眼科・MIYA 等）、青楠会 — いずれも別会社・別組織のため本リポジトリのスコープ外（`_agent/docs/optkongo_glossary.md` 等の金剛SSoTと同じ切り分け）。他院・青楠会向けの配布物は別リポジトリで管理する。

## Not for（このリポジトリに含めないもの＝リスク管理）

以下は**未公開施策情報**であり、公開リポジトリ（GitHub Pages）には含めない：

- 価格の内部原価・仕入原価
- 仕入先の詳細（発注先・単価契約等）
- その他、店舗運営上非公開とすべき内部数値・取引条件

配布物として公開してよい「お客様向け価格・訴求内容」と、社内検討用の「予算比率・目標母数・反応率シナリオ」等の内部数値が混在する資料（WB等）をこのリポジトリに置く場合は、**commit前に辻が内容を確認**すること。判定に迷う場合はscratchpad側の下書き段階で該当箇所をコメントとして残し、辻の検品を経てから本リポジトリへ反映する。

## ディレクトリ構成

```
kongo_materials/
├─ README.md          (本ファイル)
├─ _config.yml         (Jekyll最小設定)
├─ .gitignore
└─ <年-施策slug>/
    └─ <ターゲットslug>/
        └─ index.html
```

## 現在の配布物

| slug | URL | 目的 |
|:--|:--|:--|
| `2026-natsuobi/m3-henko/` | https://tsuji-ai.github.io/kongo_materials/2026-natsuobi/m3-henko/ | 2026年夏帯施策 M3店 偏光（RARTS）向けWB |
| `2026-natsuobi/0307-chokou/` | https://tsuji-ai.github.io/kongo_materials/2026-natsuobi/0307-chokou/ | 2026年夏帯施策 03/07店 調光（HOYA SENSITY）向けWB |

## 検索エンジン対策

各 index.html に `<meta name="robots" content="noindex, nofollow, noarchive">` を埋め込み、検索エンジンのインデックス対象から外す。URLを知る関係者のみアクセスできる運用（GAS webapp 時代と同等の秘匿性）。

注：`robots.txt` はドメインルート（`tsuji-ai.github.io/robots.txt`）でのみ有効でリポサブパスからは制御できないため、本リポでは meta タグでの防御に一本化する。
