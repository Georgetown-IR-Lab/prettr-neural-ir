# Efficient Document Re-Ranking for Transformers by Precomputing Term Representations

Sean MacAvaney, Franco Maria Nardini, Raffaele Perego, Nicola Tonellotto, Nazli Goharian, and Ophir
Frieder. *Efficient Document Re-Ranking for Transformers by Precomputing Term Representations*. SIGIR 2020.

[PDF](https://arxiv.org/pdf/2004.14255.pdf)

## Code

Code to reproduce the results in the paper is found in [OpenNIR](https://github.com/Georgetown-IR-Lab/OpenNIR).

The PreTTR vocab is a drop-in replacement for a BERT-based vocab by setting: `vocab=prettr_bert`.

You can set the join layer with `vocab.join_layer=X` (where `X` is the layer where cross-attention begins). To enable compression, set `vocab.compress_size=X` (where `X` is typically `0` (no compression) `384`, `256`, or `128`, but can be anything). To enable FP16, set `vocab.compress_fp16=True`.

You can use pre-trained compressions using `vocab.bert_weights=X`, where `X` is a file name that exists in `~/data/onir/vocab/prettr_bert/`. We have a set of pre-trained compressors from CAR [here](#PreTrainedCompressors).

Set these *after* loading in the model configuration, such as `config/vanilla_bert vocab=prettr_bert ...`

## Citation

```
@inproceedings{macavaney:sigir2020-eff,
  author = {MacAvaney, Sean and Nardini, Franco Maria and Perego, Raffaele and Tonellotto, Nicola and Goharian, Nazli and Frieder, Ophir},
  title = {Efficient Document Re-Ranking for Transformers by Precomputing Term Representations},
  booktitle = {Proceedings of the 43rd International ACM SIGIR Conference on Research and Development in Information Retrieval},
  year = {2020}
}
```

### Pre-Trained Compressors

Download: [Google Drive](https://drive.google.com/file/d/1IMbbvkWko1-GnZUA_rYUcjumSHVA8Nht/view?usp=sharing) (21M)

*([Tip for downloading large Google Drive files using wget](https://medium.com/@acpanjan/download-google-drive-files-using-wget-3c2c025a8b99))*

| File Name    | join_layer | compress_size | MD5                                |
|--------------|------------|---------------|------------------------------------|
| `car.10.128` |         10 |           128 | `1efa63621216c3e2322b2fcec4524917` |
| `car.10.256` |         10 |           256 | `be3be7f8680fa7ffae842acaf2999b71` |
| `car.10.384` |         10 |           384 | `5eac1cc55d8a9b71c83da8c6c2fbc890` |
| `car.11.128` |         11 |           128 | `6f87029d7802e64e855a45a081e45068` |
| `car.11.256` |         11 |           256 | `eec1592077c39e93be0c4ef74f0981a0` |
| `car.11.384` |         11 |           384 | `074e57afef603dfb24b0344f613744d6` |
| `car.7.128`  |          7 |           128 | `02b659407375f634835ab610fbe5db1a` |
| `car.7.256`  |          7 |           256 | `d2ca951bd09a69db716cf97e24ad606c` |
| `car.7.384`  |          7 |           384 | `85fde69e6a6a21e213ee054354343b74` |
| `car.8.128`  |          8 |           128 | `b7490664cf042b33dc29988920db9167` |
| `car.8.256`  |          8 |           256 | `a8923b7669a6f091d060007e8bff9bf5` |
| `car.8.384`  |          8 |           384 | `2b42a6beb65e76390b762a53140bc774` |
| `car.9.128`  |          9 |           128 | `a3ae7780b18a2f00509cc4671530c716` |
| `car.9.256`  |          9 |           256 | `9202a3bea49cf70dd859f6bd0b77dbe8` |
| `car.9.384`  |          9 |           384 | `8b8547e55abe4c12c78c4b946de39adc` |
