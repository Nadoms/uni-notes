# W10 - Object Recognition

## Indexing Local Features
With thousands of features per image, and millions of images to search, matching an object is a high computation task.
For text, an efficient way to find pages where a word occurs is with an index. To use this idea, we map features to visual words.
![3ab2500a0263d99ccb29f936d72657ad.png](./3ab2500a0263d99ccb29f936d72657ad.png)

When querying an image, one can match its features to the known points in the feature space.
Certain combinations of features map to different database images.
![747b2fd05a544014eb989220013d7144.png](./747b2fd05a544014eb989220013d7144.png)

One can **quantize** the feature space by mapping tokens to clusters of close descriptors.
![31b08e9544c4c1b9837b6b6c2bbd2a4f.png](./31b08e9544c4c1b9837b6b6c2bbd2a4f.png)