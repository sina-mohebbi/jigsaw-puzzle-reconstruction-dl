# Model Card

## Task

Reconstruct a 96x96 RGB image from 9 shuffled 28x28 RGB patches. The patches are produced by splitting an STL-10 image into a 3x3 grid and removing a 2-pixel border from each 32x32 tile.

## Dataset

The project uses the STL-10 unlabeled image set. The notebook downloads the dataset through `tf.keras.utils.get_file`.

## Inputs and Outputs

- Input: 9 shuffled image patches with shape `9 x 28 x 28 x 3`
- Output: reconstructed RGB image with shape `96 x 96 x 3`

## Supervision

The model is trained against the original image only. It does not receive explicit labels for the true location of each patch.

## Metric

Mean Absolute Error (MAE) between the reconstructed image and the target image.

## Reported Result

- Baseline MAE: 0.1822
- Final model MAE: 0.04529

## Limitations

The model can still fail when multiple patches are visually ambiguous or when texture cues are weak. The result should be viewed as an image-reconstruction experiment, not a general-purpose image restoration system.
