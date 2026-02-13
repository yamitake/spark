---
title: "GPT-5.3-Codex-Sparkが爆速すぎる件について"
emoji: "⚡"
type: "tech"
topics: ["OpenAI", "GPT", "Codex", "AI", "Cerebras"]
published: true
---

## はじめに

2026年2月12日、OpenAIが新しいコーディング特化モデル「GPT-5.3-Codex-Spark」をリリースしました。「リアルタイムコーディング」を謳うこのモデル、なんと **1秒間に1,000トークン以上** を出力するという爆速っぷり。実際に何がすごいのか、エンジニア視点で掘り下げてみます。

## GPT-5.3-Codex-Sparkとは

GPT-5.3-Codex-Sparkは、OpenAIのコード生成モデル「GPT-5.3-Codex」の軽量版です。ただの軽量版ではなく、**リアルタイムコーディング専用** に設計された初のモデルとのこと。

### 主な特徴

| 項目 | 内容 |
|------|------|
| **推論速度** | 1,000+ トークン/秒 |
| **コンテキストウィンドウ** | 128k トークン |
| **GPT-5.3-Codex比** | 約15倍高速 |
| **入出力** | テキストのみ（マルチモーダルは今後対応予定） |

## Cerebrasとのパートナーシップ

この爆速を実現しているのが、Cerebras社との提携です。2026年1月に発表された100億ドル規模の複数年契約の最初の成果がこのCodex-Sparkです。

### Wafer-Scale Engine 3

Cerebrasの「Wafer-Scale Engine 3（WSE-3）」は、文字通り **ディナープレートサイズ** の巨大チップ。4兆個のトランジスタを搭載し、通常のAIクラスタで発生する通信オーバーヘッドを大幅に削減しています。

NVIDIAの牙城に風穴を開ける存在として注目されているCerebras。OpenAIがNVIDIA以外のハードウェアを本格採用したのは大きなニュースです。

## ベンチマーク結果

### Terminal-Bench 2.0

| モデル | スコア |
|--------|--------|
| GPT-5.3-Codex | 77.3% |
| **GPT-5.3-Codex-Spark** | **58.4%** |
| GPT-5.1-Codex-mini | 46.1% |

精度は落ちますが、速度とのトレードオフとしては十分実用的な数値です。

### SWE-Bench Pro

実際のソフトウェアエンジニアリングタスクを測定するSWE-Bench Proでは：

- **GPT-5.3-Codex**: 15〜17分で完了
- **GPT-5.3-Codex-Spark**: **2〜3分で同等の精度**

開発中のイテレーション速度を考えると、この差は体感で相当変わります。

## 技術的な改善点

速度向上はチップだけではありません。WebSocket接続の最適化も行われています：

- クライアント・サーバー間のオーバーヘッド: **80%削減**
- 最初のトークンが返るまでの時間: **50%改善**
- トークンあたりのオーバーヘッド: **30%削減**

## どこで使える？

現在はリサーチプレビューとして、ChatGPT Proユーザー向けに以下で利用可能：

- Codexアプリ
- CLI
- VS Code拡張機能

APIアクセスは一部のデザインパートナー向けに順次展開中です。

## 論争も

一方で、カリフォルニア州のAI安全法（SB 53）に関する論争も起きています。GPT-5.3-Codexが「高リスク」に分類されたにもかかわらず、約束した安全対策を実施していないとの指摘がウォッチドッグから出ています。OpenAI側は法令遵守を主張していますが、今後の動向には注目です。

## まとめ

GPT-5.3-Codex-Sparkは、「ちょっと待ってる間にコーヒー飲む」みたいな従来のAIコード生成体験を変える可能性があります。

- **爆速**: 1,000トークン/秒、従来の15倍
- **実用的**: ベンチマークで十分なスコア
- **新しいハードウェア**: Cerebras WSE-3の採用

精度と速度のバランスを取りつつ、開発のフィードバックループを短縮する。そんな使い方がメインになりそうです。個人的には、VS Code拡張でサクサク補完が効くなら、日常のコーディングが結構変わるんじゃないかと期待しています。

## 参考リンク

- [Introducing GPT-5.3-Codex-Spark | OpenAI](https://openai.com/index/introducing-gpt-5-3-codex-spark/)
- [Introducing OpenAI GPT-5.3-Codex-Spark Powered by Cerebras](https://www.cerebras.ai/blog/openai-codexspark)
- [OpenAI Releases a Research Preview of GPT-5.3-Codex-Spark | MarkTechPost](https://www.marktechpost.com/2026/02/12/openai-releases-a-research-preview-of-gpt-5-3-codex-spark-a-15x-faster-ai-coding-model-delivering-over-1000-tokens-per-second-on-cerebras-hardware/)
- [OpenAI Debuts First Model Using Chips From Nvidia Rival Cerebras | Bloomberg](https://www.bloomberg.com/news/articles/2026-02-12/openai-debuts-first-model-using-chips-from-nvidia-rival-cerebras)
