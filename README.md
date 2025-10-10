# customer-targeting-portfolio

## 📘 概要
このリポジトリは、SIGNATE提供の「銀行の顧客ターゲティング」データをもとに、顧客ごとに「定期預金（Y）」と「NISA口座（X）」のどちらを優先提案すべきかを確率的に判定する分析プロジェクトです。RandomForestと確率較正を用いて成功確率を算出し、各顧客に対してより効果的な施策を選択するシミュレーションを実施しています。NISAに関するデータは、顧客属性に基づいて仮想的に生成したものです。

## ⚙️ 使用技術
- **言語・環境**
  - Python（pandas, numpy, scikit-learn, matplotlib, seaborn）
  - Jupyter Notebook / Google Colab による再現性ある分析環境

- **データ前処理**
  - 数値・カテゴリ変数を自動判別し、`ColumnTransformer` で統合前処理
  - 数値：`StandardScaler` による標準化  
    カテゴリ：`OneHotEncoder(handle_unknown='ignore')` によるワンホット化
  - `Pipeline` 構築により、前処理〜学習〜推論までを一貫化

- **モデル構築**
  - `RandomForestClassifier`（n_estimators=300, class_weight='balanced'）
  - 確率較正：`CalibratedClassifierCV(method='sigmoid', cv='prefit')` による Platt scaling
  - 目的変数（定期預金・NISA）ごとに個別モデルを構築し、成功確率を比較・採択

- **モデル評価**
  - 識別力指標：ROC-AUC, PR-AUC  
  - 確率信頼性：LogLoss, Brierスコア, 校正曲線（`calibration_curve`）
  - 政策評価：Policy成功率、Baseline比較（Always Y / Always X / Random）
  - 意思決定精度：実際の成功フラグとの整合率

- **可視化**
  - seaborn / matplotlib による分布・ヒストグラム・精度曲線可視化
  - 確率分布、校正曲線、Top-N 成功率などをグラフ化して報告資料化

## 📊 成果物
- 概要版レポート（8p）: [`docs/report_summary.pdf`](docs/report_summary.pdf)
- 詳細分析（22p）: [`docs/appendix_trend_analysis.pdf`](docs/appendix_trend_analysis.pdf)

## 🔒 データについて
本分析は SIGNATE 提供の「銀行の顧客ターゲティング」データをもとに構成しています。  
NISA関連の属性は仮想的に生成したペルソナデータであり、元データは含まれていません。
データセット名：銀行の顧客ターゲティング(学習用データ)
取得元： [https://user.competition.signate.jp/ja/competition/detail/?competition=092375ab3c4a43c18c8277e1fd264aa9&task=f3c678327db64f3b988fb85d8a49e5ed&tab=dataset)
データの内容：定期預金勧誘に関する顧客属性および取引情報
