# COVID-19 ML Diagnostic tool

![Identify COVID-19 X-rays](https://i.imgur.com/b6Ek63F.jpg)

I have been exploring the potential of using machine learning in identifying #COVID19 cases using x-rays. Code & results are available at https://github.com/kornesh/covid19-diagnostic-tool

Radiologists currently do not recommend the use of CT-scans for COVID-19 detection as it’s hard to tell the difference between COVID-19 and common lung infections like bacterial or viral pneumonia [1](https://www.acr.org/Advocacy-and-Economics/ACR-Position-Statements/Recommendations-for-Chest-Radiography-and-CT-for-Suspected-COVID19-Infection) [2](https://car.ca/news/canadian-society-of-thoracic-radiology-and-canadian-association-of-radiologists-statement-on-covid-19/). AI could help us differentiate these fine nuances in matter of seconds. This machine learning model achieves 93.5% ± 5 accuracy in identifying COVID-19 and pneumonia cases using X-rays.

While the results are promising, this is merely a preliminary experiment and is not suitable for clinical diagnostics due to the limited crowdsourced dataset. We will need to concentrate our efforts on sourcing a quality dataset before we can consider such tools ready for clinical trials. I believe this will be a valuable tool to supplement understaffed radiology departments.

This experiment was inspired by [a study](https://www.medrxiv.org/content/10.1101/2020.02.14.20023028v4) in China which used CT-scans to train a machine learning model to screen patients for COVID-19. CT-scans are probably a better alternative for a dataset, since COVID-19 symptoms such as pulmonary nodules can be easily seen in a CT-scan than X-rays. Unfortunately, the publicly available dataset for this is even more limited. There is [a study](https://pubs.rsna.org/doi/10.1148/radiol.2020200642) that even suggests CT-scans are better for diagnostics than RT-PCR tests.

Automating the process of evaluating CT-scans/X-Rays for clinical diagnosis (or even helping radiologists to evaluate them faster) would allow us to do mass screening and will help us get out of this crisis.

I am looking for collaborators who are interested in building a clinical dataset or improving the performance and safety of the model. Do reach out to me.

## Model
- ResNet50 with [one-cycle policy](https://sgugger.github.io/the-1cycle-policy.html) and [progressive image resizing](https://www.fast.ai/2018/08/10/fastai-diu-imagenet/)
- Uses PyTorch and FastAI

## Dataset
- We're only using anteroposterior X-rays
- COVID-19 patients X-rays are [crowdsourced](https://github.com/ieee8023/covid-chestxray-dataset.git)
- Normal and pneumonia X-rays are selected from cohorts of pediatric patients from [Guangzhou Women and Children’s Medical Center](https://data.mendeley.com/datasets/rscbjbr9sj/2) (available on Kaggle)
- since the available dataset for COVID-19 is small, I made sure the distribution is balanced. ie equal number of X-rays for `normal`, `pneumonia` and `covid`

## Future work
- Experiment with EfficientNet and DenseNet
- Integrate image segmentation
- Fine tuning & improve dataset quality
