# Mastra

[![npm version](https://badge.fury.io/js/@mastra%2Fcore.svg)](https://www.npmjs.com/package/@mastra/core)
[![CodeQl](https://github.com/mastra-ai/mastra/actions/workflows/github-code-scanning/codeql/badge.svg)](https://github.com/mastra-ai/mastra/actions/workflows/github-code-scanning/codeql)
[![GitHub Repo stars](https://img.shields.io/github/stars/mastra-ai/mastra)](https://github.com/mastra-ai/mastra/stargazers)
[![Discord](https://img.shields.io/discord/1309558646228779139?logo=discord&label=Discord&labelColor=white&color=7289DA)](https://discord.gg/BTYqqHKUrf)
[![Twitter Follow](https://img.shields.io/twitter/follow/mastra_ai?style=social)](https://x.com/mastra_ai)
[![NPM Downloads](https://img.shields.io/npm/dm/%40mastra%252Fcore)](https://www.npmjs.com/package/@mastra/core)
[![Static Badge](https://img.shields.io/badge/Y%20Combinator-W25-orange)](https://www.ycombinator.com/companies?batch=W25)

Mastraは、AIエージェントやアシスタントを構築するためのTypescriptフレームワークです。世界最大級の企業で、社内AI自動化ツールや顧客向けエージェントの構築に使用されています。

Mastraは、ローカルマシンで実行したり、Honoを使ってNode.jsサーバーにバンドルしたり、サーバーレスクラウドにデプロイしたりすることができます。

Mastraの主な機能は以下の通りです。

| 機能                                                   | 説明                                                                                                                                                                                                                                                                                                   |
| ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| LLMモデル                                              | Mastraはモデルルーティングに[Vercel AI SDK](https://sdk.vercel.ai/docs/introduction)を使用しており、OpenAI、Anthropic、Google Geminiなど、あらゆるLLMプロバイダーと対話するための統一されたインターフェースを提供します。特定のモデルとプロバイダーを選択し、レスポンスをストリーミングするかどうかを決定できます。 |
| [エージェント](https://mastra.ai/docs/agents/overview)       | エージェントは、言語モデルが一連のアクションを選択するシステムです。Mastraでは、エージェントはLLMモデルにツール、ワークフロー、同期データを提供します。エージェントは、独自の関数やサードパーティ統合のAPIを呼び出したり、構築したナレッジベースにアクセスしたりできます。                                   |
| [ツール](https://mastra.ai/docs/agents/adding-tools)       | ツールは、エージェントやワークフローによって実行できる型付き関数で、組み込みの統合アクセスとパラメータ検証機能を備えています。各ツールには、入力を定義するスキーマ、ロジックを実装するエグゼキュータ関数、設定済みの統合へのアクセスがあります。                               |
| [ワークフロー](https://mastra.ai/docs/workflows/overview) | ワークフローは、耐久性のあるグラフベースのステートマシンです。ループ、分岐、人間からの入力を待機、他のワークフローの埋め込み、エラー処理、リトライ、解析などを行います。コードまたはビジュアルエディタで構築できます。ワークフローの各ステップには、OpenTelemetryトレースが組み込まれています。               |
| [RAG](https://mastra.ai/docs/rag/overview)             | RAG（Retrieval-augmented generation）を使用すると、エージェント用のナレッジベースを構築できます。RAGは、チャンキング、埋め込み、ベクトル検索などの特定のクエリ技術を使用したETLパイプラインです。                                                                                                       |
| [統合](https://mastra.ai/docs/integrations)            | Mastraでは、統合はサードパーティサービス用の自動生成されたタイプセーフなAPIクライアントであり、エージェントのツールやワークフローのステップとして使用できます。                                                                                                                                                 |
| [評価](https://mastra.ai/docs/08-running-evals)        | 評価は、モデル評価、ルールベース、統計的手法を使用してLLMの出力を評価する自動テストです。各評価は、0から1の間の正規化されたスコアを返し、ログに記録して比較できます。評価は、独自のプロンプトとスコアリング関数でカスタマイズできます。                                    |

## クイックスタート

### 前提条件

- Node.js (v20.0+)

## LLMプロバイダーのAPIキーを取得する

LLMプロバイダーのAPIキーをお持ちでない場合は、以下のサービスから取得できます。

- [OpenAI](https://platform.openai.com/)
- [Anthropic](https://console.anthropic.com/settings/keys)
- [Google Gemini](https://ai.google.dev/gemini-api/docs)
- [Groq](https://console.groq.com/docs/overview)
- [Cerebras](https://inference-docs.cerebras.ai/introduction)

これらのプロバイダーのアカウントをお持ちでない場合は、サインアップしてAPIキーを取得できます。AnthropicはAPIキーを取得するためにクレジットカードが必要です。一部のOpenAIモデルとGeminiは不要で、APIには寛大な無料利用枠があります。

## 新しいプロジェクトを作成する

Mastraを始める最も簡単な方法は、`create-mastra`を使用することです。このCLIツールを使用すると、すべてが設定された新しいMastraアプリケーションの構築を迅速に開始できます。

```bash
npx create-mastra@latest
```

### スクリプトを実行する

最後に、`mastra dev`を実行してMastraプレイグラウンドを開きます。

```bash copy
npm run dev
```

Anthropicを使用している場合は`ANTHROPIC_API_KEY`を設定します。Geminiを使用している場合は`GOOGLE_GENERATIVE_AI_API_KEY`を設定します。

# MCPサーバー ([@mastra/mcp-docs-server](https://www.npmjs.com/package/@mastra/mcp-docs-server))

Mastraの使用方法をLLMに教えるには、MCPサーバー[@mastra/mcp-docs-server](https://www.npmjs.com/package/@mastra/mcp-docs-server)を使用してください。

これは、AIアシスタントにMastra.aiの完全なナレッジベースへの直接アクセスを提供するモデルコンテキストプロトコル（MCP）サーバーです。

## Cursorでの設定

プロジェクトのルートにある`.cursor/mcp.json`を作成または更新します。

### MacOS/Linux

```
{
  "mcpServers": {
    "mastra": {
      "command": "npx",
      "args": ["-y", "@mastra/mcp-docs-server"]
    }
  }
}
```

### Windows

```
{
  "mcpServers": {
    "mastra": {
      "command": "cmd",
      "args": ["/c", "npx", "-y", "@mastra/mcp-docs-server"]
    }
  }
}
```

これにより、すべてのMastraドキュメンテーションツールがCursorワークスペースで利用可能になります。MCPサーバーはデフォルトでは有効になっていないことに注意してください。Cursorの設定 -> MCP設定に移動し、Mastra MCPサーバーで「有効にする」をクリックする必要があります。

## Windsurfでの設定

`~/.codeium/windsurf/mcp_config.json`を作成または更新します。

### MacOS/Linux

```
{
  "mcpServers": {
    "mastra": {
      "command": "npx",
      "args": ["-y", "@mastra/mcp-docs-server"]
    }
  }
}
```

その他のインストールオプションについては、[https://www.npmjs.com/package/@mastra/mcp-docs-server](https://www.npmjs.com/package/@mastra/mcp-docs-server)をご覧ください。

### Claude Codeでの設定

Claude Codeをインストールした後、次を実行します。

```sh
claude mcp add mastra-docs -- npx -y @mastra/mcp-docs-server
```

## 貢献

貢献に興味がありますか？コーディングからテスト、機能仕様まで、あらゆる種類の支援を歓迎します。

開発者でコードで貢献したい場合は、プルリクエストを開く前に、まずIssueを開いて議論してください。

プロジェクトのセットアップに関する情報は、[開発ドキュメント](./DEVELOPMENT.md)に記載されています。

## サポート

[オープンコミュニティのDiscord](https://discord.gg/BTYqqHKUrf)があります。ぜひご参加いただき、ご質問や実行に関するヘルプが必要な場合はお知らせください。

また、[ページ上部](https://github.com/mastra-ai/mastra)でプロジェクトにスターを付けていただけると、非常に助かります。

## セキュリティ

私たちは、このリポジトリおよびMastra全体のセキュリティを維持することに尽力しています。セキュリティ上の問題を発見された場合は、[security@mastra.ai](mailto:security@mastra.ai)まで責任を持ってご報告ください。折り返しご連絡いたします。
