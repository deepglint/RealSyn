# RealSyn-100M

[RealSyn](https://arxiv.org/pdf/2502.12513) is a large-scale dataset that contains up to 100M synthetic multimodal interleaved documents (available in 15M, 30M, and 100M scales) to enhance the usability for vision-language representation learning. Our dataset follows a novel transformation paradigm, converting real-world image-text pairs (extracted from 118M documents in the OBELICS dataset) into coherent interleaved documents by combining retrieved realistic texts with synthetic captions generated via a visual semantic augmented module. We expect RealSyn to be used to train popular large-scale foundation models, offering a high-quality, semantically balanced alternative to noisy web-crawled datasets.

## Download the metadata

Download RealSyn Dataset from [🤗Hugging Face](https://huggingface.co/collections/Kaichengalex/realsyn-dataset).

```bash
# brew install git-xet
# git xet install
bash hfd.sh Kaichengalex/RealSyn100M --dataset --tool aria2c -x 10
```

## Download the images with img2dataset
```bash
# pip install img2dataset
img2dataset --url_list RealSyn100M/data \
        --input_format "parquet"\
        --url_col "raw_image_url" \
        --caption_col "text1" \
        --output_format webdataset \
        --output_folder RealSyn100M-webdataset \
        --processes_count 32 \
        --thread_count 64 \
        --image_size 224 \
        --resize_only_if_bigger=True \
        --resize_mode="keep_ratio" \
        --skip_reencode=True \
        --save_additional_columns '["text2","text3","syn_text"]' \
        --enable_wandb False
```