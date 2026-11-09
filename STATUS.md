# 現在地

最終更新: 2026-11-09
フェーズ: 設計の前の準備(進め方、記録の仕組み、リポジトリの整備)

## 決定済み

[`decisions/README.md`](decisions/README.md) の一覧を参照。要点は次のとおり。

- メモはサーバー上に保存する([0001](decisions/0001-memo-stored-on-server.md))
- 将来Androidにも展開する([0002](decisions/0002-android-in-future.md))
- クライアントはPWAを先行する([0003](decisions/0003-pwa-first.md))
- バックエンドはTypeScript + Effect、実行基盤は未確定([0004](decisions/0004-backend-typescript-effect.md))
- 進め方はスクラム風([0005](decisions/0005-scrum-like-process.md))
- 公開前提のポートフォリオ([0006](decisions/0006-public-portfolio.md))
- リポジトリは3つ([0007](decisions/0007-three-repositories.md))
- 決定ログはこのリポジトリ1か所([0008](decisions/0008-decision-log-operation.md))
- アプリ名はPostism([0009](decisions/0009-app-name-postism.md))
- 開発の分担: コーディングはローカルのClaude Code、進行はClaudeアプリのプロジェクト([0010](decisions/0010-development-roles.md))
- 開発プロセス: Issue、ブランチ、PR、CI、別セッションのレビューを最初から採用([0011](decisions/0011-development-process.md))
- Issue・PRのテンプレとDoD、バックログ推移の見せ方([0012](decisions/0012-templates-and-dod.md))
- デザイン原則(見た目の方針)([0013](decisions/0013-design-principles.md))
- 種類ごとのマーカー色を採用し、0013の原則3・6の色の部分を置き換える([0014](decisions/0014-category-marker-colors.md))
- アクセント色は紫系([0015](decisions/0015-accent-color-purple.md))
- 入口は、右下の丸い追加ボタンから開くポップアップ([0016](decisions/0016-entry-button-popup.md))
- 画面構成と表記: 下タブ4つ、「気づき」→「記録」、マーカーの形([0017](decisions/0017-screen-structure-and-labels.md))

## 次にやること

1. ミニマル範囲の線引きと、Issue化の方針(別セッション)
2. 分類の入出力の契約を決めて、サンプルのメモで精度を確かめる(分類の種類の増減を含む)
3. デザインの残り(解決済みの疑問の見せ方とAIの回答の有無、詳細画面と設定画面、手動の再分類の操作、スマホでのドラッグ&ドロップ、PC版とApple Watch版)
4. アーキテクチャ設計の残り(下の未決事項)
5. ローカルで骨組みを通す → 実行基盤を選ぶ → 薄く本番へ
6. (あとで)後方互換性のあるAPI設計の調査と考察

## 未決事項

- AIプロバイダー
- 認証(最初の1人用の方式、端末を増やすときの方式)
- 分類を動かすタイミング(定期的な巡回だけか、投げた直後にも回すか)
- AIに送る情報の線引き(位置、カレンダーなど)
- 実行基盤(AWS Lambda、Cloudflare Workers など)と保存先のデータベース
- ユーザーによる色の変更(種類ごとの色分けは[0014](decisions/0014-category-marker-colors.md)で承認済み。設定で変えられるようにするかは未決)
- 丸角の半透明のタブバーや、キーボードの上の入力欄を、PWAで実現できるか(未確認。[0016](decisions/0016-entry-button-popup.md)、[0017](decisions/0017-screen-structure-and-labels.md))
- 一覧のソート、解決済みの打ち消し線(機能としてIssue化して扱う)
- 複数行メモの扱い(見本では一覧で2行まで表示。全文を見せる詳細画面は未作成)
- 解決済みの疑問の見せ方、疑問へのAIの回答の有無(見本に4案。ラベル「AIによる回答」は[0013](decisions/0013-design-principles.md)の原則2との整合も確認する)
- 分類の種類の増減
- Effectの書き方の方針(`pipe`中心か`Effect.gen`中心か。postism側のCLAUDE.mdに書く)
- スマホでのドラッグ&ドロップの扱い
- 「未確認」リスト(AI整理の直後で、まだ見ていない項目を見せる)をどう扱うか
- Google Play、ドメイン、商標の確認
- 各リポジトリのライセンス
- レビューの観点
- GitHub Projectの公開範囲(Insightsが公開側から見えるかの確認を含む)
- Claude Codeから過程リポジトリを読む具体的な方法

## 未承認の仮案(決定ではない)

AI(Claude)が議論の中で出した案のうち、承認されていないもの。決定として扱わない。

- Cloudflare Workers + D1 + Cron Trigger の構成
- 5分おきの巡回、1回のAI呼び出しで分割・分類・回答をまとめて行う設計
- 固定トークンによる認証
- 4週間の工程案
- 分類の種類の追加(調べもの、アイデア、想い)

## ふりかえり

- [準備フェーズの中間ふりかえり(2026-11-08)](retros/2026-11-08-preparation-midway.md)。準備フェーズは未完了で、Effectの学習は進行中。
