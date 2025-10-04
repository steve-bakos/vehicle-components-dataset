# Vehicle Interior Components Dataset - Public Release

This dataset contains information about vehicle interior components across multiple brands and models.

## Structure

```
data_public/
├── dataset/
│   ├── brands.json           # List of all brands
│   └── [Brand]/              # Browse directories for available models
│       └── [Model]/
│           ├── components.json      # List of components
│           └── image_sources.json   # Image source metadata
└── ground_truth/
    └── [Brand]/
        └── [Model]_annotations.json # Ground truth annotations
```

## Image Sources

Due to copyright restrictions, this dataset does not include the actual images. Instead, each model directory contains an `image_sources.json` file with references to where the images can be found in the manufacturer's owner's manuals.

### Image Sources Format

Each model has a single image source entry with a consistent format. All models include `brand`, `model`, `source.url`, and `source.page`.

```json
{
  "brand": "Acura",
  "model": "2022 ILX",
  "source": {
    "url": "https://cdn.dealereprocess.org/cdn/servicemanuals/acura/2022-ilx.pdf",
    "page": 6
  }
}
```

**Important:** Some vehicle legends span multiple pages in the owner's manual. In these cases, you must stitch the pages together to create a single composite image as seen by the annotators. The `page` field indicates the starting page of the legend.

## Dataset Contents

### Components
Each model includes a `components.json` file listing all interior components found in the vehicle.

### Ground Truth Annotations
The `ground_truth/` directory contains spatial relationship annotations for each model, including:
- Component names and IDs
- Size and frequency information
- Spatial relationships (proximity, position, landmark status)
- Note: Placeholder significance values have been removed from the public release

### Image Sources
Each model includes an `image_sources.json` file with references to owner's manual pages where the interior diagrams can be found.

## Usage

To use this dataset:
1. Download the data
2. Reference the `image_sources.json` files to obtain images from manufacturer's owner's manuals
3. For legends spanning multiple pages, stitch them together into a single composite image
4. Load the `components.json` to see the list of components for each model
5. Use the ground truth annotations for training or evaluating spatial relationship models

## Citation

If you use this dataset in your research, please cite:

```bibtex
@inproceedings{bakos2025generating,
  title={Generating Spatial Knowledge Graphs from Automotive Diagrams for Question Answering},
  author={Bakos, Steve and Xing, Chen and Davoudi, Heidar and An, Aijun and DiCarlantonio, Ron},
  booktitle={Proceedings of the 2025 Conference on Empirical Methods in Natural Language Processing (EMNLP)},
  year={2025},
  url={[Paper URL - will be added upon publication]}
}
```

**Note:** This dataset accompanies our EMNLP 2025 paper. The full paper link and OpenReview discussion will be added once published.

## License

The data annotations are provided under [LICENSE]. Images must be obtained from the original manufacturer sources and are subject to their respective copyrights.
