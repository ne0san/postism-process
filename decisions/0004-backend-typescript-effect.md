# バックエンドはTypeScript + Effectにする(実行基盤は未確定)

- 状態: 承認
- 決定日: 2026-11-02
- 決定者: オーナー

## 背景

バックエンドの言語として、TypeScript(Effect)と、AWS LambdaでのGoの2案を想定していた。

## 検討した選択肢

- TypeScript + Effect(実行基盤は、AWS Lambdaでも、Cloudflare Workersでも動かせる見込み)
- Go(AWS Lambda)

## 決定

言語はTypeScript + Effectにする。実行基盤(PaaS)は未確定のままにする。

## 議論での論点

(以下はClaudeの提案を含む)

- PWAと同じ言語になり、型や契約(スキーマ)を共有しやすい。
- 再試行、定期実行、AIのモックと本物の差し替えといった要件が、Effectの部品に合う。
- Effectには学習コストがある。Goは起動が速く、運用が素直という利点がある。
- 実行基盤に依存しないコアにして、保存、AI呼び出し、定期起動を差し替え可能にする案がある(未承認の案)。

## 関連する未決事項

- 実行基盤(AWS Lambda / Cloudflare Workers など)の選定。時期の案は、ローカルで骨組みが通ったあと、本番を作る前
- 保存先のデータベースの選定
- AIプロバイダー
