<div itemscope itemtype="http://schema.org/Dataset">
  <div itemscope itemprop="includedInDataCatalog" itemtype="http://schema.org/DataCatalog">
    <meta itemprop="name" content="TensorFlow Datasets" />
  </div>
  <meta itemprop="name" content="cifar100_n" />
  <meta itemprop="description" content="A re-labeled version of CIFAR-100 with real human annotation errors. For every &#10;pair (image, label) in the original CIFAR-100 train set, it provides an &#10;additional label given by a real human annotator.&#10;&#10;To use this dataset:&#10;&#10;```python&#10;import tensorflow_datasets as tfds&#10;&#10;ds = tfds.load(&#x27;cifar100_n&#x27;, split=&#x27;train&#x27;)&#10;for ex in ds.take(4):&#10;  print(ex)&#10;```&#10;&#10;See [the guide](https://www.tensorflow.org/datasets/overview) for more&#10;informations on [tensorflow_datasets](https://www.tensorflow.org/datasets).&#10;&#10;" />
  <meta itemprop="url" content="https://www.tensorflow.org/datasets/catalog/cifar100_n" />
  <meta itemprop="sameAs" content="https://www.cs.toronto.edu/~kriz/cifar.html" />
  <meta itemprop="citation" content="@inproceedings{wei2022learning,&#10;  title={Learning with Noisy Labels Revisited: A Study Using Real-World Human &#10;  Annotations},&#10;  author={Jiaheng Wei and Zhaowei Zhu and Hao Cheng and Tongliang Liu and Gang &#10;  Niu and Yang Liu},&#10;  booktitle={International Conference on Learning Representations},&#10;  year={2022},&#10;  url={https://openreview.net/forum?id=TBWA6PLJZQm}&#10;}" />
</div>

# `cifar100_n`


Note: This dataset was added recently and is only available in our
`tfds-nightly` package
<span class="material-icons" title="Available only in the tfds-nightly package">nights_stay</span>.

Warning: Manual download required. See instructions below.

*   **Description**:

A re-labeled version of CIFAR-100 with real human annotation errors. For every
pair (image, label) in the original CIFAR-100 train set, it provides an
additional label given by a real human annotator.

*   **Homepage**:
    [https://www.cs.toronto.edu/~kriz/cifar.html](https://www.cs.toronto.edu/~kriz/cifar.html)

*   **Source code**:
    [`tfds.image_classification.cifar100_n.Cifar100N`](https://github.com/tensorflow/datasets/tree/master/tensorflow_datasets/image_classification/cifar100_n/cifar100_n.py)

*   **Versions**:

    *   **`1.0.0`** (default): Initial release.

*   **Download size**: `160.71 MiB`

*   **Dataset size**: `136.08 MiB`

*   **Manual download instructions**: This dataset requires you to
    download the source data manually into `download_config.manual_dir`
    (defaults to `~/tensorflow_datasets/downloads/manual/`):<br/>
    Download 'side_info_cifar100N.csv' and 'CIFAR-100_human_ordered.npy' from
    https://github.com/UCSC-REAL/cifar-10-100n.

Then convert 'CIFAR-100_human_ordered.npy' into a CSV file
'CIFAR-100_human_annotations.csv'. This can be done with the following code:

```
import numpy as np
import pandas as pd
import tensorflow as tf

human_labels_np_path = '<local_path>/CIFAR-100_human_ordered.npy'
human_labels_csv_path = '<local_path>/CIFAR-100_human_annotations.csv'

with tf.io.gfile.GFile(human_labels_np_path, "rb") as f:
  human_annotations = np.load(f, allow_pickle=True)

df = pd.DataFrame(human_annotations[()])

with tf.io.gfile.GFile(human_labels_csv_path, "w") as f:
  df.to_csv(f)
```

*   **Auto-cached**
    ([documentation](https://www.tensorflow.org/datasets/performances#auto-caching)):
    Yes

*   **Splits**:

Split     | Examples
:-------- | -------:
`'test'`  | 10,000
`'train'` | 50,000

*   **Feature structure**:

```python
FeaturesDict({
    'coarse_label': ClassLabel(shape=(), dtype=tf.int64, num_classes=20),
    'id': Text(shape=(), dtype=tf.string),
    'image': Image(shape=(32, 32, 3), dtype=tf.uint8),
    'label': ClassLabel(shape=(), dtype=tf.int64, num_classes=100),
    'noise_label': ClassLabel(shape=(), dtype=tf.int64, num_classes=100),
    'worker_id': tf.int64,
    'worker_time': tf.float32,
})
```

*   **Feature documentation**:

Feature      | Class        | Shape       | Dtype      | Description
:----------- | :----------- | :---------- | :--------- | :----------
             | FeaturesDict |             |            |
coarse_label | ClassLabel   |             | tf.int64   |
id           | Text         |             | tf.string  |
image        | Image        | (32, 32, 3) | tf.uint8   |
label        | ClassLabel   |             | tf.int64   |
noise_label  | ClassLabel   |             | tf.int64   |
worker_id    | Tensor       |             | tf.int64   |
worker_time  | Tensor       |             | tf.float32 |

*   **Supervised keys** (See
    [`as_supervised` doc](https://www.tensorflow.org/datasets/api_docs/python/tfds/load#args)):
    `None`

*   **Figure**
    ([tfds.show_examples](https://www.tensorflow.org/datasets/api_docs/python/tfds/visualization/show_examples)):
    Not supported.

*   **Examples**
    ([tfds.as_dataframe](https://www.tensorflow.org/datasets/api_docs/python/tfds/as_dataframe)):
    Missing.

*   **Citation**:

```
@inproceedings{wei2022learning,
  title={Learning with Noisy Labels Revisited: A Study Using Real-World Human
  Annotations},
  author={Jiaheng Wei and Zhaowei Zhu and Hao Cheng and Tongliang Liu and Gang
  Niu and Yang Liu},
  booktitle={International Conference on Learning Representations},
  year={2022},
  url={https://openreview.net/forum?id=TBWA6PLJZQm}
}
```

