# customer-targeting-portfolio

## 📘 概要
このリポジトリは、SIGNATE提供の「銀行の顧客ターゲティング」データをもとに、顧客ごとに「定期預金（Y）」と「NISA口座（X）」のどちらを優先提案すべきかを確率的に判定する分析プロジェクトです。RandomForestと確率較正を用いて成功確率を算出し、各顧客に対してより効果的な施策を選択するシミュレーションを実施しています。NISAに関するデータは、顧客属性に基づいて仮想的に生成したものです。

## ⚙️ 使用技術
- **プログラミング**：Python（pandas, numpy, scikit-learn, matplotlib, seaborn）
- **モデル構築**：RandomForestClassifier, CalibratedClassifierCV（確率較正付きモデル）
- **特徴量処理**：ColumnTransformer, OneHotEncoder, StandardScaler
- **データ分割**：train / validation / test の三分割による汎化性能検証
- **評価指標**：ROC-AUC, PR-AUC, LogLoss, Brierスコア, 成功率リフト分析
- **可視化**：matplotlib / seaborn による分布・精度曲線・ヒストグラム描画
- **レポーティング**：Jupyter Notebook（Colab）＋ PowerPoint（自動生成による報告書出力）
- **その他**：git / GitHub（ポートフォリオ公開・バージョン管理）

## 📊 成果物
- 概要版レポート（8p）: [`docs/report_summary.pdf`](docs/report_summary.pdf)
- 詳細分析（22p）: [`docs/appendix_trend_analysis.pdf`](docs/appendix_trend_analysis.pdf)
- スライド資料: [`docs/portfolio_summary_slides.pptx`](docs/portfolio_summary_slides.pptx)

## 🔒 データについて
本分析は SIGNATE 提供の「銀行の顧客ターゲティング」データをもとに構成しています。  
NISA関連の属性は仮想的に生成したペルソナデータであり、元データは含まれていません。
