# COVID-19 ML Diagnostic tool

- Achieves 90% ± 5 accuracy using PA X-rays. This is merely a preliminary experiment and is *not* suitable for clinical diagnostic due to limited, crowdsourced dataset
- Automating the process of evaluating CT-scans/X-Rays for clinical diagnosis, or at least helping radiologist to evaluate them faster would allow us to do mass screening and get out of this crisis faster
- Inspired by [a study in China](https://www.medrxiv.org/content/10.1101/2020.02.14.20023028v4) which uses CT scans and machine learning to screen patients for covid-19. CT-scans are probably a better option for dataset, since covid-19 symptoms such as pulmonary nodules can be easily seen in a CT scan than X-rays. Unfortunately, this dataset is even more limited.
- Also, there's [a study](https://pubs.rsna.org/doi/10.1148/radiol.2020200642) that suggests that CT scans are better for diagnostics than RT-PCR tests.

## Model
- ResNet50 with [one-cycle policy](https://sgugger.github.io/the-1cycle-policy.html) and [progressive image resizing](https://www.fast.ai/2018/08/10/fastai-diu-imagenet/)
- Uses pytorch and fastai

## Dataset
- only using anteroposterior x-rays
- covid19 patients x-rays are [crowdsourced](https://github.com/ieee8023/covid-chestxray-dataset.git)
- normal and pneumonia x-rays are selected from cohorts of pediatric patients from [Guangzhou Women and Children’s Medical Center](https://data.mendeley.com/datasets/rscbjbr9sj/2) (available on Kaggle)
- since the available dataset for COVID-19 is small, I made sure the distribution is balanced. ie equal number of x-rays for `normal`, `pneumonia` and `covid`

## Future work
- Experiment with efficientnet and densenet
- Integrate image segmentation
- Fine tuning & improve dataset quality
