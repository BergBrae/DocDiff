# DocDiff
A data generator to generate random document changes and their labels + a Swim Transformer to segment changes between documents.

Use Case: Regression testing for automatic PDF generation.

This ia a Swin Transformer-based vision model. Originally trained to learn Change Detection (CD) for remote sensing operations, this model is adopted to identify missing content between two pdf documents under moderate local translations. i.e. the model identifies translated content vs. removed content.

`generate_data.ipynb` shows how synthetic training data is created. Starting with a dataset of document images, two sets of random changes are applied to one document, producing two documents. Random local content is removed, and added to the corresponding output label's channel. In essence, the model must determine if a given sentence/section is somewhere in the other document. If it is not, it will be highlighted in the 3-channel output segmentation map.

`DocDiff.ipynb` Shows the model and training loop used. This model's archtecture is adopted from https://github.com/AI-Zhpp/FTN/tree/main. Inputs are two single-channel document images. Output is a single three-channel segmentation map where two channels are the left and right changes and the third is no change.

## Examples
Highlighted regions signify that the content is not in the other document.

![Example](./images/Screenshot%202024-01-02%20at%201.44.55 PM.png)

![Example](./images/Screenshot%202024-01-02%20at%201.45.48 PM.png)