# Named Keypoints Format Support for PyMAF-X

This extension adds support for a third keypoint format to PyMAF-X, where keypoints are stored with named keys rather than indexed arrays.

## Named Keypoints Format

```json
{
  "performers": {
    "0": {  // Person ID as string
      "skeletons_2d": {
        "gymnast_closeup": [
          {  // Frame 0
            "keypoints": {
              "nose": [x, y, c],
              "left_eye": [x, y, c],
              "right_eye": [x, y, c],
              // ... other keypoints
            }
          },
          // ... other frames
        ]
      }
    },
    // ... other performers
  }
}
```

### Key Components:

- **performers**: Dictionary of performers/people
  - **person_id**: String identifier for each person (e.g., "0", "1")
    - **skeletons_2d**: Contains different skeleton views
      - **gymnast_closeup**: List of frames with keypoints
        - Each frame contains a **keypoints** dictionary with named body parts
          - Each keypoint is a 3-element array [x, y, confidence]

### Supported Keypoint Names

The following keypoint names are supported and mapped to the COCO format:

- nose
- left_eye
- right_eye
- left_ear
- right_ear
- left_shoulder
- right_shoulder
- left_elbow
- right_elbow
- left_wrist
- right_wrist
- left_hip
- right_hip
- left_knee
- right_knee
- left_ankle
- right_ankle

## Using the Named Keypoints Format

1. Load your JSON file with the named keypoints format
2. Use the `load_named_keypoints_from_json` function from `apps.demo_smplx` to parse it
3. Optionally, convert it to the standard PyMAF-X format using the notebook

## Example Usage

Run PyMAF-X directly with your named keypoints format:

```bash
python -m apps.demo_smplx --image_folder examples/images --keypoints_json your_named_keypoints.json --pretrained_model data/pretrained_model/PyMAF-X_model_checkpoint_v1.1.pt --misc TRAIN.BHF_MODE full_body MODEL.PyMAF.HAND_VIS_TH 0.1
```

## Testing

Use the `test_named_keypoints.ipynb` notebook in the `datasamples` folder to:
1. Load a JSON file with named keypoints
2. Visualize the skeleton
3. Convert to standard PyMAF-X format for further processing

## Details of the Conversion

The conversion process maps the named keypoints to the corresponding indices in the COCO format:

| Named Keypoint   | COCO Index |
|------------------|------------|
| nose             | 0          |
| left_eye         | 1          |
| right_eye        | 2          |
| left_ear         | 3          |
| right_ear        | 4          |
| left_shoulder    | 5          |
| right_shoulder   | 6          |
| left_elbow       | 7          |
| right_elbow      | 8          |
| left_wrist       | 9          |
| right_wrist      | 10         |
| left_hip         | 11         |
| right_hip        | 12         |
| left_knee        | 13         |
| right_knee       | 14         |
| left_ankle       | 15         |
| right_ankle      | 16         |