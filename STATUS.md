# 現在地

最終更新: 2026-11-12
フェーズ: 設計の前の準備(進め方、記録の仕組み、リポジトリの整備)

## 決定済み

[`decisions/README.md`](decisions/README.md) の一覧を参照。要点は次のとおり。

- メモはサーバー上に保存する([0001](decisions/0001-memo-stored-on-server.md))
- 将来Androidにも展開する([0002](decisions/0002-android-in-future.md))
- クライアントは、クロスプラットフォームのアプリとWebを前提にする。FWは後で選ぶ([0019](decisions/0019-client-cross-platform-and-web.md)。0003のPWA先行を置き換え)
- バックエンドはTypeScript + Effect。実行基盤は0024で確定([0004](decisions/0004-backend-typescript-effect.md))
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
- ミニマル範囲は、投げる / 裏で分類 / 一覧と種類別タブ / 解決にする / 手動の再分類。Issueは次に着手する可能性がある範囲だけ作り、残りは「あとでやる」に置く([0020](decisions/0020-minimal-scope-and-issue-policy.md))。ミニマルのIssue: [#1 投げる](https://github.com/ne0san/postism/issues/1) / [#2 一覧と種類別タブ](https://github.com/ne0san/postism/issues/2) / [#3 裏で分類](https://github.com/ne0san/postism/issues/3) / [#4 解決にする](https://github.com/ne0san/postism/issues/4) / [#5 手動で再分類](https://github.com/ne0san/postism/issues/5)
- 解決済みの疑問は打ち消し線で見せる。疑問へのAIの回答は、つける前提でミニマルには含めない([0021](decisions/0021-resolved-question-display-and-ai-answer-scope.md))
- 手動の再分類は長押しメニューの「種類を変更」から。分類前は回転する丸で示す。複数行は折りたたみのトグル。折りたたみのないテキストのタップで編集。編集後も種類は今のまま。「編集」をミニマルに入れる。詳細画面は作らない([0022](decisions/0022-reclassify-pending-collapse-edit.md))。編集のIssue: [#6 編集する](https://github.com/ne0san/postism/issues/6)
- 分類の契約: 種類は ToDo / 疑問 / 記録 の3種固定、1メモ=1種類、暫定のAIは Claude Haiku 5.5、確信度はユーザーに見せず統計として保存する、分類はメモを投げた直後に動かす([0023](decisions/0023-classification-contract.md))
- イベントソーシングを採用する。実行基盤はAWS Lambda、イベントの保存先はDynamoDB、投影はTiDB。0004の実行基盤の未確定を確定する([0024](decisions/0024-event-sourcing-and-infrastructure.md))

## 次にやること

1. PC版とApple Watch版のUI
2. アーキテクチャ設計の残り(下の未決事項)
3. ローカルで骨組みを通す → 薄く本番へ(実行基盤は0024で確定済み)

## あとでやる

Issueにする前の候補。Issueにしたら、この一覧から消す([0020](decisions/0020-minimal-scope-and-issue-policy.md))。

- 一覧の並び替え
- 解決済みの表示切替(設定画面とセット)
- 疑問へのAIによる回答(つける前提。ミニマルには含めない([0021](decisions/0021-resolved-question-display-and-ai-answer-scope.md))。出すときは、疑問に分類したあとに別途質問を投げる仕組みにする案。ラベルは[0018](decisions/0018-ai-answer-label.md))
- スマホでのドラッグ&ドロップによる再分類(技術の確認が先)
- ユーザーが起動する再AI分類の操作(編集後も分類は今の種類のまま。[0022](decisions/0022-reclassify-pending-collapse-edit.md))
- 1メモに複数の中身が混ざる場合の分割([0023](decisions/0023-classification-contract.md)で1メモ=1種類を採用。分割は後回し)
- 分類の種類の追加(アイデア、予定など。使ってみて「記録」の中身を見てから。[0023](decisions/0023-classification-contract.md))
- 長押しメニューの細部
- PC版とApple Watch版
- 後方互換性のあるAPI設計の調査と考察
- postismをprocessから独立させる(コントリビュートを受け入れる前に。きっかけは、CONTRIBUTING.mdを書く時点や、外部からの反応。postism側のIssueテンプレとPRテンプレの、processへの言及2か所の直しを含む)

## 未決事項

- AIプロバイダーの最終確定(暫定は Claude Haiku 5.5。[0023](decisions/0023-classification-contract.md)。公式単価の確認が前提で、使ってみて見直す)
- 認証(最初の1人用の方式、端末を増やすときの方式)
- 失敗した分類の再試行の仕組み(定期的な巡回など。[0023](decisions/0023-classification-contract.md))
- AIに送る情報の線引き(位置、カレンダーなど)
- イベントの種類と形、同期のAPI(冪等性、カーソル)、投影の冪等性と再構築、メモの削除の扱い([0024](decisions/0024-event-sourcing-and-infrastructure.md))
- TiDBのプランと起動待ちの確認(公式で料金も確認。[0024](decisions/0024-event-sourcing-and-infrastructure.md))
- ユーザーによる色の変更(種類ごとの色分けは[0014](decisions/0014-category-marker-colors.md)で承認済み。設定で変えられるようにするかは未決)
- クライアントのフレームワークの選定(Web側とアプリ側の両立方法を含む)
- アプリとWebの着手順
- 丸角の半透明のタブバーや、キーボードの上の入力欄を、選んだFWで実現できるか(未確認。[0016](decisions/0016-entry-button-popup.md)、[0017](decisions/0017-screen-structure-and-labels.md))
- 分類前のメモを編集できるか(編集中に分類が終わったときの扱いを含む)
- 分類の検証サンプル(架空メモ200件)とスクリプトの置き場所(公開リポジトリに置くか)
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

- 5分おきの巡回
- 固定トークンによる認証
- 4週間の工程案

## ふりかえり

- [準備フェーズの中間ふりかえり(2026-11-08)](retros/2026-11-08-preparation-midway.md)。準備フェーズは未完了で、Effectの学習は進行中。
