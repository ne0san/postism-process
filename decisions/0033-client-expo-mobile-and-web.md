# クライアントは、Expo(React Native)でスマホとWebを作る。デスクトップは必要になったら検討する

- 状態: 承認
- 決定日: 2026-11-16
- 決定者: オーナー

## 背景

[0019](0019-client-cross-platform-and-web.md) で、クライアントをクロスプラットフォームのアプリとWebの両方を前提にし、具体的なフレームワークは後で選ぶことにした。[0028](0028-sync-api.md) では、投影ロジックの共有はクライアントのフレームワークの選定次第とした。

[0016](0016-entry-button-popup.md)、[0017](0017-screen-structure-and-labels.md) の「丸角の半透明のタブバー」「キーボードの上の入力欄」は、フレームワークで実現できるかの確認ではなく、「ネイティブのUIを使いたい」という要件である(オーナーの説明)。

オーナーがPerplexityで調べた候補は、React Native + React Native Web + Electron/Tauri だった。Claudeが、他の選択肢との比較と、ウィジェット・Apple Watch・Web・デスクトップの対応状況を調べた。

## 検討した選択肢

- React Native + Expo
- Flutter
- Kotlin Multiplatform(Compose Multiplatform)

(Kotlin Multiplatformの、ウィジェットとApple Watchの対応は調べていない)

## 決定

- スマホ(iOS、Android)とWebは、Expo(React Native + React Native Web)で作る。
- Expoでできることは、Expoの機能で行う。
- デスクトップは、今は作らない。必要になったときに検討する。
- UIは、ネイティブのUIを使いたい(要件)。0016・0017 の「フレームワークで実現できるか」の確認項目は、この要件に読み替える。

## 議論での論点

(以下はClaudeの提案を含む)

- フレームワークは、オーナーがPerplexityの調査結果を持ち込み、Claudeが比較を調べた。「Expoでできることは、Expoで」「デスクトップは必要になったら検討」は、オーナーの方針。
- iOSのウィジェットとApple Watchは、Expoの場合、本体とは別のターゲット(Swift / SwiftUI)で実装する形になる。ExpoのConfig Plugin(expo-apple-targets)で、`/ios` の外にターゲットを置ける。Flutterも、ウィジェットとWatchはSwiftで別に実装する形だった。この実装の進め方は、今回は決めていない。
- ネイティブUIは、Expo RouterのNativeTabsが、システムのタブバーを描画する(iOS 26ではLiquid Glass)。Webでの見た目は、Claudeの推測で、未確認。
- Webは、Expo(React Native Web)が公式にサポートしている。出力は、`single`、`static`、`server` の3種類。
- デスクトップは、Expo単体では公式サポートを確認できなかった。方法は、Expo Web + Electron/Tauri、react-native-macos / windows、expo-desktop(ベストエフォートのユーザーランド実装)の3つ。
- クライアントがTypeScriptになり、[0004](0004-backend-typescript-effect.md) のバックエンドと言語が揃う(Claudeの指摘)。投影ロジックを共有する具体的な方法は、決めていない。

## 関連する未決事項

- アプリとWebの着手順
- Androidの展開時期([0002](0002-android-in-future.md)。今回の前提で、時期を見直すか)
- ウィジェット、音声入力、Apple Watch、手書き入力を、どの段階で入れるか(ウィジェットとWatchは、別ターゲットで実装する前提)
- 投影ロジックの共有方法([0028](0028-sync-api.md))
- NativeTabsの、Webでの見た目
- デスクトップ版の技術選定(必要になったとき)
