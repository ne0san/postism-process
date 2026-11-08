# 現在地

最終更新: 2026-11-08
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

## 次にやること

1. デザインの残り(アクセント色、種類ごとの色の扱い、入口の形。見本はボタン+ポップアップで進行中)
2. 分類の入出力の契約を決めて、サンプルのメモで精度を確かめる
3. アーキテクチャ設計の残り(下の未決事項)
4. ローカルで骨組みを通す → 実行基盤を選ぶ → 薄く本番へ

## 未決事項

- AIプロバイダー
- 認証(最初の1人用の方式、端末を増やすときの方式)
- 分類を動かすタイミング(定期的な巡回だけか、投げた直後にも回すか)
- AIに送る情報の線引き(位置、カレンダーなど)
- 実行基盤(AWS Lambda、Cloudflare Workers など)と保存先のデータベース
- アクセント色(見本を見てから選ぶ)
- 種類ごとの色の扱い、ユーザーによる色の変更([0014](decisions/0014-category-marker-colors.md)を提案中)
- 入口の形(テキストボックス常駐 / ボタン→ポップアップ。見本はボタン+ポップアップで進行中)
- 一覧のソート、解決済みの打ち消し線(機能としてIssue化して扱う)
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
- 種類ごとのマーカー色の採用([0014](decisions/0014-category-marker-colors.md)として提案中)

## ふりかえり

- [準備フェーズの中間ふりかえり(2026-11-08)](retros/2026-11-08-preparation-midway.md)。準備フェーズは未完了で、Effectの学習は進行中。
