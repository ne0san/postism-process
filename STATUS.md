# 現在地

最終更新: 2026-11-09
フェーズ: 設計の前の準備(進め方、記録の仕組み、リポジトリの整備)

## 決定済み

[`decisions/README.md`](decisions/README.md) の一覧を参照。要点は次のとおり。

- メモはサーバー上に保存する([0001](decisions/0001-memo-stored-on-server.md))
- 将来Androidにも展開する([0002](decisions/0002-android-in-future.md))
- クライアントは、クロスプラットフォームのアプリとWebを前提にする。FWは後で選ぶ([0019](decisions/0019-client-cross-platform-and-web.md)。0003のPWA先行を置き換え)
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
- AIが出す回答には「AIによる回答」と最小限の表記を付ける([0018](decisions/0018-ai-answer-label.md))
- ミニマル範囲は、投げる / 裏で分類 / 一覧と種類別タブ / 解決にする / 手動の再分類。Issueは次に着手する可能性がある範囲だけ作り、残りは「あとでやる」に置く([0020](decisions/0020-minimal-scope-and-issue-policy.md))

## 次にやること

1. 分類の入出力の契約を決めて、サンプルのメモで精度を確かめる(分類の種類の増減を含む)
2. 解決済みの疑問の見せ方と、疑問へのAIの回答の有無を決める(ミニマルでは、疑問は暫定で打ち消し線)
3. 描き足す画面(詳細画面、設定画面、手動の再分類の操作の中身。手動の再分類は、ミニマルの着手前に要る)
4. PC版とApple Watch版のUI
5. アーキテクチャ設計の残り(下の未決事項)
6. ローカルで骨組みを通す → 実行基盤を選ぶ → 薄く本番へ

## あとでやる

Issueにする前の候補。Issueにしたら、この一覧から消す([0020](decisions/0020-minimal-scope-and-issue-policy.md))。

- 一覧の並び替え
- 解決済みの表示切替(設定画面とセット)
- 疑問へのAIによる回答(出すかどうかは「次にやること」の2で決める。ラベルは[0018](decisions/0018-ai-answer-label.md))
- スマホでのドラッグ&ドロップによる再分類(技術の確認が先)
- 長押しメニューの細部
- PC版とApple Watch版
- 後方互換性のあるAPI設計の調査と考察

## 未決事項

- AIプロバイダー
- 認証(最初の1人用の方式、端末を増やすときの方式)
- 分類を動かすタイミング(定期的な巡回だけか、投げた直後にも回すか)
- AIに送る情報の線引き(位置、カレンダーなど)
- 実行基盤(AWS Lambda、Cloudflare Workers など)と保存先のデータベース
- ユーザーによる色の変更(種類ごとの色分けは[0014](decisions/0014-category-marker-colors.md)で承認済み。設定で変えられるようにするかは未決)
- クライアントのフレームワークの選定(Web側とアプリ側の両立方法を含む)
- アプリとWebの着手順
- 丸角の半透明のタブバーや、キーボードの上の入力欄を、選んだFWで実現できるか(未確認。[0016](decisions/0016-entry-button-popup.md)、[0017](decisions/0017-screen-structure-and-labels.md))
- 複数行メモの扱い(見本では一覧で2行まで表示。全文を見せる詳細画面は未作成)
- 解決済みの疑問の見せ方、疑問へのAIの回答の有無(見本に4案。回答を出す場合のラベルは[0018](decisions/0018-ai-answer-label.md)で決定済み)
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
