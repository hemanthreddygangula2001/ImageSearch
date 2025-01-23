# Image Similarity Search Project

## Overview

This Django project implements an image similarity search system using deep learning feature extraction with ResNet50. The project allows users to train on multiple image datasets and find similar images based on feature embeddings.

## Features

- Feature extraction using pre-trained ResNet50 model
- Support for multiple image datasets
- Nearest neighbor search for finding similar images
- Logging and error handling
- Flexible prediction across different datasets

## Project Structure

```
project_root/
│
├── dataset
│   ├── Category 1
│   ├── Category 2
│   ├── ...
│   └── ...
├── docker-compose.yaml
├── Dockerfile
├── imageFeatures
├── ImageSearchApp
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   ├── models.py
│   ├── prediction
│   ├── __pycache__
│   ├── serializers.py
│   ├── templates
│   ├── tests.py
│   ├── training
│   ├── urls.py
│   └── views.py
├── ImageSearchProject
│   ├── asgi.py
│   ├── __init__.py
│   ├── __pycache__
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── log
│   ├── prediction.log
│   └── training.log
├── manage.py
├── media
│   └── temp
└── requirements.txt

```

## Prerequisites

- Python 3.8+
- Django
- TensorFlow
- NumPy
- scikit-learn
- tqdm

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/hemanthreddygangula2001/ImageSearch.git
   cd ImageSearch
   ```

2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. Install required packages:
   ```bash
   pip install -r requirements.txt
   ```

## Configuration

1. Set the `base_path` in your Django settings to point to your project root
2. Ensure `DATASET_URL` is correctly configured in Django settings
3. Place your image datasets in the `dataset/` directory with subdirectories:
   - `dataset/category 1/`
   - `dataset/category 1/` and so on...
4. Add the categories in the settings as `DATASETS` list

## Training Process

To train the model and extract image features:

1. Initialize the `Training` class with your base path
2. Call the `train()` method to process images and extract features
3. Features will be saved in `imageFeatures/` directory

Example:
```python
from training import Training

trainer = Training(base_path='/path/to/project')
result = trainer.train(request={})
```

## Prediction Process

To find similar images:

1. Initialize the `Prediction` class
2. Use the `predict()` method with an image path
3. Optionally specify datasets and number of results

Example:
```python
from prediction import Prediction

predictor = Prediction(base_path='/path/to/project')
result = predictor.predict({
    'image_path': '/path/to/query/image.jpg',
    'num_results': 5,
    'datasets': [category 1, category 2]
})
```

## Logging

- Logs are stored in `log/training.log` and `log/prediction.log`
- Includes timestamps, log levels, and detailed error messages

## Error Handling

- Comprehensive error logging
- Graceful handling of missing datasets
- Feature extraction and prediction errors are logged

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Contact

Name - Hemanth Reddy Gangula

Email- hemanthreddygangula.2001@gmail.com


Project Link: [https://github.com/yourusername/image-similarity-search](https://github.com/hemanthreddygangula2001/ImageSearch)
