# RFD4-Proteina-Tutorial

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mionoyui/RFD4-Proteina-Tutorial/blob/main/RFD4_Proteina_Binder_Design_Tutorial.ipynb)

[RFD4-Proteina](https://github.com/RosettaCommons/RFD4-Proteina) を使って、標的タンパク質に結合する小さなタンパク質（バインダー）を設計する日本語チュートリアルです。Google Colab の無料 T4 GPU で最初から最後まで動きます。

## 題材

免疫チェックポイント受容体 **PD-1**（PDB ID: [4ZQK](https://www.rcsb.org/structure/4ZQK)）を標的に、PD-L1 が結合していた面を狙ってバインダーを設計します。

## このノートブックが扱う範囲

- 標的構造の準備とホットスポットの指定
- 設計条件（YAML）の作成
- RFD4-Proteina による構造・配列の生成
- 構造だけで計算できる指標による一次フィルタリングと可視化
- 再検証（AlphaFold3 / OpenFold3 など）に渡すための FASTA 書き出し

AlphaFold による折り畳みの再検証は Apptainer イメージが必要なため、Colab 自体では行いません。このノートブックで得られる設計はすべて未検証の候補です。

## Google Drive との連携（基本的には不要）

既定では Google Drive には接続せず、出力は Colab のローカルディスク（`/content`）に書かれます。これはセッション終了とともに消えるため、ステップ 12 で ZIP にまとめてダウンロードしてください。

Colab は無操作が続くと切断され、ランタイムにも時間の上限があります。切断をまたいで同じ実験を続けたい場合だけ、ステップ 2 の `BASE_DIR` を Drive 上のパス（`/content/drive/MyDrive/...`）に変更してください。その場合、同じ `RUN_TAG` で再実行すれば足りない分だけ追加生成されます（既存の設計は再生成されません）。

## 使い方

1. 上の **Open in Colab** バッジを開く
2. `[ランタイム] → [ランタイムのタイプを変更]` で GPU（T4 など）を選択
3. 各セルの `#@param` パラメータ（標的の PDB ID、バインダー長、設計本数など）を確認し、必要に応じて調整
4. `[ランタイム] → [すべてのセルを実行]` で一括実行

## 参考リンク

- [RFD4-Proteina（RosettaCommons）](https://github.com/RosettaCommons/RFD4-Proteina)
- [design.yaml の文法リファレンス](https://rfd4-proteina.org/latest/reference/yaml-json.html)
- [4ZQK（PD-1 と PD-L1 の複合体）](https://www.rcsb.org/structure/4ZQK)

## ライセンス

このチュートリアル（ノートブックと付随文書）は MIT License で配布します。

このノートブックが利用するソフトウェアとデータは、それぞれの提供元の条件に従います。

- [RFD4-Proteina](https://github.com/RosettaCommons/RFD4-Proteina)
  — BSD 3-Clause License, Copyright (c) 2026, Institute for Protein Design,
  University of Washington. コード・モデル・重みのいずれも同ライセンスです。
- モデルの重み: [nvidia/RFD4-Proteina](https://huggingface.co/nvidia/RFD4-Proteina)
- 構造データ 4ZQK: RCSB PDB（座標データはパブリックドメイン）
