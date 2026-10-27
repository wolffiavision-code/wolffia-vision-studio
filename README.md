# Wolffia Vision Studio

Wolffiaおよびウキクサ類の画像について、教師データ作成から推論・計測・解析までを一つのGUIで扱うWindowsアプリケーションです。  
*A Windows application for creating training data, running inference, measuring objects, and analysing images of Wolffia and other duckweeds in a single GUI.*

[Webサイト / Website](https://wolffiavision-code.github.io/wolffia-vision-studio/) · [Releases](https://github.com/wolffiavision-code/wolffia-vision-studio/releases) · [ライセンス / License](LICENSE)

## 概要 / Overview

4つの作業領域から、データ作成、学習・テスト、推論・処理、解析を選択できます。  
*Four workspaces provide data creation, training and testing, inference and processing, and analysis.*

同梱モデルはWolffiaを基にしています。  
*The bundled models were developed using Wolffia images.*

他のウキクサ種にも同じ処理手順を適用できる可能性がありますが、対象種に合った画像、アノテーション、学習、独立した評価が必要です。  
*The same workflow may be applicable to other duckweed species, but target-specific images, annotations, training, and independent evaluation are required.*

## 主な機能 / Main features

### 01 データ作成 / Data creation

- **BBOX・マスクアノテーション / BBOX and mask annotation** — YOLO矩形と二値マスクを別々のデータセットとして作成します。 / *Create YOLO boxes and binary masks as separate datasets.*
- **クラス定義 / Class definitions** — YOLOのクラスID、名前、表示色を編集し、YAMLとして保存します。 / *Edit YOLO class IDs, names, and display colours and save them as YAML.*
- **補助ラベリング / Assisted labelling** — 学習済みモデルを表示中画像または全画像へ適用します。全画像処理は1画像ずつ保存するため、途中停止しても完了済みの結果を保持します。 / *Apply a trained model to the displayed image or all images. All-image processing saves one image at a time and retains completed results if stopped.*
- **YOLOデータセット準備 / YOLO dataset preparation** — train・val・test分割、基本コピー、拡張、クラス均等型拡張に対応します。 / *Prepare train, validation, and test splits with copy-only, augmentation, or class-balancing modes.*

### 02 学習・テスト / Training and testing

- **YOLO / YOLO** — 追加学習、検証、テスト、混同行列、TP・FP・FN・WC、precision、recall、F1、誤判定率を表示・保存します。 / *Fine-tune, validate, and test YOLO models, with confusion matrices, TP, FP, FN, WC, precision, recall, F1, and error rate.*
- **領域分割 / Segmentation** — SegFormer-B0およびLRASPP-MobileNetV3を用いた二値領域分割の学習・テストに対応します。 / *Train and test binary segmentation with SegFormer-B0 and LRASPP-MobileNetV3.*
- **学習モニタリング / Training monitoring** — エポック推移、損失・評価指標、全体・直近20・直近5エポックの傾きを表示します。 / *Monitor epoch history, losses, evaluation metrics, and slopes over all, the latest 20, and the latest 5 epochs.*

### 03 推論・処理 / Inference and processing

- **YOLO検出 / YOLO detection** — 推定画像、比較画像、集計CSVを出力します。 / *Export predicted images, comparison images, and summary CSV files.*
- **切り抜き・個体領域 / Cropping and individual regions** — 検出領域の切り抜き、マスク生成、RGBA画像、元画像位置へ再配置した背景除去画像を出力します。 / *Export detection crops, masks, RGBA images, and background-removed composites mapped to their original positions.*
- **向き補正 / Orientation normalisation** — 個体形状に基づいて向きをそろえます。 / *Normalise orientation from object shape.*
- **連続推定 / Continuous inference** — 動画モードと写真モードに対応します。写真モードでは任意のタイミングで撮影と推定を実行できます。 / *Use video mode or photo mode. Photo mode captures and processes a frame on demand.*
- **カメラフィルター / Camera filters** — 輝度、明るさ、コントラスト、ホワイトバランスなどの条件を記録します。 / *Record filter settings such as luminance, brightness, contrast, and white balance.*

### 04 解析 / Analysis

- **特徴量抽出 / Feature extraction** — 形状、色、テクスチャ、楕円近似などの画像特徴量をCSVへ保存します。 / *Save shape, colour, texture, ellipse-fit, and related image features to CSV.*
- **分別 / Sorting** — MF、DF、Edge候補を、ルールまたは形状特徴量に基づく分別で整理します。画像別または全画像で処理し、根拠をHTMLへ出力します。 / *Sort MF, DF, and Edge candidates using rules or shape-based analysis, per image or across all images, with HTML audit reports.*
- **統合索引 / Master index** — 同じrun内の全cropについて、画像、推論、領域、特徴量、分別結果を統合します。 / *Combine image, inference, region, feature, and sorting information for every crop in a run.*
- **集団解析・作図作表 / Population analysis and charts** — 分布HTMLと、複数CSVを用いた図表を作成します。 / *Create interactive distribution HTML reports and charts from multiple CSV files.*

MF・DF・Edgeは形状解析上の候補ラベルであり、生物学的な同定を保証するものではありません。  
*MF, DF, and Edge are candidate labels from shape analysis and do not constitute guaranteed biological identification.*

## 動作環境 / System requirements

- Windows 10またはWindows 11、64ビット版 / *64-bit Windows 10 or Windows 11*
- セットアップファイルは約2 GBです。インストール、モデル、学習データ、出力用に追加の空き容量が必要です。 / *The installer is approximately 2 GB. Additional storage is required for installation, models, training data, and outputs.*
- NVIDIA GPUは任意です。対応するGPUとドライバーを利用できる場合、一部の学習・推論を高速化できます。 / *An NVIDIA GPU is optional. A compatible GPU and driver can accelerate selected training and inference tasks.*
- GPUを利用できない場合はCPUを選択できます。処理時間は画像、モデル、PC構成によって異なります。 / *CPU execution is available when a GPU cannot be used. Runtime depends on images, models, and computer configuration.*

配布版はPyTorch 2.12.1+cu126を同梱しています。AMD RadeonのGPU演算には現在対応していません。  
*The distributed build includes PyTorch 2.12.1+cu126. AMD Radeon GPU acceleration is not currently supported.*

## インストール / Installation

1. [Releases](https://github.com/wolffiavision-code/wolffia-vision-studio/releases)を開きます。  
   *Open the [Releases](https://github.com/wolffiavision-code/wolffia-vision-studio/releases) page.*
2. `WolffiaVisionStudio-1.0.0-Windows-x64-Setup.exe`をダウンロードします。  
   *Download `WolffiaVisionStudio-1.0.0-Windows-x64-Setup.exe`.*
3. 公開されているSHA-256とダウンロードしたファイルを照合します。  
   *Compare the downloaded file with the published SHA-256 value.*
4. セットアップを実行し、画面の案内に従います。  
   *Run the setup file and follow the installer instructions.*

## Windowsの保護警告 / Windows protection warning

現在のセットアップファイルにはコード署名がありません。Microsoft Defender SmartScreenが「WindowsによってPCが保護されました」と表示する場合があります。  
*The current setup file is not code-signed. Microsoft Defender SmartScreen may display a “Windows protected your PC” warning.*

公式配布元、ファイル名、SHA-256を確認し、Windowsセキュリティで検査してください。脅威が検出された場合、ハッシュが一致しない場合、配布元を確認できない場合は実行しないでください。  
*Verify the official source, filename, and SHA-256, and scan the file with Windows Security. Do not run it if a threat is detected, the hash differs, or the source cannot be verified.*

保護機能の無効化や除外設定は推奨しません。詳しくは[日本語の注意事項](WARNINGS_JA.txt)または[English safety notice](WARNINGS_EN.txt)を参照してください。  
*Disabling protection or adding exclusions is not recommended. See the [Japanese safety notice](WARNINGS_JA.txt) or [English safety notice](WARNINGS_EN.txt).*

## 基本的な使い方 / Basic workflow

1. ホーム画面から作業領域を選択します。  
   *Select a workspace from the Home screen.*
2. 使用する機能、入力、モデル、出力先を設定します。  
   *Choose a task and configure its inputs, model, and output location.*
3. 実行前に入力内容と保存先を確認します。  
   *Check the inputs and destination before starting.*
4. 実行後、元画像、画面表示、CSV、HTML、出力画像を確認します。  
   *After processing, inspect the source images, GUI results, CSV and HTML reports, and output images.*

ホームの「用語・索引」では、画面上の機能名や画像解析・AI関連用語を検索できます。  
*The Terms and Index window provides searchable explanations of GUI functions and image-analysis and AI terminology.*

## アノテーション操作 / Annotation controls

- `N`：新規作成モードと選択モードを切り替えます。 / *Toggle new-item and selection modes.*
- `C`：次に新規作成するYOLO矩形のクラスを1つ進めます。既存矩形は変更しません。 / *Advance the class for the next new YOLO box. Existing boxes are not changed.*
- `D` / `F`：前の画像 / 次の画像へ移動します。 / *Move to the previous / next image.*
- `Delete` / `Backspace`：選択した項目を削除します。 / *Delete the selected item.*
- 矢印キー：選択した矩形を平行移動します。 / *Move the selected box.*
- `E`：マスクのブラシと消しゴムを切り替えます。 / *Toggle the mask brush and eraser.*
- `H`：マスクの表示と非表示を切り替えます。 / *Toggle mask visibility.*

## 学習データ / Training data

YOLOの学習には画像、同名のYOLO形式TXTラベル、クラス名とデータセット位置を定義したYAMLが必要です。  
*YOLO training requires images, matching YOLO-format TXT labels, and YAML defining class names and dataset paths.*

領域分割の学習には画像と、同じファイル名に対応する二値マスク画像が必要です。  
*Segmentation training requires images and matching binary mask images with corresponding filenames.*

YAMLを書き換えるだけでは、新しい種やクラスをモデルへ学習させることはできません。アノテーション済みデータによる学習と、学習に使っていない画像での評価が必要です。  
*Editing YAML alone does not teach a model a new species or class. Training with annotated data and evaluation on held-out images are required.*

## 出力 / Outputs

通常の推論・解析は`output/practice/run_日時/`へまとめ、処理段階ごとのフォルダへ保存します。  
*Routine inference and analysis are grouped under `output/practice/run_timestamp/` and saved by processing stage.*

```text
run_YYYYMMDD_HHMMSS_*/
  input_jpg_trans/
  01_yolo/
  02_crops/
  03_segmentation/
  04_features&analysis/
  all_crops_master_index.csv
```

アノテーション、データセット、学習結果はそれぞれ`output/annotations`、`output/datasets`、`output/training`へ保存できます。保存先はGUIで変更できます。  
*Annotations, datasets, and training results can be saved under `output/annotations`, `output/datasets`, and `output/training`. Destinations can be changed in the GUI.*

## 検証範囲 / Verification scope

1.0.0配布物では、104件のソース回帰テスト、凍結EXE自己診断、隔離インストール、インストール後自己診断を実施しています。  
*The 1.0.0 package was checked with 104 source regression tests, a frozen-executable self-test, an isolated installation, and a post-installation self-test.*

この確認は、すべてのPC構成、撮影条件、対象種、モデル精度を保証するものではありません。  
*These checks do not guarantee operation on every computer configuration, imaging condition, species, or model accuracy.*

AIの出力は補助結果です。重要な解析では、元画像、アノテーション、出力画像、CSV、HTMLの根拠を利用者自身で確認してください。  
*AI output is assistive. For important analyses, users should inspect the source images, annotations, output images, CSV files, and HTML evidence.*

## チェックサム / Checksum

公開ファイルのSHA-256は、各リリースに含まれる`SHA256SUMS.txt`を参照してください。  
*See `SHA256SUMS.txt` in each release for published SHA-256 values.*

```powershell
Get-FileHash .\WolffiaVisionStudio-1.0.0-Windows-x64-Setup.exe -Algorithm SHA256
```

## ライセンスとデータ / License and data

アプリケーションソースはAGPL-3.0です。第三者ライブラリはそれぞれのライセンスに従います。  
*The application source is licensed under AGPL-3.0. Third-party libraries remain subject to their respective licences.*

モデル、教師画像、サンプル画像、解析結果の利用条件はソフトウェアライセンスとは別に確認してください。  
*Check the separate terms for models, training images, sample images, and analysis results; they are not determined by the software licence.*

## 開発者・連絡先 / Developer and contact

Kento Kuwata  
[wolffia.vision@gmail.com](mailto:wolffia.vision@gmail.com)
