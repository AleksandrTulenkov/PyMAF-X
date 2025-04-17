# PyMAF-X Keypoints JSON Format
```json
[
  [  // Frame 0
    {  // Person 0
      "nose": {
        "x": 1509,
        "y": 467,
        "confidence": 0.95947265625,
        "bbox": {
          "image_width": 1920,
          "image_height": 1080,
          "x1": 723,
          "y1": 206,
          "x2": 872,
          "y2": 651
        },
        "was_initialized": true
      },
      "left_eye": {
        "x": 1516,
        "y": 458,
        "confidence": 0.9697265625,
        "bbox": {
          "image_width": 1920,
          "image_height": 1080,
          "x1": 723,
          "y1": 206,
          "x2": 872,
          "y2": 651
        },
        "was_initialized": true
      },
      // ... other keypoints
    }
  ],
  // ... more frames
]
```

## Example Usage

```bash
# Named keypoints format (only supported format)
python -m apps.demo_smplx --image_folder examples/images --keypoints_json path/to/named_keypoints.json --pretrained_model data/pretrained_model/PyMAF-X_model_checkpoint_v1.1.pt --misc TRAIN.BHF_MODE full_body MODEL.PyMAF.HAND_VIS_TH 0.1
```

## Sample JSON Files

- Named keypoints format sample: `examples/named_keypoints_sample.json`