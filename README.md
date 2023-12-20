# ml-food-recommendation

![TensorFlow](https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
[![Google Colab](https://img.shields.io/badge/open_in_colab-blue?style=for-the-badge&logo=googlecolab&color=blue&labelColor=525252)](https://colab.research.google.com/github/MamMates/ml-food-recommendation/blob/main/MamMates_Food_Recommendation.ipynb)
![LICENSE](https://img.shields.io/github/license/MamMates/ml-food-recommendation?style=for-the-badge)
![Docker Version](https://img.shields.io/docker/v/putuwaw/mammates-food-recommendation/latest?style=for-the-badge)
![Docker Pulls](https://img.shields.io/docker/pulls/putuwaw/mammates-food-recommendation?style=for-the-badge)

Food Recommendation System using TensorFlow Recommenders (TFRS) and deployed using TensorFlow Serving.

Notebook: [MamMates Food Recommendation](https://colab.research.google.com/github/MamMates/ml-food-recommendation/blob/main/MamMates_Food_Recommendation.ipynb)

Dataset: [Food Recommendation Dataset (Dummy)](https://drive.google.com/drive/folders/1lAXsNMC32tJhOEQvpLHyNFP9VyZAux0O?usp=sharing)

## Features 💡

Using MamMates Food Recommendation, you can get food recommendation based on the given `id_user`.

## Prerequisites 📋

- [TensorFlow](https://www.tensorflow.org/) 2.14.0 or higher
- [TensorFlow Recommenders](https://www.tensorflow.org/recommenders) 0.7.3 or higher
- [Docker](https://www.docker.com/) 24.0.7 or higher

## Usage ✨

If you already have Docker installed, you only need to run the following command:

- Pull the image from Docker Hub:

```bash
docker pull putuwaw/mammates-food-recommendation
```

- Run the image:

```bash
docker run -p 8504:8504 --name ml-rec putuwaw/mammates-food-recommendation
```

- You can check that the model is already running by opening the browser and go to http://localhost:8504/v1/models/food_rec

- To do prediction, you can use the following command:

```bash
curl -s https://raw.githubusercontent.com/MamMates/ml-food-recommendation/main/example.json | curl -X POST -d @- http://localhost:8504/v1/models/food_rec:predict
```

- You will get the following response:

```json
{
  "predictions": [
    {
      "output_1": [
        1.59945917, 1.14119792, 0.741919041, 0.635785818, 0.532811046,
        0.467606097, 0.457192838, 0.0975963473, 0.017279733, -0.0865440145
      ],
      "output_2": ["13", "14", "12", "2", "18", "20", "11", "10", "7", "9"]
    }
  ]
}
```

## Development 💻

If you want to develop this model, you can follow the steps below:

- Clone this repository:

```bash
git clone https://github.com/MamMates/ml-food-recommendation.git
```

- Update the model by changing the saved model in the [model](model/) folder.

- Build the Docker image:

```bash
docker build -t mammates-food-recommendation .
```

- Run the image:

```bash
docker run -p 8504:8504 --name ml-rec mammates-food-recommendation
```

- You can check that the model is already running by opening browser and go to http://localhost:8504/v1/models/food_rec

- To do prediction, you can use the following command:

```bash
curl -d @example.json -X POST http://localhost:8504/v1/models/food_rec:predict
```

- To stop the container:

```bash
docker stop ml-rec
```

> [!NOTE]  
> If you want to learn more about TensorFlow Serving, you can read the REST API documentation [here](https://www.tensorflow.org/tfx/serving/api_rest).

## License 📝

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
