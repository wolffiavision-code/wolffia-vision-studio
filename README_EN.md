# Wolffia Vision Studio 1.0.0

[日本語](README.md) · [License](LICENSE) · [License guide](LICENSE_EN.md)

A Windows desktop workflow for duckweed image annotation, dataset preparation, fine-tuning, held-out testing, object detection, masks, orientation alignment and feature measurement. Other duckweed species require appropriate annotations and independent evaluation.
By Kento Kuwata / wolffia.vision@gmail.com

## Install

Download the 1.0.0 setup from GitHub Releases, compare SHA256SUMS.txt, and follow the installer. Python is bundled. Japanese and English shortcuts are included. The website itself does not run inference.

Windows protection warnings
This 1.0.0 build is unsigned. SmartScreen may show "Windows protected your PC". This warning alone neither proves infection nor guarantees safety.
Verify the official download source, filename and published SHA-256. A matching hash verifies integrity, not harmlessness. Scan the download. Only if you trust the source and choose to proceed, use "More info" then "Run anyway".
Do not run files with a mismatched hash, unknown origin or a detected threat. If organization policy or Smart App Control blocks execution, contact your administrator. Do not disable protection or add antivirus exclusions.
Publisher-side options include trusted code signing or Microsoft Store distribution. Signing does not guarantee immediate removal of reputation warnings. This package has not been signed.
Analysis and classification are assistive. Accuracy and applicability to other duckweed species are not guaranteed. Keep original data and review results. Do not load untrusted .pt checkpoints.
Reference: https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation

## Workflow

Select a workspace on HOME, then YOLO or Mask. Click a rectangle to select its list item; double-click an item to change only that rectangle's class. N toggles new annotation; Delete/Backspace removes selection; E toggles mask eraser and H toggles visibility. Review assisted labels before export.
Use preprocessing to split train/val/test. For prepared training input, select the parent containing data.yaml and images/labels or masks. An unsplit annotation export is not a prepared training dataset. Separate input shows four train/validation image and label/mask folders plus class definition data.yaml. Source files are copied.
Training displays a validation confusion matrix every epoch (GT rows / prediction columns), not a training-set matrix. Testing shows comparisons, a matrix, TP/FP/FN/WC, precision, recall, F1 and processing error count. Binary masks count pixels and have WC=0.

## Output layout

```text
output/
  annotations/             BBOX_annotation_* / Mask_annotation_*
  datasets/                dataset_*
  training/                yolo_finetune_* / segmentation runs
  run_YYYYMMDD_HHMMSS_*/
    input_jpg_trans/
    01_yolo/               predicted / comparisons / details / CSV
    02_crops/
    03_segmentation/        original_seg / normalize
    04_features&analysis/  features / population / sorting
  continuous_YYYYMMDD_HHMMSS_*/
    01_yolo/               predicted / comparisons / annotated.mp4 / CSV
default_models/
  yolo/best.pt
  segmentation/
  download/

```

Crop margin defaults to 0%. Test output defaults to the selected checkpoint's parent folder. Manual output selection remains available. Bilingual terminology and numerical dictionaries are in config/dictionaries.

[Dataset form setup](FORM_SETUP_EN.md). The owner must configure a responder URL. See the bundled verification record for tested scope. Independent clean-PC testing, all Windows/GPU combinations, elimination of protection warnings and downloading 1.0.0 from the public site remain unverified. Models and images have separate redistribution terms.
Corresponding source and third-party license notices are included in the executable distribution.
