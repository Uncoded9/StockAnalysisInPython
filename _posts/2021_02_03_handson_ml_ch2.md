{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "name": "2021-02-03-handson_ml_ch2",
      "provenance": [],
      "authorship_tag": "ABX9TyOjmqXps8sCHONDv6KlPNtm",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/Uncoded9/StockAnalysisInPython/blob/master/_posts/2021_02_03_handson_ml_ch2.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "CM3acPDKQbRx"
      },
      "source": [
        "---\n",
        "title: Chapter 2\n",
        "layout: post\n",
        "categories: [ML, Python]\n",
        "image: /assets/img/logo.jpg\n",
        "description: \"Welcome to Hands on ML chapter 2\"\n",
        "---\n",
        "\n"
      ]
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "xXtx7xqEPEq2"
      },
      "source": [
        "## 1. 데이터 다운로드"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "OSKNwwP-I3u_"
      },
      "source": [
        "import os\n",
        "import tarfile\n",
        "import urllib.request"
      ],
      "execution_count": 15,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "y4msunEPJAxP"
      },
      "source": [
        "DOWNLOAD_ROOT = \"https://raw.githubusercontent.com/rickiepark/handson-ml2/master/\"\n",
        "HOUSING_PATH = os.path.join(\"datasets\", \"housing\")\n",
        "HOUSING_URL = DOWNLOAD_ROOT + \"datasets/housing/housing.tgz\"\n",
        "\n",
        "def fetch_housing_data(housing_url=HOUSING_URL, housing_path=HOUSING_PATH):\n",
        "    if not os.path.isdir(housing_path):\n",
        "        os.makedirs(housing_path)  # housing_path가 없다면 directory 생성 (/datasets/housing)\n",
        "    tgz_path = os.path.join(housing_path, \"housing.tgz\") \n",
        "    urllib.request.urlretrieve(housing_url, tgz_path) # tgz_path에 파일다운로드\n",
        "    housing_tgz = tarfile.open(tgz_path)\n",
        "    housing_tgz.extractall(path=housing_path)\n",
        "    housing_tgz.close()"
      ],
      "execution_count": 16,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "K52lUwjsKWO2"
      },
      "source": [
        "fetch_housing_data()"
      ],
      "execution_count": 17,
      "outputs": []
    },
    {
      "cell_type": "code",
      "metadata": {
        "id": "_mleUEG-KPuT"
      },
      "source": [
        "import pandas as pd\n",
        "\n",
        "def load_housing_data(housing_path=HOUSING_PATH):\n",
        "    csv_path = os.path.join(housing_path, \"housing.csv\") \n",
        "    return pd.read_csv(csv_path) # housing_path에 있는 csv file을 dataframe으로 읽어오기 "
      ],
      "execution_count": 18,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "vkQHTCx0LoOg"
      },
      "source": [
        "## 2. 데이터 구조 훑어보기"
      ]
    },
    {
      "cell_type": "code",
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 165
        },
        "id": "kXUg0H_VK8UC",
        "outputId": "e3e2673a-dc8b-47f8-e25d-49f737a769e2"
      },
      "source": [
        "housing = load_housing_data()\n",
        "housing.head().to_markdown() # 데이터의 처음 5행 확인"
      ],
      "execution_count": 21,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "string"
            },
            "text/plain": [
              "'|    |   longitude |   latitude |   housing_median_age |   total_rooms |   total_bedrooms |   population |   households |   median_income |   median_house_value | ocean_proximity   |\\n|---:|------------:|-----------:|---------------------:|--------------:|-----------------:|-------------:|-------------:|----------------:|---------------------:|:------------------|\\n|  0 |     -122.23 |      37.88 |                   41 |           880 |              129 |          322 |          126 |          8.3252 |               452600 | NEAR BAY          |\\n|  1 |     -122.22 |      37.86 |                   21 |          7099 |             1106 |         2401 |         1138 |          8.3014 |               358500 | NEAR BAY          |\\n|  2 |     -122.24 |      37.85 |                   52 |          1467 |              190 |          496 |          177 |          7.2574 |               352100 | NEAR BAY          |\\n|  3 |     -122.25 |      37.85 |                   52 |          1274 |              235 |          558 |          219 |          5.6431 |               341300 | NEAR BAY          |\\n|  4 |     -122.25 |      37.85 |                   52 |          1627 |              280 |          565 |          259 |          3.8462 |               342200 | NEAR BAY          |'"
            ]
          },
          "metadata": {
            "tags": []
          },
          "execution_count": 21
        }
      ]
    }
  ]
}