# Derivative for Bedrock(統合版)— Vibrant Visuals Edition

Java版のシェーダー「Derivative」(DureXXX)の雰囲気を、統合版の公式グラフィックス機能 **Vibrant Visuals(ヴィブラントビジュアル)** 上で再現するリソースパックです。
Derivativeのコードは使っていません。非公式・非関連の「インスパイア版」です。

## ダウンロード
[Derivative_Bedrock.mcpack](https://storage.googleapis.com/runable-templates/cli-uploads%2FfhqlSTjmWj2zcSiHTfwfTh9VDAqSbOrA%2FSlSCiZvceuw3Nrs-ZYBNE%2FDerivative_Bedrock.mcpack)

または `python3 build.py`(要 git と pillow)で自分で生成できます。

## 導入
1. `Derivative_Bedrock.mcpack` をダブルクリック(またはMinecraftで開く)
2. 設定 > グローバルリソース(またはワールド設定 > リソースパック)で有効化
3. 設定 > ビデオ > グラフィックス で **Vibrant Visuals** を選択
   - 対応: Windows / Xbox / PS5 / iOS / Android 等の Vibrant Visuals 対応端末(Switchは非対応)
4. ゲームバージョン 1.21.120 以上

## 再現しているもの
| 要素 | 内容 |
|---|---|
| 太陽光 | 昼は暖かい白、夕方は深いオレンジ、軌道を12度傾けて影を長く |
| 空 | 濃い青の天頂、朝夕の赤〜紫のグラデーション、強めのミー散乱(太陽のグロー) |
| カラーグレーディング | ACESトーンマップ + ティール&オレンジ(影は青寄り、ハイライトは暖色) |
| バイオーム別 | 砂漠/サバンナ=暖色、雪原=寒色、ジャングル/沼=高彩度、ペイルガーデン=低彩度、洞窟=明るめ、ネザー/エンド=専用 |
| 水 | 波+コースティクス有効。暖海=ターコイズ、寒海=緑がかった青、沼=濁り、川=黄味 |
| 松明など | 点光源を暖色に(松明・ランタン・キャンドル)。魂系はシアン、溶岩・グロウストーンなどは静的光源 |
| 影 | ソフトシャドウ |

## 再現できないもの(統合版の制約)
Vibrant Visuals は JSON とテクスチャによる設定のみで、GLSLを書き換える機能はありません。次はできません。
- ブルーム、被写界深度、モーションブラー、DLSS系、オーロラ等のカスタム描画
- Java版と同じ雲・星・太陽の描画
- 独自のボリューメトリック光線(ゴッドレイ)の追加(Vibrant Visuals標準のものは動作します)

## 調整したいとき
`build.py` の数値を直して `python3 build.py` で再生成できます(`pip install pillow` が必要)。主な項目:
- 明るさ: `grade()` の `gain`
- 彩度: `sat`
- 暖かさ: `temp`(大きいほど暖色)
- 太陽の傾き: `orbital_offset_degrees`

## クレジット
バイオーム設定の雛形: microsoft/minecraft-samples `deferred_lighting_starter`(MIT License, Microsoft Corporation)
