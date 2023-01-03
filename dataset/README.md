> **_NOTE:_**
> The data set in this directory is derived from the original [UIBert dataset](https://github.com/google-research-datasets/uibert#data-format), which is distributed under [CC BY 4.0](License).

# UI understanding datasets for UIBert

This directory contains only the RefExp dataset from the original [UIBert paper](https://arxiv.org/abs/2107.13731).

In RefExp, each datapoint contains a UI and a referring expression of a UI
element on it, such as “Red button on the top”.

The dataset uses unique image ids in both datasets to represent the UI and they can be
used to retrieve the original UI data in
[Rico](https://interactionmining.org/rico).

## RefExp Data format

The data set is saved as TFRecords, which makes it easy to be loaded in
Tensorflow.

Each TFRecord has the following features. Values under
`image/view_hierarchy` are information extracted from UI’s view hierarchy
file.

    -   `image/id`: bytes_list[1]. Image id.
    -   `image/ref_exp/label`: int64_list[1]. Index of the UI element that is
        referred to by the referring expression in the `image/object/bbox/…`
        list.
    -   `image/ref_exp/text`: bytes_list[1]. Referring expression.
    -   `image/object/bbox/{xmax|xmin|ymax|ymin}`: float_list of variable
        length. UI elements on the UI. The number of elements is denoted in
        `image/object/num`.
    -   `image/object/num`: float_list[1]. Number of UI elements.

    -   `image/view_hierarchy/bbox/{xmax|xmin|ymax|ymin}`: float list of
        variable length. Bounding boxes of leaf nodes in the view hierarchy.

    -   `image/view_hierarchy/class/label`: int64_list. Label of the class name.

    -   `image/view_hierarchy/class/name`: bytes_list. Processed class name
        string in the view hierarchy.

    -   `image/view_hierarchy/description` bytes_list. Content description
        string in the view hierarchy.

    -   `image/view_hierarchy/id/name`: bytes_list. Processed source id string
        in the view hierarchy.

    -   `image/view_hierarchy/text`: byte_list. Text string in the view
        hierarchy.

## Citation

If you use or discuss this dataset in your work, please cite the original paper:

```
@misc{bai2021uibert,
      title={UIBert: Learning Generic Multimodal Representations for UI Understanding},
      author={Chongyang Bai and Xiaoxue Zang and Ying Xu and Srinivas Sunkara and Abhinav Rastogi and Jindong Chen and Blaise Aguera y Arcas},
      year={2021},
      eprint={2107.13731},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```

## License

Datasets are licensed under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
