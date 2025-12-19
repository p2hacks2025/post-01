# P2HACKS2025 アピールシート

## プロダクト名

OctoDeck（おくとでっく）

## コンセプト

キラキラカードを集めてキラキラエンジニアとつながろう！

## 対象ユーザ

- まわりのキラキラエンジニアを探したい人
  - つながりを作りたい
- 他の人の活動をみたい人
  - 作っているものを知りたい
  - 得意分野を知りたい
- 技術イベントにたくさん参加する人
  - どんな人が参加したのか知りたい

## 利用の流れ

1. GitHub アカウントを連携
2. 自分の「キラキラ」GitHub プロフィールカードを作成

### カード交換機能

1. 自分のカードをシェア (AirDrop, SNS)
2. 相手のカードを受け取ることで自分のデッキに追加

### コミュニティ機能

1. イベント単位でコミュニティ参加 (例：P2HACKS2025 コミュニティ)
2. コミュニティでカード一覧を確認
3. コミュニティ内で最も「キラキラ」している人を発見 (Best Contributor, Best Committer, Best Reviewer, Best Issuer, Best Pull Requester)

## 推しポイント

- GitHub のデータをもとに、一人一人デザインが全く違う**世界で一つだけの**「キラキラ」プロフィールカードを作成
  - GitHub の Identicon がカードに表示される
    - カードを唯一無二な存在に
    - 初心を思い出そう！
  - Most Used Language でカードの色が変わる
    - あの人の得意言語を知ることができる！
    - 得意言語が変化することも...??
- AirDrop や SNS で**簡単に**「キラキラ」カードを交換
- イベント単位などのコミュニティで、**GitHub での活動が多い**ユーザのカードを確認
  - イベントの例：P2HACKS2025
  - 活動のタイプによって「**キラキラ**」**光る色が変わります**！
    - レビューマンはあいつだ！

## スクリーンショット(任意)

## 開発体制

### 役割分担

| メンバー               | 担当                                       |
| :--------------------- | :----------------------------------------- |
| 及川 寛太 (Kantacky)   | モバイル (iOS)                             |
| 大須賀 雅也 (まさや)   | バックエンド                               |
| 齊藤 輝 (ヒカル)       | バックエンド                               |
| 仲里 絢音 (Ayanentity) | デザイン, 発表スライド, 癒し系その 1       |
| 藤間 里緒香 (りょーか) | モバイル (iOS), 発表スライド, 癒し系その 2 |

### 開発における工夫した点

#### 全般

- 集まってめっちゃやった！！胃腸炎メンバーとは、Google Meet で逐次相談
- Google Calendar でお互いの予定を把握、共有
- GitHub Projects を活用したタスク管理、共有
- タスクごとに Issue を立てて、必要な情報を書き込み、共有
- Issue や PR を Slack で通知

#### モバイル (iOS)

- MVVM アーキテクチャと swift-dependencies を活用したテスタブルな設計
- カバレッジ 61%のユニットテスト (ViewModel, UseCase)
- TypeSpec と Open API を活用したスキーマ駆動開発
- GitHub Actions (macOS Self-hosted runner) を活用した CI
- TestFlight を活用したデザイナーの実機によるデザインチェック
- fastlane による証明書管理・ビルド・テスト・配信ワークフローの自動化
- Slack への通知によりチームメンバーへの迅速なテスト結果のフィードバック

#### バックエンド

- Clean Architecture を採用
  - 依存性の逆転により、フレームワーク、UI、DB からロジックを保護
  - DI によりテスタビリティの向上
- テストの拡充
  - 安全な機能拡張やファクタリングが可能に
  - テストカバレッジ
    - Handler: 89.1%
    - Service: 98.9%
- GitHub Actions を活用した CI/CD の導入
  - フィードバックサイクルの短縮
  - dev, stg, prod といったデプロイ環境を複数用意することで安全な検証が可能に
- DDD の採用
  - DB や API の都合をドメインロジックに持ち込まないよう、3 つの型を厳密に使い分ける設計
    - DB Model
    - Domain Entity
    - API Type
  - 上記 3 つを完全に分離し、相互変換層を実装することで DB スキーマ変更や API 仕様変更の影響範囲を局所化
- スキーマ駆動開発
  - スキーマからコードを生成することで型安全
- ドキュメントの拡充
  - スキーマの変更に追従して更新されるドキュメントにより、最新の API の仕様をチームで共有
  - ER 図を用意し、テーブル間のリレーションや制約をチームで共有
  - アーキテクチャ図により、Handler / Service / Domain / Repository の責務を明確化

#### デザイン

- Figma の開発モードを用いたデザイナー・エンジニア間のコミュニケーションの円滑化
- 素早くイメージを共有するため、まず手描きで画面フロー全体を共有し、随時チーム全員で認識を揃えた上で、Figma でデザインを清書した
- カードがよりキラキラして見えるよう、何度も試行錯誤した
- ![][image1]

## 開発技術

### 利用したプログラミング言語

- Swift
- Go

### 利用したフレームワーク・ライブラリ

#### モバイル (iOS)

- Apple Frameworks
  - Foundations
  - Observation
  - SwiftUI
- Swift Packages
  - airbnb/lottie-ios
  - apple/swift-openapi-generator
  - apple/swift-openapi-runtime
  - apple/swift-openapi-urlsession
  - kean/Nuke
  - pointfreeco/swift-dependencies

#### バックエンド

- gin-gonic/gin
- gorm.io/gorm
- gorm.io/driver/postgres
- jackc/pgx/v5
- cloud.google.com/go/cloudsqlconn
- oapi-codegen/runtime
- oapi-codegen/gin-middleware
- getkin/kin-openapi
- google/go-github/v80
- google/uuid
- joho/godotenv

### その他開発に使用したツール・サービス

- Claude Code
- Cursor
- fastlane
  - match
  - gym
  - scan
  - pilot
- Figma
- Gemini
- GitHub
- GitHub Actions
- GitHub Projects
- Google Cloud
  - Cloud Run
  - Cloud SQL
- Google Calendar
- Slack
- Redocly
- TestFlight
- Xcode
- OpenAPI Code Generator
