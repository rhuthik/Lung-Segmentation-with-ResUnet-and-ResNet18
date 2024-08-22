# Lung Segmentation using CT Scans with ResUnet

This project focuses on accurately segmenting lungs from CT scans using deep learning techniques. We utilize a dataset of 45 lung CT scans with varying numbers of slices and corresponding labels for trachea, left lung, and right lung (combined into a single lung label).

## Link to the Dataset with Labels:


## Project Overview

Our approach involves:
1. Preprocessing steps, including trachea label removal and lung mask amalgamation
2. Experimenting with various deep learning models and loss functions
3. Fine-tuning models to achieve high segmentation accuracy
4. Benchmarking our best model against the state-of-the-art lungmask tool

## Initial Data Processing

We remove the trachea (label 5) and combine left (label 3) and right (label 4) lung masks into a single label.

## Experimentation Results

We conducted experiments with different ResNet-based models and loss function variations. Our best-performing model is ResNet18 with Binary Cross-Entropy (BCE) loss.

| Model         | Train  | Validation | Test   |
|---------------|--------|------------|--------|
| Res34 BCE     | 0.9828 | 0.9667     | 0.9560 |
| **Res18 BCE** | 0.9872 | 0.9444     | **0.9573** |
| Res18 Dice    | 0.9827 | 0.9325     | 0.9517 |
| Res18 Focal   | 0.9780 | 0.9323     | 0.8559 |
| LungMask      | -      | -          | 0.9526 |

## Key Components

1. **Data Preprocessing**: Includes intensity clipping and contrast stretching.
2. **Model Architecture**: Utilizes ResUNet with ResNet18 encoder.
3. **Loss Functions**: Experiments with BCE, Dice, and Focal losses.
4. **Evaluation Metric**: Dice score for segmentation accuracy.

## Best Model: ResUNet with ResNet18 and BCE

- **Architecture**: ResNet18 encoder with U-Net decoder
- **Loss Function**: Binary Cross-Entropy with Logits Loss
- **Performance**: Achieved an average test Dice score of 0.9573

## Comparison with State-of-the-Art

Our best model (Res18 BCE) slightly outperforms the lungmask tool:
- Lungmask (U-net(R231)) Dice Score: 0.952
- Our Best Model (Res18 BCE) Dice Score: 0.957
