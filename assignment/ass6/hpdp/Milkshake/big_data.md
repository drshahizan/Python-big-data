{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
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
        "<a href=\"https://colab.research.google.com/github/drshahizan/Python-big-data/blob/main/assignment/ass6/hpdp/Milkshake/big_data.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "## Assignment 6\n",
        "\n",
        "- Group Name : MilkShake\n",
        "- Group Member :\n",
        " - Nurunnajwa binti Zulkifli A21EC0121\n",
        " - Nur Shuhada Safiah binti Ayob A21EC0114\n",
        "-Date : 17 December 2023\n"
      ],
      "metadata": {
        "id": "_6IcbUM4E90X"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "\n",
        "---\n",
        "\n"
      ],
      "metadata": {
        "id": "f8-APGzWHybl"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "### 1. Pick a Big Dataset\n",
        "\n",
        "Start by choosing a suitable dataset. Choose a dataset from reputable sources such as Kaggle, UCI Machine Learning Repository, or any other pertinent dataset repository. Make sure it's big—over 700 MB."
      ],
      "metadata": {
        "id": "1u06XUgGHBSi"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Our dataset is [Spotify Chart](https://www.kaggle.com/datasets/dhruvildave/spotify-charts).\n",
        "\n",
        "This is a complete dataset of all the \"Top 200\" and \"Viral 50\" charts published globally by Spotify. Spotify publishes a new chart every 2-3 days. This is its entire collection since January 1, 2017.\n",
        "\n"
      ],
      "metadata": {
        "id": "jWrLlCZtHG0U"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "\n",
        "---\n",
        "\n"
      ],
      "metadata": {
        "id": "5KZUAMQHIMkx"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "###2. Loading the Dataset\n",
        "Use Python and Pandas to load your chosen dataset into your Colab notebook. You can either upload it from your computer or directly from an online source."
      ],
      "metadata": {
        "id": "xoq_VDRmITue"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Kaggle Setup:**\n",
        "\n",
        "- We install the Kaggle package, create a directory named .kaggle in the home directory"
      ],
      "metadata": {
        "id": "aLjvV_h-p7gt"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "! pip install kaggle"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "hqqld_n0ITC-",
        "outputId": "dc0e02d4-e8b2-4cd6-e214-04052c0a90f7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Requirement already satisfied: kaggle in /usr/local/lib/python3.10/dist-packages (1.5.16)\n",
            "Requirement already satisfied: six>=1.10 in /usr/local/lib/python3.10/dist-packages (from kaggle) (1.16.0)\n",
            "Requirement already satisfied: certifi in /usr/local/lib/python3.10/dist-packages (from kaggle) (2023.11.17)\n",
            "Requirement already satisfied: python-dateutil in /usr/local/lib/python3.10/dist-packages (from kaggle) (2.8.2)\n",
            "Requirement already satisfied: requests in /usr/local/lib/python3.10/dist-packages (from kaggle) (2.31.0)\n",
            "Requirement already satisfied: tqdm in /usr/local/lib/python3.10/dist-packages (from kaggle) (4.66.1)\n",
            "Requirement already satisfied: python-slugify in /usr/local/lib/python3.10/dist-packages (from kaggle) (8.0.1)\n",
            "Requirement already satisfied: urllib3 in /usr/local/lib/python3.10/dist-packages (from kaggle) (2.0.7)\n",
            "Requirement already satisfied: bleach in /usr/local/lib/python3.10/dist-packages (from kaggle) (6.1.0)\n",
            "Requirement already satisfied: webencodings in /usr/local/lib/python3.10/dist-packages (from bleach->kaggle) (0.5.1)\n",
            "Requirement already satisfied: text-unidecode>=1.3 in /usr/local/lib/python3.10/dist-packages (from python-slugify->kaggle) (1.3)\n",
            "Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.10/dist-packages (from requests->kaggle) (3.3.2)\n",
            "Requirement already satisfied: idna<4,>=2.5 in /usr/local/lib/python3.10/dist-packages (from requests->kaggle) (3.6)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- We copy the Kaggle API key file (kaggle.json) to the .kaggle directory , and set the appropriate permissions on the key file."
      ],
      "metadata": {
        "id": "voooQCOqqMh4"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "! mkdir ~/.kaggle"
      ],
      "metadata": {
        "id": "98DH-aPNVd4Y",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "a6bec4ae-0791-4f89-c8d4-58fc81bec131"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "mkdir: cannot create directory ‘/root/.kaggle’: File exists\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "!  cp /content/kaggle.json ~/.kaggle/"
      ],
      "metadata": {
        "id": "erz6lBiuVisZ"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "! chmod 600 ~/.kaggle/kaggle.json"
      ],
      "metadata": {
        "id": "m5PQ8aUrV4pJ"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Download Dataset:**\n",
        "\n",
        "- This line command uses the Kaggle API to download the dataset named \"spotify-charts\" from Kaggle."
      ],
      "metadata": {
        "id": "2qr3nl-rqb4f"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "! kaggle datasets download dhruvildave/spotify-charts"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "CU9DgGl9V7L_",
        "outputId": "7a872df7-65fe-4a91-c6dc-48cc1f35a0c2"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "spotify-charts.zip: Skipping, found more recently modified local copy (use --force to force download)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Modin Installation:**\n",
        "\n",
        "- The code installs the Modin library along with its dependencies using !pip install modin[all].\n",
        "\n",
        "- Modin is a library designed to accelerate and scale up pandas workflows by parallelizing and optimizing the underlying computations."
      ],
      "metadata": {
        "id": "qIH1TVOWqlxE"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "!pip install modin[all]"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "HU_DrRvnliSF",
        "outputId": "c85e1bf1-1c2b-404d-b059-edc68abea8c7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Requirement already satisfied: modin[all] in /usr/local/lib/python3.10/dist-packages (0.26.0)\n",
            "Requirement already satisfied: pandas<2.2,>=2.1 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2.1.4)\n",
            "Requirement already satisfied: packaging>=21.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (23.2)\n",
            "Requirement already satisfied: numpy>=1.22.4 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (1.23.5)\n",
            "Requirement already satisfied: fsspec>=2022.05.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2023.6.0)\n",
            "Requirement already satisfied: psutil>=5.8.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (5.9.5)\n",
            "Requirement already satisfied: dask>=2.22.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2023.8.1)\n",
            "Requirement already satisfied: distributed>=2.22.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2023.8.1)\n",
            "Requirement already satisfied: ray[default]!=2.5.0,>=1.13.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2.8.1)\n",
            "Requirement already satisfied: pyarrow>=7.0.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (10.0.1)\n",
            "Requirement already satisfied: pydantic<2 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (1.10.13)\n",
            "Requirement already satisfied: modin-spreadsheet>=0.1.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (0.1.2)\n",
            "Requirement already satisfied: click>=8.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (8.1.7)\n",
            "Requirement already satisfied: cloudpickle>=1.5.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (2.2.1)\n",
            "Requirement already satisfied: partd>=1.2.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (1.4.1)\n",
            "Requirement already satisfied: pyyaml>=5.3.1 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (6.0.1)\n",
            "Requirement already satisfied: toolz>=0.10.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (0.12.0)\n",
            "Requirement already satisfied: importlib-metadata>=4.13.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (7.0.0)\n",
            "Requirement already satisfied: jinja2>=2.10.3 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (3.1.2)\n",
            "Requirement already satisfied: locket>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (1.0.0)\n",
            "Requirement already satisfied: msgpack>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (1.0.7)\n",
            "Requirement already satisfied: sortedcontainers>=2.0.5 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (2.4.0)\n",
            "Requirement already satisfied: tblib>=1.6.0 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (3.0.0)\n",
            "Requirement already satisfied: tornado>=6.0.4 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (6.3.2)\n",
            "Requirement already satisfied: urllib3>=1.24.3 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (2.0.7)\n",
            "Requirement already satisfied: zict>=2.2.0 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (3.0.0)\n",
            "Requirement already satisfied: jupyter>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from modin-spreadsheet>=0.1.0->modin[all]) (1.0.0)\n",
            "Requirement already satisfied: notebook>=6.0.3 in /usr/local/lib/python3.10/dist-packages (from modin-spreadsheet>=0.1.0->modin[all]) (6.5.5)\n",
            "Requirement already satisfied: ipywidgets>=7.0.0 in /usr/local/lib/python3.10/dist-packages (from modin-spreadsheet>=0.1.0->modin[all]) (7.7.1)\n",
            "Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.10/dist-packages (from pandas<2.2,>=2.1->modin[all]) (2.8.2)\n",
            "Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.10/dist-packages (from pandas<2.2,>=2.1->modin[all]) (2023.3.post1)\n",
            "Requirement already satisfied: tzdata>=2022.1 in /usr/local/lib/python3.10/dist-packages (from pandas<2.2,>=2.1->modin[all]) (2023.3)\n",
            "Requirement already satisfied: typing-extensions>=4.2.0 in /usr/local/lib/python3.10/dist-packages (from pydantic<2->modin[all]) (4.5.0)\n",
            "Requirement already satisfied: filelock in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.13.1)\n",
            "Requirement already satisfied: jsonschema in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (4.19.2)\n",
            "Requirement already satisfied: protobuf!=3.19.5,>=3.15.3 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.20.3)\n",
            "Requirement already satisfied: aiosignal in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.3.1)\n",
            "Requirement already satisfied: frozenlist in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.4.0)\n",
            "Requirement already satisfied: requests in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (2.31.0)\n",
            "Requirement already satisfied: aiohttp>=3.7 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.9.1)\n",
            "Requirement already satisfied: aiohttp-cors in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.7.0)\n",
            "Requirement already satisfied: colorful in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.5.5)\n",
            "Requirement already satisfied: py-spy>=0.2.0 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.3.14)\n",
            "Requirement already satisfied: gpustat>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.1.1)\n",
            "Requirement already satisfied: opencensus in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.11.3)\n",
            "Requirement already satisfied: prometheus-client>=0.7.1 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.19.0)\n",
            "Requirement already satisfied: smart-open in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (6.4.0)\n",
            "Requirement already satisfied: virtualenv<20.21.1,>=20.0.24 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (20.21.0)\n",
            "Requirement already satisfied: grpcio>=1.42.0 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.60.0)\n",
            "Requirement already satisfied: attrs>=17.3.0 in /usr/local/lib/python3.10/dist-packages (from aiohttp>=3.7->ray[default]!=2.5.0,>=1.13.0->modin[all]) (23.1.0)\n",
            "Requirement already satisfied: multidict<7.0,>=4.5 in /usr/local/lib/python3.10/dist-packages (from aiohttp>=3.7->ray[default]!=2.5.0,>=1.13.0->modin[all]) (6.0.4)\n",
            "Requirement already satisfied: yarl<2.0,>=1.0 in /usr/local/lib/python3.10/dist-packages (from aiohttp>=3.7->ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.9.4)\n",
            "Requirement already satisfied: async-timeout<5.0,>=4.0 in /usr/local/lib/python3.10/dist-packages (from aiohttp>=3.7->ray[default]!=2.5.0,>=1.13.0->modin[all]) (4.0.3)\n",
            "Requirement already satisfied: nvidia-ml-py>=11.450.129 in /usr/local/lib/python3.10/dist-packages (from gpustat>=1.0.0->ray[default]!=2.5.0,>=1.13.0->modin[all]) (12.535.133)\n",
            "Requirement already satisfied: blessed>=1.17.1 in /usr/local/lib/python3.10/dist-packages (from gpustat>=1.0.0->ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.20.0)\n",
            "Requirement already satisfied: zipp>=0.5 in /usr/local/lib/python3.10/dist-packages (from importlib-metadata>=4.13.0->dask>=2.22.0->modin[all]) (3.17.0)\n",
            "Requirement already satisfied: ipykernel>=4.5.1 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (5.5.6)\n",
            "Requirement already satisfied: ipython-genutils~=0.2.0 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.2.0)\n",
            "Requirement already satisfied: traitlets>=4.3.1 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (5.7.1)\n",
            "Requirement already satisfied: widgetsnbextension~=3.6.0 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (3.6.6)\n",
            "Requirement already satisfied: ipython>=4.0.0 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (7.34.0)\n",
            "Requirement already satisfied: jupyterlab-widgets>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (3.0.9)\n",
            "Requirement already satisfied: MarkupSafe>=2.0 in /usr/local/lib/python3.10/dist-packages (from jinja2>=2.10.3->distributed>=2.22.0->modin[all]) (2.1.3)\n",
            "Requirement already satisfied: qtconsole in /usr/local/lib/python3.10/dist-packages (from jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (5.5.1)\n",
            "Requirement already satisfied: jupyter-console in /usr/local/lib/python3.10/dist-packages (from jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (6.1.0)\n",
            "Requirement already satisfied: nbconvert in /usr/local/lib/python3.10/dist-packages (from jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (6.5.4)\n",
            "Requirement already satisfied: pyzmq<25,>=17 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (23.2.1)\n",
            "Requirement already satisfied: argon2-cffi in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (23.1.0)\n",
            "Requirement already satisfied: jupyter-core>=4.6.1 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (5.5.0)\n",
            "Requirement already satisfied: jupyter-client<8,>=5.3.4 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (6.1.12)\n",
            "Requirement already satisfied: nbformat in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (5.9.2)\n",
            "Requirement already satisfied: nest-asyncio>=1.5 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.5.8)\n",
            "Requirement already satisfied: Send2Trash>=1.8.0 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.8.2)\n",
            "Requirement already satisfied: terminado>=0.8.3 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (0.18.0)\n",
            "Requirement already satisfied: nbclassic>=0.4.7 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.0.0)\n",
            "Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.10/dist-packages (from python-dateutil>=2.8.2->pandas<2.2,>=2.1->modin[all]) (1.16.0)\n",
            "Requirement already satisfied: distlib<1,>=0.3.6 in /usr/local/lib/python3.10/dist-packages (from virtualenv<20.21.1,>=20.0.24->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.3.8)\n",
            "Requirement already satisfied: platformdirs<4,>=2.4 in /usr/local/lib/python3.10/dist-packages (from virtualenv<20.21.1,>=20.0.24->ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.11.0)\n",
            "Requirement already satisfied: jsonschema-specifications>=2023.03.6 in /usr/local/lib/python3.10/dist-packages (from jsonschema->ray[default]!=2.5.0,>=1.13.0->modin[all]) (2023.11.2)\n",
            "Requirement already satisfied: referencing>=0.28.4 in /usr/local/lib/python3.10/dist-packages (from jsonschema->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.32.0)\n",
            "Requirement already satisfied: rpds-py>=0.7.1 in /usr/local/lib/python3.10/dist-packages (from jsonschema->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.13.2)\n",
            "Requirement already satisfied: opencensus-context>=0.1.3 in /usr/local/lib/python3.10/dist-packages (from opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.1.3)\n",
            "Requirement already satisfied: google-api-core<3.0.0,>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (2.11.1)\n",
            "Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.10/dist-packages (from requests->ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.3.2)\n",
            "Requirement already satisfied: idna<4,>=2.5 in /usr/local/lib/python3.10/dist-packages (from requests->ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.6)\n",
            "Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.10/dist-packages (from requests->ray[default]!=2.5.0,>=1.13.0->modin[all]) (2023.11.17)\n",
            "Requirement already satisfied: wcwidth>=0.1.4 in /usr/local/lib/python3.10/dist-packages (from blessed>=1.17.1->gpustat>=1.0.0->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.2.12)\n",
            "Requirement already satisfied: googleapis-common-protos<2.0.dev0,>=1.56.2 in /usr/local/lib/python3.10/dist-packages (from google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.62.0)\n",
            "Requirement already satisfied: google-auth<3.0.dev0,>=2.14.1 in /usr/local/lib/python3.10/dist-packages (from google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (2.17.3)\n",
            "Requirement already satisfied: setuptools>=18.5 in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (67.7.2)\n",
            "Requirement already satisfied: jedi>=0.16 in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.19.1)\n",
            "Requirement already satisfied: decorator in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (4.4.2)\n",
            "Requirement already satisfied: pickleshare in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.7.5)\n",
            "Requirement already satisfied: prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0 in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (3.0.43)\n",
            "Requirement already satisfied: pygments in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (2.16.1)\n",
            "Requirement already satisfied: backcall in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.2.0)\n",
            "Requirement already satisfied: matplotlib-inline in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.1.6)\n",
            "Requirement already satisfied: pexpect>4.3 in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (4.9.0)\n",
            "Requirement already satisfied: jupyter-server>=1.8 in /usr/local/lib/python3.10/dist-packages (from nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.24.0)\n",
            "Requirement already satisfied: notebook-shim>=0.2.3 in /usr/local/lib/python3.10/dist-packages (from nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (0.2.3)\n",
            "Requirement already satisfied: lxml in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (4.9.3)\n",
            "Requirement already satisfied: beautifulsoup4 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (4.11.2)\n",
            "Requirement already satisfied: bleach in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (6.1.0)\n",
            "Requirement already satisfied: defusedxml in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.7.1)\n",
            "Requirement already satisfied: entrypoints>=0.2.2 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.4)\n",
            "Requirement already satisfied: jupyterlab-pygments in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.3.0)\n",
            "Requirement already satisfied: mistune<2,>=0.8.1 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.8.4)\n",
            "Requirement already satisfied: nbclient>=0.5.0 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.9.0)\n",
            "Requirement already satisfied: pandocfilters>=1.4.1 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (1.5.0)\n",
            "Requirement already satisfied: tinycss2 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (1.2.1)\n",
            "Requirement already satisfied: fastjsonschema in /usr/local/lib/python3.10/dist-packages (from nbformat->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (2.19.0)\n",
            "Requirement already satisfied: ptyprocess in /usr/local/lib/python3.10/dist-packages (from terminado>=0.8.3->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (0.7.0)\n",
            "Requirement already satisfied: argon2-cffi-bindings in /usr/local/lib/python3.10/dist-packages (from argon2-cffi->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (21.2.0)\n",
            "Requirement already satisfied: qtpy>=2.4.0 in /usr/local/lib/python3.10/dist-packages (from qtconsole->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (2.4.1)\n",
            "Requirement already satisfied: cachetools<6.0,>=2.0.0 in /usr/local/lib/python3.10/dist-packages (from google-auth<3.0.dev0,>=2.14.1->google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (5.3.2)\n",
            "Requirement already satisfied: pyasn1-modules>=0.2.1 in /usr/local/lib/python3.10/dist-packages (from google-auth<3.0.dev0,>=2.14.1->google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.3.0)\n",
            "Requirement already satisfied: rsa<5,>=3.1.4 in /usr/local/lib/python3.10/dist-packages (from google-auth<3.0.dev0,>=2.14.1->google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (4.9)\n",
            "Requirement already satisfied: parso<0.9.0,>=0.8.3 in /usr/local/lib/python3.10/dist-packages (from jedi>=0.16->ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.8.3)\n",
            "Requirement already satisfied: anyio<4,>=3.1.0 in /usr/local/lib/python3.10/dist-packages (from jupyter-server>=1.8->nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (3.7.1)\n",
            "Requirement already satisfied: websocket-client in /usr/local/lib/python3.10/dist-packages (from jupyter-server>=1.8->nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.7.0)\n",
            "Requirement already satisfied: cffi>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from argon2-cffi-bindings->argon2-cffi->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.16.0)\n",
            "Requirement already satisfied: soupsieve>1.2 in /usr/local/lib/python3.10/dist-packages (from beautifulsoup4->nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (2.5)\n",
            "Requirement already satisfied: webencodings in /usr/local/lib/python3.10/dist-packages (from bleach->nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.5.1)\n",
            "Requirement already satisfied: sniffio>=1.1 in /usr/local/lib/python3.10/dist-packages (from anyio<4,>=3.1.0->jupyter-server>=1.8->nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.3.0)\n",
            "Requirement already satisfied: exceptiongroup in /usr/local/lib/python3.10/dist-packages (from anyio<4,>=3.1.0->jupyter-server>=1.8->nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.2.0)\n",
            "Requirement already satisfied: pycparser in /usr/local/lib/python3.10/dist-packages (from cffi>=1.0.1->argon2-cffi-bindings->argon2-cffi->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (2.21)\n",
            "Requirement already satisfied: pyasn1<0.6.0,>=0.4.6 in /usr/local/lib/python3.10/dist-packages (from pyasn1-modules>=0.2.1->google-auth<3.0.dev0,>=2.14.1->google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.5.1)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Import Libraries:**\n",
        "\n",
        "- The code imports Modin pandas as pd, zipfile, and os modules for working with files and directories."
      ],
      "metadata": {
        "id": "VFqhOi4QrBQ3"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "import modin.pandas as pd"
      ],
      "metadata": {
        "id": "4JyUGYXQmmeR"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "import zipfile\n",
        "import os"
      ],
      "metadata": {
        "id": "Dc1q0J1uWmTQ"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Unzip Dataset:**\n",
        "\n",
        "- The code unzips the downloaded dataset using the zipfile module. The contents are extracted into a directory named 'spotify-charts'.\n",
        "\n",
        "**List Extracted Files:**\n",
        "\n",
        "- It lists the files present in the 'spotify-charts' directory."
      ],
      "metadata": {
        "id": "fRaUXAEerj87"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Path to the downloaded zip file\n",
        "zip_file_path = 'spotify-charts.zip'\n",
        "\n",
        "# Directory to extract the contents of the zip file\n",
        "extracted_dir = 'spotify-charts'\n",
        "\n",
        "# Unzip the file\n",
        "with zipfile.ZipFile(zip_file_path, 'r') as zip_ref:\n",
        "    zip_ref.extractall(extracted_dir)\n",
        "\n",
        "# List the files in the extracted directory\n",
        "extracted_files = os.listdir(extracted_dir)"
      ],
      "metadata": {
        "id": "reiUVd01Xz4l"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Select and read CSV File:**\n",
        "\n",
        "- It filters and selects the CSV file from the list of extracted files.\n",
        "\n",
        "- The code reads the selected CSV file into a Modin DataFrame using pd.read_csv()."
      ],
      "metadata": {
        "id": "HQTDDWNErMhT"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "csv_file = [file for file in extracted_files if file.endswith('.csv')][0]\n",
        "df = pd.read_csv(os.path.join(extracted_dir, csv_file))"
      ],
      "metadata": {
        "id": "rUxsaUGlYYBT",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "100abf36-68ae-4494-9215-693c763daaf6"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "UserWarning: Ray execution environment not yet initialized. Initializing...\n",
            "To remove this warning, run the following python code before doing dataframe operations:\n",
            "\n",
            "    import ray\n",
            "    ray.init()\n",
            "\n",
            "UserWarning: The size of /dev/shm is too small (6133121024 bytes). The required size at least half of RAM (6804721664 bytes). Please, delete files in /dev/shm or increase size of /dev/shm with --shm-size in Docker. Also, you can can override the memory size for each Ray worker (in bytes) to the MODIN_MEMORY environment variable.\n",
            "2023-12-17 06:59:10,172\tINFO worker.py:1673 -- Started a local Ray instance.\n",
            "2023-12-17 07:00:42,177\tWARNING worker.py:2074 -- A worker died or was killed while executing a task by an unexpected system error. To troubleshoot the problem, check the logs for the dead worker. RayTask ID: 7bfe64c6d51abdce372e54081152d1f4fc00961201000000 Worker ID: be18a379cc5c2e4ddb7fb6370efca6022e1b6a86eb227ce75b744310 Node ID: ab372961f69c4b91ac399b9fd2b83d625dc596605f4390198be1fad6 Worker IP address: 172.28.0.12 Worker port: 35803 Worker PID: 65040 Worker exit type: SYSTEM_ERROR Worker exit detail: Worker unexpectedly exits with a connection error code 2. End of file. There are some potential root causes. (1) The process is killed by SIGKILL by OOM killer due to high memory usage. (2) ray stop --force is called. (3) The worker is crashed unexpectedly due to SIGSEGV or other unexpected errors.\n",
            "\u001b[33m(raylet)\u001b[0m [2023-12-17 07:01:10,094 E 64995 64995] (raylet) node_manager.cc:3035: 1 Workers (tasks / actors) killed due to memory pressure (OOM), 0 Workers crashed due to other reasons at node (ID: ab372961f69c4b91ac399b9fd2b83d625dc596605f4390198be1fad6, IP: 172.28.0.12) over the last time period. To see more information about the Workers killed on this node, use `ray logs raylet.out -ip 172.28.0.12`\n",
            "\u001b[33m(raylet)\u001b[0m \n",
            "\u001b[33m(raylet)\u001b[0m Refer to the documentation on how to address the out of memory issue: https://docs.ray.io/en/latest/ray-core/scheduling/ray-oom-prevention.html. Consider provisioning more memory on this node or reducing task parallelism by requesting more CPUs per task. To adjust the kill threshold, set the environment variable `RAY_memory_usage_threshold` when starting Ray. To disable worker killing, set the environment variable `RAY_memory_monitor_refresh_ms` to zero.\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# Display the DataFrame\n",
        "df.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 399
        },
        "id": "UTceNbkmY3yU",
        "outputId": "33fec201-7e7a-42fa-ac27-7538e58e5cd0"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                         title  rank        date  \\\n",
              "0      Chantaje (feat. Maluma)     1  2017-01-01   \n",
              "1  Vente Pa' Ca (feat. Maluma)     2  2017-01-01   \n",
              "2   Reggaetón Lento (Bailemos)     3  2017-01-01   \n",
              "3                       Safari     4  2017-01-01   \n",
              "4                  Shaky Shaky     5  2017-01-01   \n",
              "\n",
              "                                  artist  \\\n",
              "0                                Shakira   \n",
              "1                           Ricky Martin   \n",
              "2                                   CNCO   \n",
              "3  J Balvin, Pharrell Williams, BIA, Sky   \n",
              "4                           Daddy Yankee   \n",
              "\n",
              "                                                 url     region   chart  \\\n",
              "0  https://open.spotify.com/track/6mICuAdrwEjh6Y6...  Argentina  top200   \n",
              "1  https://open.spotify.com/track/7DM4BPaS7uofFul...  Argentina  top200   \n",
              "2  https://open.spotify.com/track/3AEZUABDXNtecAO...  Argentina  top200   \n",
              "3  https://open.spotify.com/track/6rQSrBHf7HlZjtc...  Argentina  top200   \n",
              "4  https://open.spotify.com/track/58IL315gMSTD37D...  Argentina  top200   \n",
              "\n",
              "           trend   streams  \n",
              "0  SAME_POSITION  253019.0  \n",
              "1        MOVE_UP  223988.0  \n",
              "2      MOVE_DOWN  210943.0  \n",
              "3  SAME_POSITION  173865.0  \n",
              "4        MOVE_UP  153956.0  "
            ],
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>url</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>trend</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Chantaje (feat. Maluma)</td>\n",
              "      <td>1</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Shakira</td>\n",
              "      <td>https://open.spotify.com/track/6mICuAdrwEjh6Y6...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>SAME_POSITION</td>\n",
              "      <td>253019.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Vente Pa' Ca (feat. Maluma)</td>\n",
              "      <td>2</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Ricky Martin</td>\n",
              "      <td>https://open.spotify.com/track/7DM4BPaS7uofFul...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_UP</td>\n",
              "      <td>223988.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Reggaetón Lento (Bailemos)</td>\n",
              "      <td>3</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>CNCO</td>\n",
              "      <td>https://open.spotify.com/track/3AEZUABDXNtecAO...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>210943.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Safari</td>\n",
              "      <td>4</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>J Balvin, Pharrell Williams, BIA, Sky</td>\n",
              "      <td>https://open.spotify.com/track/6rQSrBHf7HlZjtc...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>SAME_POSITION</td>\n",
              "      <td>173865.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Shaky Shaky</td>\n",
              "      <td>5</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Daddy Yankee</td>\n",
              "      <td>https://open.spotify.com/track/58IL315gMSTD37D...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_UP</td>\n",
              "      <td>153956.0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ]
          },
          "metadata": {},
          "execution_count": 12
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "df.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "DBHySUhDpv6q",
        "outputId": "03674939-2fb1-4202-9f9c-59fc6c28781b"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'modin.pandas.dataframe.DataFrame'>\n",
            "RangeIndex: 26173514 entries, 0 to 26173513\n",
            "Data columns (total 9 columns):\n",
            " #   Column   Dtype  \n",
            "---  ------   -----  \n",
            " 0   title    object \n",
            " 1   rank     int64  \n",
            " 2   date     object \n",
            " 3   artist   object \n",
            " 4   url      object \n",
            " 5   region   object \n",
            " 6   chart    object \n",
            " 7   trend    object \n",
            " 8   streams  float64\n",
            "dtypes: float64(1), int64(1), object(7)\n",
            "memory usage: 1.8+ GB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Data columns:**\n",
        "\n",
        "- The DataFrame has 9 columns.\n",
        "\n",
        "**Columns and Data Types:**\n",
        "\n",
        "- **title**: Object type, representing the title of songs.\n",
        "- **rank**: Int64 type, representing the rank.\n",
        "- **date**: Object type,  representing dates.\n",
        "- **artist**: Object type, representing the artist associated with the data.\n",
        "- **url**: Object type, representing URLs.\n",
        "- **region**: Object type, representing a region.\n",
        "- **chart**: Object type, representing the song's chart.\n",
        "- **trend**: Object type, indicating the song position\n",
        "- **streams**: Float64 type, representing streaming data.\n",
        "\n",
        "**Memory Usage:**\n",
        "\n",
        "- The dataset occupies approximately 1.8 gigabytes of memory."
      ],
      "metadata": {
        "id": "Fc2GH_v5sJqM"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "##### **Measure memory usage, computation time, and file size**"
      ],
      "metadata": {
        "id": "uXu0ay36rB7q"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "pip install psutil"
      ],
      "metadata": {
        "id": "dJa2n54krIZp",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "b3618429-b056-4f93-a313-f04e9ba1dec6"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Requirement already satisfied: psutil in /usr/local/lib/python3.10/dist-packages (5.9.5)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import time\n",
        "import os\n",
        "import psutil\n",
        "import pandas as pd\n",
        "\n",
        "# Record start time\n",
        "start_time = time.time()\n",
        "\n",
        "# Record end time\n",
        "end_time = time.time()\n",
        "\n",
        "# Calculate the time taken\n",
        "load_time = end_time - start_time\n",
        "\n",
        "# Print the time taken\n",
        "print(f\"Time taken to load the data: {load_time} seconds\")\n",
        "\n",
        "# Get memory usage\n",
        "memory_usage = psutil.Process(os.getpid()).memory_info().rss\n",
        "print(f\"Memory usage: {memory_usage / (1024 * 1024):.2f} MB\")\n",
        "\n",
        "# Get file size\n",
        "file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB\n",
        "print(f\"File size: {file_size:.2f} MB\")\n",
        "\n",
        "# Additional computation or analysis can be done on the loaded data here\n",
        "\n",
        "# Remember to free up memory if you're done using the DataFrame\n",
        "df = None\n",
        "\n",
        "# Optionally, you can print CPU usage as well\n",
        "cpu_percent = psutil.cpu_percent()\n",
        "print(f\"CPU Usage: {cpu_percent}%\")\n"
      ],
      "metadata": {
        "id": "rFSnTJKsrQsj",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "1033becb-a757-455d-d401-9f588945930b"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Time taken to load the data: 4.029273986816406e-05 seconds\n",
            "Memory usage: 194.75 MB\n",
            "File size: 3322.10 MB\n",
            "CPU Usage: 67.9%\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "\n",
        "---\n",
        "\n"
      ],
      "metadata": {
        "id": "DbDjpgDwJaQY"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "### 3. Strategies for Big Datasets\n",
        "\n",
        "Apply five smart strategies to handle large datasets effectively"
      ],
      "metadata": {
        "id": "2nqtVcDRIXY7"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "#### 3.1 Load Less Data:\n",
        "\n",
        "Strategically load only the essential portions of the dataset to optimize memory usage.\n"
      ],
      "metadata": {
        "id": "F9DkOgC1IdMK"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Specify column of interest**\n",
        "\n",
        "- We focused on to primary column such as title, rank, date, artist, region, streams and chart. You can find out the details of each columns on above."
      ],
      "metadata": {
        "id": "s5yR1FBa27lW"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Specify columns of interest\n",
        "columns_of_interest = ['title', 'rank', 'date', 'artist', 'region','streams','chart']"
      ],
      "metadata": {
        "id": "NZ22L2ksRaGR"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "- We load 100,000 rows here and read the dataset."
      ],
      "metadata": {
        "id": "FKcJUWHx3NfX"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "subset_size = 1000000"
      ],
      "metadata": {
        "id": "hwxkHnNJAM2V"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "-  We reads a subset of the CSV file with the specified columns and rows."
      ],
      "metadata": {
        "id": "RaetBbjzBxoR"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "df = pd.read_csv(\n",
        "    os.path.join(extracted_dir, csv_file),\n",
        "    usecols=columns_of_interest,\n",
        "    nrows=subset_size\n",
        ")\n"
      ],
      "metadata": {
        "id": "YC3wqVOecAdq",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "42e390fe-21ab-4b50-c81b-43c736727dff"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "UserWarning: `read_*` implementation has mismatches with pandas:\n",
            "Data types of partitions are different! Please refer to the troubleshooting section of the Modin documentation to fix this issue.\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "##### Measure memory usage, computation time, and file size"
      ],
      "metadata": {
        "id": "0GjQWxJMDID6"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "\n",
        "# Record end time\n",
        "end_time = time.time()\n",
        "\n",
        "# Calculate the time taken\n",
        "load_time = end_time - start_time\n",
        "\n",
        "# Print the time taken\n",
        "print(f\"Time taken to load the data: {load_time} seconds\")\n",
        "\n",
        "# Get memory usage\n",
        "memory_usage = psutil.Process(os.getpid()).memory_info().rss\n",
        "print(f\"Memory usage: {memory_usage / (1024 * 1024):.2f} MB\")\n",
        "\n",
        "# Get file size\n",
        "file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB\n",
        "print(f\"File size: {file_size:.2f} MB\")\n",
        "\n",
        "# Additional computation or analysis can be done on the loaded data here\n",
        "\n",
        "# Remember to free up memory if you're done using the DataFrame\n",
        "df = None\n",
        "\n",
        "# Optionally, you can print CPU usage as well\n",
        "cpu_percent = psutil.cpu_percent()\n",
        "print(f\"CPU Usage: {cpu_percent}%\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "y37WkSGGAjiT",
        "outputId": "c7314f0d-c0e5-477c-decb-e8900e2fd1fc"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Time taken to load the data: 2.546340227127075 seconds\n",
            "Memory usage: 342.62 MB\n",
            "File size: 3322.10 MB\n",
            "CPU Usage: 60.2%\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Drop duplicates row."
      ],
      "metadata": {
        "id": "QtyuqSxT3a8v"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Dealing with Duplicates\n",
        "df.drop_duplicates(inplace=True)\n"
      ],
      "metadata": {
        "id": "OkHpPmH7m6C0"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Replaces missing values in numeric columns with the mean and in string columns with the mode."
      ],
      "metadata": {
        "id": "qgoTNpcHCOv0"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Replace missing values with mean for numeric columns\n",
        "import numpy as np\n",
        "\n",
        "numeric_cols = df.select_dtypes(include=np.number).columns\n",
        "df[numeric_cols] = df[numeric_cols].fillna(df[numeric_cols].mean())"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "fXKGI1ml_kh1",
        "outputId": "e7b5f406-945b-41ba-dc35-4ceb7462042c"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "UserWarning: `DataFrame.setitem_unhashable_key` is not currently supported by PandasOnRay, defaulting to pandas implementation.\n",
            "Please refer to https://modin.readthedocs.io/en/stable/supported_apis/defaulting_to_pandas.html for explanation.\n",
            "UserWarning: Distributing <class 'pandas.core.frame.DataFrame'> object. This may take some time.\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Replaces missing values in object columns with the mean and in string columns with the mode."
      ],
      "metadata": {
        "id": "q5Q8o8k1CQlc"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Replace missing values with mode for string columns in the subset\n",
        "string_cols = df.select_dtypes(include='object').columns\n",
        "df[string_cols] = df[string_cols].fillna(df[string_cols].mode().iloc[0])"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "8G6saM9qA08H",
        "outputId": "7b08d78e-1c14-4b30-98be-8f05e78d8ac8"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "UserWarning: `DataFrame.setitem_unhashable_key` is not currently supported by PandasOnRay, defaulting to pandas implementation.\n",
            "UserWarning: Distributing <class 'pandas.core.frame.DataFrame'> object. This may take some time.\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "df['date'] = pd.to_datetime(df['date'])\n",
        "\n",
        "df.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Z1qrXWSDwxLf",
        "outputId": "40c21619-0c20-407d-dbb9-29e6e20d1cb7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'modin.pandas.dataframe.DataFrame'>\n",
            "RangeIndex: 1000000 entries, 0 to 999999\n",
            "Data columns (total 7 columns):\n",
            " #   Column   Non-Null Count    Dtype         \n",
            "---  ------   --------------    -----         \n",
            " 0   title    1000000 non-null  object        \n",
            " 1   rank     1000000 non-null  int64         \n",
            " 2   date     1000000 non-null  datetime64[ns]\n",
            " 3   artist   1000000 non-null  object        \n",
            " 4   region   1000000 non-null  object        \n",
            " 5   chart    1000000 non-null  object        \n",
            " 6   streams  1000000 non-null  float64       \n",
            "dtypes: datetime64[ns](1), float64(1), int64(1), object(4)\n",
            "memory usage: 53.4+ MB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- This dataset contain year from 2017 - 2021"
      ],
      "metadata": {
        "id": "p0FUv-IcDBC9"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "unique_years = df['date'].dt.year.unique()\n",
        "\n",
        "# Display the unique years\n",
        "print(unique_years)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "11aueAS3Cu5-",
        "outputId": "37bad667-c235-4e5e-e120-d061941b3e27"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "[2017 2018 2020 2019 2021]\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Here, we only focus to Malaysia region and chart top200 from 2017 - 2021."
      ],
      "metadata": {
        "id": "I0_T5kosCb9V"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "spotify_my_top200 = df[(df['region'] == 'Malaysia') & (df['chart'] == 'top200')]\n",
        "\n",
        "spotify_my_top200.head()\n"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "bg06xmfi9Lqq",
        "outputId": "a0db025b-06bc-461c-c2a8-87e2e12cffb7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                     title  rank       date                    artist  \\\n",
              "4755                 Mercy    23 2017-01-01              Shawn Mendes   \n",
              "4784                Closer     1 2017-01-01  The Chainsmokers, Halsey   \n",
              "4785  Say You Won't Let Go     2 2017-01-01              James Arthur   \n",
              "4786               Starboy     3 2017-01-01     The Weeknd, Daft Punk   \n",
              "4787       Let Me Love You     4 2017-01-01   DJ Snake, Justin Bieber   \n",
              "\n",
              "        region   chart  streams  \n",
              "4755  Malaysia  top200  12925.0  \n",
              "4784  Malaysia  top200  27062.0  \n",
              "4785  Malaysia  top200  26577.0  \n",
              "4786  Malaysia  top200  24878.0  \n",
              "4787  Malaysia  top200  22310.0  "
            ],
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>4755</th>\n",
              "      <td>Mercy</td>\n",
              "      <td>23</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Shawn Mendes</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>12925.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4784</th>\n",
              "      <td>Closer</td>\n",
              "      <td>1</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>The Chainsmokers, Halsey</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>27062.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4785</th>\n",
              "      <td>Say You Won't Let Go</td>\n",
              "      <td>2</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>James Arthur</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>26577.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4786</th>\n",
              "      <td>Starboy</td>\n",
              "      <td>3</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>The Weeknd, Daft Punk</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>24878.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4787</th>\n",
              "      <td>Let Me Love You</td>\n",
              "      <td>4</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>DJ Snake, Justin Bieber</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>22310.0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ]
          },
          "metadata": {},
          "execution_count": 21
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "spotify_my_top200.tail()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "C19XwATDcE0s",
        "outputId": "899e7ae9-175c-4658-be3f-545a86e07f50"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                  title  rank       date          artist  \\\n",
              "998838                     Bodak Yellow   196 2018-02-13         Cardi B   \n",
              "998839  Bartier Cardi (feat. 21 Savage)   197 2018-02-13         Cardi B   \n",
              "998840         2U (feat. Justin Bieber)   198 2018-02-13    David Guetta   \n",
              "998841                Berakhirlah Sudah   199 2018-02-13       Atmosfera   \n",
              "998842                She Loves Control   200 2018-02-13  Camila Cabello   \n",
              "\n",
              "          region   chart  streams  \n",
              "998838  Malaysia  top200   4412.0  \n",
              "998839  Malaysia  top200   4410.0  \n",
              "998840  Malaysia  top200   4401.0  \n",
              "998841  Malaysia  top200   4400.0  \n",
              "998842  Malaysia  top200   4389.0  "
            ],
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>998838</th>\n",
              "      <td>Bodak Yellow</td>\n",
              "      <td>196</td>\n",
              "      <td>2018-02-13</td>\n",
              "      <td>Cardi B</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>4412.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>998839</th>\n",
              "      <td>Bartier Cardi (feat. 21 Savage)</td>\n",
              "      <td>197</td>\n",
              "      <td>2018-02-13</td>\n",
              "      <td>Cardi B</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>4410.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>998840</th>\n",
              "      <td>2U (feat. Justin Bieber)</td>\n",
              "      <td>198</td>\n",
              "      <td>2018-02-13</td>\n",
              "      <td>David Guetta</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>4401.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>998841</th>\n",
              "      <td>Berakhirlah Sudah</td>\n",
              "      <td>199</td>\n",
              "      <td>2018-02-13</td>\n",
              "      <td>Atmosfera</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>4400.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>998842</th>\n",
              "      <td>She Loves Control</td>\n",
              "      <td>200</td>\n",
              "      <td>2018-02-13</td>\n",
              "      <td>Camila Cabello</td>\n",
              "      <td>Malaysia</td>\n",
              "      <td>top200</td>\n",
              "      <td>4389.0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ]
          },
          "metadata": {},
          "execution_count": 22
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "spotify_my_top200.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "DgYTjj8LeZR7",
        "outputId": "ab7063ca-7f29-4a26-a8e6-52e44485522c"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'modin.pandas.dataframe.DataFrame'>\n",
            "Index: 16902 entries, 4755 to 998842\n",
            "Data columns (total 7 columns):\n",
            " #   Column   Non-Null Count  Dtype         \n",
            "---  ------   --------------  -----         \n",
            " 0   title    16902 non-null  object        \n",
            " 1   rank     16902 non-null  int64         \n",
            " 2   date     16902 non-null  datetime64[ns]\n",
            " 3   artist   16902 non-null  object        \n",
            " 4   region   16902 non-null  object        \n",
            " 5   chart    16902 non-null  object        \n",
            " 6   streams  16902 non-null  float64       \n",
            "dtypes: datetime64[ns](1), float64(1), int64(1), object(4)\n",
            "memory usage: 1.0+ MB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "##### Measure memory usage, computation time, and file size"
      ],
      "metadata": {
        "id": "joppKD3WYRCd"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "!pip install psutil"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "aAVsuE5w7qlu",
        "outputId": "2d436b57-c964-406f-bfa6-4c4f05d5fb60"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Requirement already satisfied: psutil in /usr/local/lib/python3.10/dist-packages (5.9.5)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import psutil"
      ],
      "metadata": {
        "id": "lSp-J9v-7tdq"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Record end time\n",
        "end_time = time.time()\n",
        "\n",
        "# Calculate the time taken\n",
        "load_time = end_time - start_time\n",
        "\n",
        "# Print the time taken\n",
        "print(f\"Time taken to load the data: {load_time} seconds\")\n",
        "\n",
        "# Get memory usage\n",
        "memory_usage = psutil.Process(os.getpid()).memory_info().rss\n",
        "print(f\"Memory usage: {memory_usage / (1024 * 1024):.2f} MB\")\n",
        "\n",
        "# Get file size\n",
        "file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB\n",
        "print(f\"File size: {file_size:.2f} MB\")\n",
        "\n",
        "# Additional computation or analysis can be done on the loaded data here\n",
        "\n",
        "# Remember to free up memory if you're done using the DataFrame\n",
        "df = None\n",
        "\n",
        "# Optionally, you can print CPU usage as well\n",
        "cpu_percent = psutil.cpu_percent()\n",
        "print(f\"CPU Usage: {cpu_percent}%\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "jQ5Y9MZiA33L",
        "outputId": "f298f874-cddd-4459-cd1d-b9565781c547"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Time taken to load the data: 196.5192108154297 seconds\n",
            "Memory usage: 413.34 MB\n",
            "File size: 3322.10 MB\n",
            "CPU Usage: 19.7%\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "The entire DataFrame is reported to consume approximately 1.0+ MB of memory. This indicates that the data is relatively small and should be manageable for analysis and exploration."
      ],
      "metadata": {
        "id": "zaDI9UBy4NWp"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "#### 3.2 Use Chunking\n",
        "Process the data in smaller pieces to avoid memory issues.\n"
      ],
      "metadata": {
        "id": "gf2J7DVsIodN"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Import Modules**\n",
        "\n",
        "- We import the necessary modules (os and pandas as pd) to help with file operations and data processing.\n",
        "\n",
        "- 'os'  provides a way to interact with the operating system, in this case, to join file paths."
      ],
      "metadata": {
        "id": "tYditx9R6SSI"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "import os"
      ],
      "metadata": {
        "id": "LRHwNZ6AJCzM"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Set Chunk Size:**\n",
        "\n",
        "- We decide to process the data in smaller parts, called chunks. Each chunk contains 100,000 rows of data."
      ],
      "metadata": {
        "id": "Q-9FBDN96bWy"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Chunk size\n",
        "chunk_size = 100000"
      ],
      "metadata": {
        "id": "khdyqqvxdJOf"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Create Storage for Processed Data:**\n",
        "\n",
        "We create an empty list (chunks) to store the processed parts of the dataset."
      ],
      "metadata": {
        "id": "rQOuKTRN6f31"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Initialize an empty list to store chunks\n",
        "chunks = []"
      ],
      "metadata": {
        "id": "ISftzCa86nlv"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Read the Dataset:**\n",
        "\n",
        "- We read a large dataset from a file, selecting only the columns we're interested in."
      ],
      "metadata": {
        "id": "ZEfZfX3j6tjA"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "df = pd.read_csv(os.path.join(extracted_dir, csv_file), usecols=columns_of_interest)"
      ],
      "metadata": {
        "id": "GCS_S8X5dM4T"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "##### Measure memory usage, computation time, and file size"
      ],
      "metadata": {
        "id": "DLoZFqXyDjqp"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Record end time\n",
        "end_time = time.time()\n",
        "\n",
        "# Calculate the time taken\n",
        "load_time = end_time - start_time\n",
        "\n",
        "# Print the time taken\n",
        "print(f\"Time taken to load the data: {load_time} seconds\")\n",
        "\n",
        "# Get memory usage\n",
        "memory_usage = psutil.Process(os.getpid()).memory_info().rss\n",
        "print(f\"Memory usage: {memory_usage / (1024 * 1024):.2f} MB\")\n",
        "\n",
        "# Get file size\n",
        "file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB\n",
        "print(f\"File size: {file_size:.2f} MB\")\n",
        "\n",
        "# Optionally, you can print CPU usage as well\n",
        "cpu_percent = psutil.cpu_percent()\n",
        "print(f\"CPU Usage: {cpu_percent}%\")\n",
        "\n",
        "# Additional computation or analysis can be done on the loaded data here\n",
        "\n",
        "# Remember to free up memory if you're done using the DataFrame\n",
        "df = None"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "zFoVZ2KpCSW1",
        "outputId": "4453f139-d7ba-45a4-86b1-0ee62ea28c7e"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Time taken to load the data: 267.078076839447 seconds\n",
            "Memory usage: 3656.25 MB\n",
            "File size: 3322.10 MB\n",
            "CPU Usage: 69.2%\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Process Data in Chunks:**\n",
        "\n",
        "- We go through the dataset in chunks, processing one chunk at a time.\n",
        "For each chunk, we filter out rows where the 'rank' is greater than 10.\n",
        "\n",
        "- We store each processed chunk in the chunks list."
      ],
      "metadata": {
        "id": "2sZmveds6xKR"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Process the data in chunks using iloc\n",
        "start_idx = 0\n",
        "while start_idx < len(df):\n",
        "    end_idx = start_idx + chunk_size\n",
        "    processed_chunk = df.iloc[start_idx:end_idx]\n",
        "\n",
        "    processed_chunk = processed_chunk[processed_chunk['rank'] <= 10]  # Filter rows where rank is less than or equal to 10\n",
        "\n",
        "    # Store the processed chunk in the list\n",
        "    chunks.append(processed_chunk)\n",
        "\n",
        "    start_idx = end_idx\n"
      ],
      "metadata": {
        "id": "wyHR_bDke8EP"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Combine Processed Chunks:**\n",
        "\n",
        "Finally, we combine all the processed chunks into a single dataset (result_df)."
      ],
      "metadata": {
        "id": "q_iz_FQG7BAO"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Concatenate the processed chunks into a single DataFrame\n",
        "result_df = pd.concat(chunks, ignore_index=True)"
      ],
      "metadata": {
        "id": "8G_7V9gefFmm"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Result of chunk:**"
      ],
      "metadata": {
        "id": "bNP-sDx17GID"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "result_df.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "ubvX1GwUlInK",
        "outputId": "1cc63ad6-9d50-4e65-d046-a60e452171e3"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 4543752 entries, 0 to 4543751\n",
            "Data columns (total 7 columns):\n",
            " #   Column   Dtype  \n",
            "---  ------   -----  \n",
            " 0   title    object \n",
            " 1   rank     int64  \n",
            " 2   date     object \n",
            " 3   artist   object \n",
            " 4   region   object \n",
            " 5   chart    object \n",
            " 6   streams  float64\n",
            "dtypes: float64(1), int64(1), object(5)\n",
            "memory usage: 242.7+ MB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "result_df.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "v8kkGb9wliCd",
        "outputId": "cb74c178-03d0-4fd1-bb53-d48e6c3e6739"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                         title  rank        date  \\\n",
              "0      Chantaje (feat. Maluma)     1  2017-01-01   \n",
              "1  Vente Pa' Ca (feat. Maluma)     2  2017-01-01   \n",
              "2   Reggaetón Lento (Bailemos)     3  2017-01-01   \n",
              "3                       Safari     4  2017-01-01   \n",
              "4                  Shaky Shaky     5  2017-01-01   \n",
              "\n",
              "                                  artist     region   chart   streams  \n",
              "0                                Shakira  Argentina  top200  253019.0  \n",
              "1                           Ricky Martin  Argentina  top200  223988.0  \n",
              "2                                   CNCO  Argentina  top200  210943.0  \n",
              "3  J Balvin, Pharrell Williams, BIA, Sky  Argentina  top200  173865.0  \n",
              "4                           Daddy Yankee  Argentina  top200  153956.0  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-9fc5682c-db53-451b-b9e8-2623219cc86b\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Chantaje (feat. Maluma)</td>\n",
              "      <td>1</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Shakira</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>253019.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Vente Pa' Ca (feat. Maluma)</td>\n",
              "      <td>2</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Ricky Martin</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>223988.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Reggaetón Lento (Bailemos)</td>\n",
              "      <td>3</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>CNCO</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>210943.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Safari</td>\n",
              "      <td>4</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>J Balvin, Pharrell Williams, BIA, Sky</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>173865.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Shaky Shaky</td>\n",
              "      <td>5</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Daddy Yankee</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>153956.0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-9fc5682c-db53-451b-b9e8-2623219cc86b')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-9fc5682c-db53-451b-b9e8-2623219cc86b button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-9fc5682c-db53-451b-b9e8-2623219cc86b');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-af7ec76d-464a-4612-878e-eab4e9e25d5b\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-af7ec76d-464a-4612-878e-eab4e9e25d5b')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-af7ec76d-464a-4612-878e-eab4e9e25d5b button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "    </div>\n",
              "  </div>\n"
            ]
          },
          "metadata": {},
          "execution_count": 59
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "result_df.tail()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "0bj6QvPDlqhh",
        "outputId": "0efc2ac2-a5c9-4e62-80e5-8bcc17695f47"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                               title  rank        date  \\\n",
              "4543747                              Giấc Mơ Rất Thơ     5  2021-07-31   \n",
              "4543748                                 Nevertheless     6  2021-07-31   \n",
              "4543749  Your Sunday (Sunday Morning) [feat. Ampoff]     7  2021-07-31   \n",
              "4543750                                We're Already     8  2021-07-31   \n",
              "4543751                    Happy For You (feat. Vũ.)     9  2021-07-31   \n",
              "\n",
              "                artist   region    chart  streams  \n",
              "4543747  Mer, thaison!  Vietnam  viral50      NaN  \n",
              "4543748      Night Off  Vietnam  viral50      NaN  \n",
              "4543749     Sunny Shin  Vietnam  viral50      NaN  \n",
              "4543750      KIMMUSEUM  Vietnam  viral50      NaN  \n",
              "4543751   Lukas Graham  Vietnam  viral50      NaN  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-0da5f383-159e-4c15-9c92-8eaab1121da7\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>4543747</th>\n",
              "      <td>Giấc Mơ Rất Thơ</td>\n",
              "      <td>5</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Mer, thaison!</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4543748</th>\n",
              "      <td>Nevertheless</td>\n",
              "      <td>6</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Night Off</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4543749</th>\n",
              "      <td>Your Sunday (Sunday Morning) [feat. Ampoff]</td>\n",
              "      <td>7</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Sunny Shin</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4543750</th>\n",
              "      <td>We're Already</td>\n",
              "      <td>8</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>KIMMUSEUM</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4543751</th>\n",
              "      <td>Happy For You (feat. Vũ.)</td>\n",
              "      <td>9</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Lukas Graham</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-0da5f383-159e-4c15-9c92-8eaab1121da7')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-0da5f383-159e-4c15-9c92-8eaab1121da7 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-0da5f383-159e-4c15-9c92-8eaab1121da7');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-80660003-61b5-491d-897d-56bbb518c4fe\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-80660003-61b5-491d-897d-56bbb518c4fe')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-80660003-61b5-491d-897d-56bbb518c4fe button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "    </div>\n",
              "  </div>\n"
            ]
          },
          "metadata": {},
          "execution_count": 60
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Replace NaN with mean**\n",
        "- We can see that the dataframe above have NaN value. Therefore, we decide to replace it with mean."
      ],
      "metadata": {
        "id": "sbZAiYun7POa"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Calculate the mean of the 'streams' column (excluding NaN values)\n",
        "mean_streams = result_df['streams'].mean()\n",
        "\n",
        "# Fill NaN values in the 'streams' column with the mean value\n",
        "result_df['streams'].fillna(mean_streams, inplace=True)"
      ],
      "metadata": {
        "id": "_rt-r0fbmEPO"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Result :**"
      ],
      "metadata": {
        "id": "BCl8EUg27k09"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "result_df.tail()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 293
        },
        "id": "ZF5Rwiu8mJuM",
        "outputId": "7824bd46-72f5-4f9b-ccd9-f007fc606f1a"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                               title  rank        date  \\\n",
              "4543747                              Giấc Mơ Rất Thơ     5  2021-07-31   \n",
              "4543748                                 Nevertheless     6  2021-07-31   \n",
              "4543749  Your Sunday (Sunday Morning) [feat. Ampoff]     7  2021-07-31   \n",
              "4543750                                We're Already     8  2021-07-31   \n",
              "4543751                    Happy For You (feat. Vũ.)     9  2021-07-31   \n",
              "\n",
              "                artist   region    chart        streams  \n",
              "4543747  Mer, thaison!  Vietnam  viral50  172593.778362  \n",
              "4543748      Night Off  Vietnam  viral50  172593.778362  \n",
              "4543749     Sunny Shin  Vietnam  viral50  172593.778362  \n",
              "4543750      KIMMUSEUM  Vietnam  viral50  172593.778362  \n",
              "4543751   Lukas Graham  Vietnam  viral50  172593.778362  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-877bf1f8-074d-4ee6-ad83-209af25b34f8\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>4543747</th>\n",
              "      <td>Giấc Mơ Rất Thơ</td>\n",
              "      <td>5</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Mer, thaison!</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>172593.778362</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4543748</th>\n",
              "      <td>Nevertheless</td>\n",
              "      <td>6</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Night Off</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>172593.778362</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4543749</th>\n",
              "      <td>Your Sunday (Sunday Morning) [feat. Ampoff]</td>\n",
              "      <td>7</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Sunny Shin</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>172593.778362</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4543750</th>\n",
              "      <td>We're Already</td>\n",
              "      <td>8</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>KIMMUSEUM</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>172593.778362</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4543751</th>\n",
              "      <td>Happy For You (feat. Vũ.)</td>\n",
              "      <td>9</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Lukas Graham</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>172593.778362</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-877bf1f8-074d-4ee6-ad83-209af25b34f8')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-877bf1f8-074d-4ee6-ad83-209af25b34f8 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-877bf1f8-074d-4ee6-ad83-209af25b34f8');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-207e11ce-41bf-46df-a6b3-2d43d060c19f\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-207e11ce-41bf-46df-a6b3-2d43d060c19f')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-207e11ce-41bf-46df-a6b3-2d43d060c19f button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "    </div>\n",
              "  </div>\n"
            ]
          },
          "metadata": {},
          "execution_count": 62
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- The NaN value has been replaced with mean value"
      ],
      "metadata": {
        "id": "5jZb9kr9Pe7B"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "#### 3.3 Optimize Data Types\n",
        "Fine-tune data types to maximize efficiency and minimize memory consumption.\n"
      ],
      "metadata": {
        "id": "nXh0oAKgIsir"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "result_df.info()"
      ],
      "metadata": {
        "id": "fLKbVOxmJDRm",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "a37e5301-ee05-4d45-95b7-716c1328e96e"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "RangeIndex: 4543752 entries, 0 to 4543751\n",
            "Data columns (total 7 columns):\n",
            " #   Column   Dtype  \n",
            "---  ------   -----  \n",
            " 0   title    object \n",
            " 1   rank     int64  \n",
            " 2   date     object \n",
            " 3   artist   object \n",
            " 4   region   object \n",
            " 5   chart    object \n",
            " 6   streams  float64\n",
            "dtypes: float64(1), int64(1), object(5)\n",
            "memory usage: 242.7+ MB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "##### Measure memory usage, computation time, and file size"
      ],
      "metadata": {
        "id": "jVnLTpCjDxte"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Record start time\n",
        "start_time = time.time()\n",
        "\n",
        "# Read the data using Pandas\n",
        "result_df = pd.read_csv(\n",
        "    os.path.join(extracted_dir, csv_file),\n",
        "    usecols=columns_of_interest\n",
        ")\n",
        "\n",
        "# Record end time\n",
        "end_time = time.time()\n",
        "\n",
        "# Calculate the time taken\n",
        "load_time = end_time - start_time\n",
        "\n",
        "# Print the time taken\n",
        "print(f\"Time taken to load the data: {load_time} seconds\")\n",
        "\n",
        "# Get memory usage\n",
        "memory_usage = psutil.Process(os.getpid()).memory_info().rss\n",
        "print(f\"Memory usage: {memory_usage / (1024 * 1024):.2f} MB\")\n",
        "\n",
        "# Get file size\n",
        "file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB\n",
        "print(f\"File size: {file_size:.2f} MB\")\n",
        "\n",
        "# Optionally, you can print CPU usage as well\n",
        "cpu_percent = psutil.cpu_percent()\n",
        "print(f\"CPU Usage: {cpu_percent}%\")\n",
        "\n",
        "# Additional computation or analysis can be done on the loaded data here\n",
        "\n",
        "# Remember to free up memory if you're done using the DataFrame\n",
        "result_df = None"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "6KbWWHZgDysF",
        "outputId": "4c597ac5-9f7d-440b-933a-761509bf4eac"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Time taken to load the data: 72.01772570610046 seconds\n",
            "Memory usage: 5784.59 MB\n",
            "File size: 3322.10 MB\n",
            "CPU Usage: 52.1%\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Select Rank column**\n",
        "-  Downcasts the numeric values to the smallest integer type that can safely represent them. In this case, it downcasts from int64 to int16, saving memory."
      ],
      "metadata": {
        "id": "GenlPswU78_6"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "result_df['rank'] = pd.to_numeric(result_df['rank'], downcast='integer')  # Convert int64 to int16"
      ],
      "metadata": {
        "id": "W4d4k9_l0-KK"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Select Stream column**\n",
        "\n",
        "-  Downcasts the numeric values to the smallest floating-point type that can safely represent them. In this case, it downcasts from float64 to float, saving memory."
      ],
      "metadata": {
        "id": "EchbU3a88OFS"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "result_df['streams'] = pd.to_numeric(result_df['streams'], downcast='float')  # Convert float64 to float"
      ],
      "metadata": {
        "id": "5HScL7pQ1ieZ"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Select Date column**\n",
        "\n",
        "-  We converts the values in the selected column to datetime format. If a value cannot be converted to datetime, it will be set to NaT (Not a Time).\n",
        "\n",
        "- If there are errors in conversion, set the problematic values to NaT."
      ],
      "metadata": {
        "id": "OQqFOy358XjM"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Convert 'date' to datetime if it's not already\n",
        "result_df['date'] = pd.to_datetime(result_df['date'], errors='coerce')"
      ],
      "metadata": {
        "id": "0s82Uybq1Zqo"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Result:**"
      ],
      "metadata": {
        "id": "9Qypb8YO8i7c"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Display data types and memory usage after optimization\n",
        "result_df.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "to9VWDwI1jxg",
        "outputId": "3a101291-3b1a-48fb-f0dd-3a0342e3c024"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'modin.pandas.dataframe.DataFrame'>\n",
            "RangeIndex: 2271876 entries, 0 to 2271875\n",
            "Data columns (total 7 columns):\n",
            " #   Column   Dtype         \n",
            "---  ------   -----         \n",
            " 0   title    object        \n",
            " 1   rank     int8          \n",
            " 2   date     datetime64[ns]\n",
            " 3   artist   object        \n",
            " 4   region   object        \n",
            " 5   chart    object        \n",
            " 6   streams  float64       \n",
            "dtypes: datetime64[ns](1), float64(1), int8(1), object(4)\n",
            "memory usage: 101.8+ MB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "result_df.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "NwjvBi492Ifg",
        "outputId": "bb5c6e73-0427-4f1a-b3e7-04b9f8177d17"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                         title  rank       date  \\\n",
              "0      Chantaje (feat. Maluma)     1 2017-01-01   \n",
              "1  Vente Pa' Ca (feat. Maluma)     2 2017-01-01   \n",
              "2   Reggaetón Lento (Bailemos)     3 2017-01-01   \n",
              "3                       Safari     4 2017-01-01   \n",
              "4                  Shaky Shaky     5 2017-01-01   \n",
              "\n",
              "                                  artist     region   chart   streams  \n",
              "0                                Shakira  Argentina  top200  253019.0  \n",
              "1                           Ricky Martin  Argentina  top200  223988.0  \n",
              "2                                   CNCO  Argentina  top200  210943.0  \n",
              "3  J Balvin, Pharrell Williams, BIA, Sky  Argentina  top200  173865.0  \n",
              "4                           Daddy Yankee  Argentina  top200  153956.0  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-f6cf3800-dc0b-4850-9e18-18d4bd9396e8\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Chantaje (feat. Maluma)</td>\n",
              "      <td>1</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Shakira</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>253019.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Vente Pa' Ca (feat. Maluma)</td>\n",
              "      <td>2</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Ricky Martin</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>223988.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Reggaetón Lento (Bailemos)</td>\n",
              "      <td>3</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>CNCO</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>210943.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Safari</td>\n",
              "      <td>4</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>J Balvin, Pharrell Williams, BIA, Sky</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>173865.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Shaky Shaky</td>\n",
              "      <td>5</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Daddy Yankee</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>153956.0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-f6cf3800-dc0b-4850-9e18-18d4bd9396e8')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-f6cf3800-dc0b-4850-9e18-18d4bd9396e8 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-f6cf3800-dc0b-4850-9e18-18d4bd9396e8');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-4bdc6813-4130-4d02-93ab-ea8d87c40757\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-4bdc6813-4130-4d02-93ab-ea8d87c40757')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-4bdc6813-4130-4d02-93ab-ea8d87c40757 button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "    </div>\n",
              "  </div>\n"
            ]
          },
          "metadata": {},
          "execution_count": 68
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "#### 3.4 Sampling\n",
        "Implement sampling methodologies to extract meaningful insights from a subset of the dataset.\n"
      ],
      "metadata": {
        "id": "blJUSISSIv-l"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Randomly select a fraction row from the DataFrame**\n",
        "\n",
        "-  Here, we specifies that we want to sample 10% of the total rows. You can adjust this percentage based on your needs.\n",
        "\n",
        "- We also sets a random seed for reproducibility (random_state=42) . Using the same seed ensures that if you run the code again, you'll get the same set of randomly selected rows."
      ],
      "metadata": {
        "id": "MMbmejkG81E0"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Sample a fraction of the DataFrame (e.g., 10%)\n",
        "sampled_df = result_df.sample(frac=0.1, random_state=42)"
      ],
      "metadata": {
        "id": "MHKJHGPKJDv3"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Result:**"
      ],
      "metadata": {
        "id": "7cSORzzY9fRD"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Display the info after sampling\n",
        "print(sampled_df.info())"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "khsAxH--2giZ",
        "outputId": "de0b4ef5-940d-48f4-88fc-a8d4537b47e5"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'modin.pandas.dataframe.DataFrame'>\n",
            "Index: 227188 entries, 783985 to 946668\n",
            "Data columns (total 7 columns):\n",
            " #   Column   Non-Null Count   Dtype         \n",
            "---  ------   --------------   -----         \n",
            " 0   title    227188 non-null  object        \n",
            " 1   rank     227188 non-null  int8          \n",
            " 2   date     227188 non-null  datetime64[ns]\n",
            " 3   artist   227187 non-null  object        \n",
            " 4   region   227188 non-null  object        \n",
            " 5   chart    227188 non-null  object        \n",
            " 6   streams  109973 non-null  float64       \n",
            "dtypes: datetime64[ns](1), float64(1), int8(1), object(4)\n",
            "memory usage: 12.3+ MB\n",
            "None\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# Display the first few rows of the sampled DataFrame\n",
        "sampled_df.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 206
        },
        "id": "UU2iWN0b2mNU",
        "outputId": "2ca2507a-d008-4ae0-ca93-6c2aef09f37c"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                title  rank       date                                 artist  \\\n",
              "783985       Materyal     9 2017-12-23                            Shanti Dope   \n",
              "874461      Missing U     3 2018-08-07                                  Robyn   \n",
              "568462   Shape of You     2 2017-03-06                             Ed Sheeran   \n",
              "2089873     Paparazzi     8 2021-01-31                            Kim Dracula   \n",
              "542887     Ahora Dice     7 2017-08-05  Chris Jedi, J Balvin, Ozuna, Arcangel   \n",
              "\n",
              "              region    chart   streams  \n",
              "783985   Philippines  viral50       NaN  \n",
              "874461       Hungary  viral50       NaN  \n",
              "568462       Ecuador   top200   24437.0  \n",
              "2089873      Denmark  viral50       NaN  \n",
              "542887        Mexico   top200  329388.0  "
            ],
            "text/html": [
              "<div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>783985</th>\n",
              "      <td>Materyal</td>\n",
              "      <td>9</td>\n",
              "      <td>2017-12-23</td>\n",
              "      <td>Shanti Dope</td>\n",
              "      <td>Philippines</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>874461</th>\n",
              "      <td>Missing U</td>\n",
              "      <td>3</td>\n",
              "      <td>2018-08-07</td>\n",
              "      <td>Robyn</td>\n",
              "      <td>Hungary</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>568462</th>\n",
              "      <td>Shape of You</td>\n",
              "      <td>2</td>\n",
              "      <td>2017-03-06</td>\n",
              "      <td>Ed Sheeran</td>\n",
              "      <td>Ecuador</td>\n",
              "      <td>top200</td>\n",
              "      <td>24437.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2089873</th>\n",
              "      <td>Paparazzi</td>\n",
              "      <td>8</td>\n",
              "      <td>2021-01-31</td>\n",
              "      <td>Kim Dracula</td>\n",
              "      <td>Denmark</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>542887</th>\n",
              "      <td>Ahora Dice</td>\n",
              "      <td>7</td>\n",
              "      <td>2017-08-05</td>\n",
              "      <td>Chris Jedi, J Balvin, Ozuna, Arcangel</td>\n",
              "      <td>Mexico</td>\n",
              "      <td>top200</td>\n",
              "      <td>329388.0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>"
            ]
          },
          "metadata": {},
          "execution_count": 38
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "##### Measure memory usage, computation time, and file size"
      ],
      "metadata": {
        "id": "5soFlDuEYdK0"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "import time\n",
        "import psutil\n",
        "# Record start time\n",
        "start_time = time.time()\n",
        "# Record end time\n",
        "end_time = time.time()\n",
        "\n",
        "# Calculate the time taken\n",
        "load_time = end_time - start_time\n",
        "\n",
        "# Print the time taken\n",
        "print(f\"Time taken to load the data: {load_time} seconds\")\n",
        "\n",
        "# Get memory usage\n",
        "memory_usage = psutil.Process(os.getpid()).memory_info().rss\n",
        "print(f\"Memory usage: {memory_usage / (1024 * 1024):.2f} MB\")\n",
        "\n",
        "# Get file size\n",
        "file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB\n",
        "print(f\"File size: {file_size:.2f} MB\")\n",
        "\n",
        "# Optionally, you can print CPU usage as well\n",
        "cpu_percent = psutil.cpu_percent()\n",
        "print(f\"CPU Usage: {cpu_percent}%\")\n",
        "\n",
        "# Additional computation or analysis can be done on the loaded data here\n",
        "\n",
        "# Remember to free up memory if you're done using the DataFrame\n",
        "sampled_df = None"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "T5UmJQmLHcBw",
        "outputId": "34d77c77-3779-4d33-f905-31b04064b9cf"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Time taken to load the data: 8.296966552734375e-05 seconds\n",
            "Memory usage: 2161.80 MB\n",
            "File size: 3322.10 MB\n",
            "CPU Usage: 78.0%\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "\n",
        "---\n",
        "\n"
      ],
      "metadata": {
        "id": "hyXSmlQRyM1Z"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "#### 3.5 Parallelize with Dask\n",
        "\n",
        "Dask is a powerful library that extends pandas to enable parallel and distributed computing. It's particularly useful for handling larger-than-memory datasets."
      ],
      "metadata": {
        "id": "YuTYTOt_I0nO"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "!pip install dask"
      ],
      "metadata": {
        "id": "mtUhj3QUJEQn",
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "outputId": "3fa7b0b0-af89-4e35-9669-a3fbe2434b9b"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Requirement already satisfied: dask in /usr/local/lib/python3.10/dist-packages (2023.8.1)\n",
            "Requirement already satisfied: click>=8.0 in /usr/local/lib/python3.10/dist-packages (from dask) (8.1.7)\n",
            "Requirement already satisfied: cloudpickle>=1.5.0 in /usr/local/lib/python3.10/dist-packages (from dask) (2.2.1)\n",
            "Requirement already satisfied: fsspec>=2021.09.0 in /usr/local/lib/python3.10/dist-packages (from dask) (2023.6.0)\n",
            "Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.10/dist-packages (from dask) (23.2)\n",
            "Requirement already satisfied: partd>=1.2.0 in /usr/local/lib/python3.10/dist-packages (from dask) (1.4.1)\n",
            "Requirement already satisfied: pyyaml>=5.3.1 in /usr/local/lib/python3.10/dist-packages (from dask) (6.0.1)\n",
            "Requirement already satisfied: toolz>=0.10.0 in /usr/local/lib/python3.10/dist-packages (from dask) (0.12.0)\n",
            "Requirement already satisfied: importlib-metadata>=4.13.0 in /usr/local/lib/python3.10/dist-packages (from dask) (7.0.0)\n",
            "Requirement already satisfied: zipp>=0.5 in /usr/local/lib/python3.10/dist-packages (from importlib-metadata>=4.13.0->dask) (3.17.0)\n",
            "Requirement already satisfied: locket in /usr/local/lib/python3.10/dist-packages (from partd>=1.2.0->dask) (1.0.0)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Here, we're importing the Dask DataFrame module and assigning it the alias dd. Dask is a parallel computing library that integrates with Pandas and allows for parallel processing of large datasets."
      ],
      "metadata": {
        "id": "b-3zZeEksw3Q"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "import dask.dataframe as dd\n",
        "\n",
        "# Load the dataset into a Dask DataFrame\n",
        "ddf = dd.read_csv(os.path.join(extracted_dir, csv_file), usecols=columns_of_interest)"
      ],
      "metadata": {
        "id": "4jbWo9kb23ob"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "file_path = 'spotify-charts/charts.csv'\n",
        "df = dd.read_csv(file_path)"
      ],
      "metadata": {
        "id": "FwNbFhRC0SJO"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "##### Measure memory usage, computation time, and file size"
      ],
      "metadata": {
        "id": "IfmvfC0MYgso"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Here, we're importing the time module, which allows us to work with time-related functions.\n",
        "\n",
        "- We measures how long it takes to load data from a CSV file using Dask. The start time is noted, the data is loaded, the end time is noted, and the difference between the start and end times gives us the time taken for the data loading process."
      ],
      "metadata": {
        "id": "QJsfFrA-tgtr"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "import time\n",
        "\n",
        "# Record start time\n",
        "start_time = time.time()\n",
        "\n",
        "# Load the data using Dask\n",
        "df = dd.read_csv(file_path)\n",
        "\n",
        "# Record end time\n",
        "end_time = time.time()\n",
        "\n",
        "# Calculate the time taken\n",
        "load_time = end_time - start_time\n",
        "\n",
        "# Print the time taken\n",
        "print(f\"Time taken to load the data: {load_time} seconds\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "k2k52BD_pKmL",
        "outputId": "0bb3eb1f-6888-4e94-ebe4-b937a26aa273"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Time taken to load the data: 0.016971349716186523 seconds\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# Get memory usage\n",
        "memory_usage = psutil.Process(os.getpid()).memory_info().rss\n",
        "print(f\"Memory usage: {memory_usage / (1024 * 1024):.2f} MB\")\n",
        "\n",
        "# Get file size\n",
        "file_size = os.path.getsize(file_path) / (1024 * 1024)  # in MB\n",
        "print(f\"File size: {file_size:.2f} MB\")\n",
        "\n",
        "# Remember to close the Dask dataframe if you're done using it\n",
        "df = None\n",
        "\n",
        "#print CPU usage\n",
        "cpu_percent = psutil.cpu_percent()\n",
        "print(f\"CPU Usage: {cpu_percent}%\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "l8khNu-U8i3h",
        "outputId": "b5cab49d-c134-43ae-aaf3-0281ee86ef53"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Memory usage: 3733.65 MB\n",
            "File size: 3322.10 MB\n",
            "CPU Usage: 12.6%\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "dtype = {'streams': 'float64'}\n",
        "df = dd.read_csv(file_path, dtype=dtype)"
      ],
      "metadata": {
        "id": "U4tITDUWpNoQ"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "df.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 399
        },
        "id": "OdsJMOYlpOWh",
        "outputId": "c986b24a-c76c-427b-fa1b-a483ae9db42f"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                         title  rank        date  \\\n",
              "0      Chantaje (feat. Maluma)     1  2017-01-01   \n",
              "1  Vente Pa' Ca (feat. Maluma)     2  2017-01-01   \n",
              "2   Reggaetón Lento (Bailemos)     3  2017-01-01   \n",
              "3                       Safari     4  2017-01-01   \n",
              "4                  Shaky Shaky     5  2017-01-01   \n",
              "\n",
              "                                  artist  \\\n",
              "0                                Shakira   \n",
              "1                           Ricky Martin   \n",
              "2                                   CNCO   \n",
              "3  J Balvin, Pharrell Williams, BIA, Sky   \n",
              "4                           Daddy Yankee   \n",
              "\n",
              "                                                 url     region   chart  \\\n",
              "0  https://open.spotify.com/track/6mICuAdrwEjh6Y6...  Argentina  top200   \n",
              "1  https://open.spotify.com/track/7DM4BPaS7uofFul...  Argentina  top200   \n",
              "2  https://open.spotify.com/track/3AEZUABDXNtecAO...  Argentina  top200   \n",
              "3  https://open.spotify.com/track/6rQSrBHf7HlZjtc...  Argentina  top200   \n",
              "4  https://open.spotify.com/track/58IL315gMSTD37D...  Argentina  top200   \n",
              "\n",
              "           trend   streams  \n",
              "0  SAME_POSITION  253019.0  \n",
              "1        MOVE_UP  223988.0  \n",
              "2      MOVE_DOWN  210943.0  \n",
              "3  SAME_POSITION  173865.0  \n",
              "4        MOVE_UP  153956.0  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-b7c24ca3-d044-4feb-a6c2-7374fcb9e74c\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>url</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>trend</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Chantaje (feat. Maluma)</td>\n",
              "      <td>1</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Shakira</td>\n",
              "      <td>https://open.spotify.com/track/6mICuAdrwEjh6Y6...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>SAME_POSITION</td>\n",
              "      <td>253019.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Vente Pa' Ca (feat. Maluma)</td>\n",
              "      <td>2</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Ricky Martin</td>\n",
              "      <td>https://open.spotify.com/track/7DM4BPaS7uofFul...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_UP</td>\n",
              "      <td>223988.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Reggaetón Lento (Bailemos)</td>\n",
              "      <td>3</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>CNCO</td>\n",
              "      <td>https://open.spotify.com/track/3AEZUABDXNtecAO...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>210943.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Safari</td>\n",
              "      <td>4</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>J Balvin, Pharrell Williams, BIA, Sky</td>\n",
              "      <td>https://open.spotify.com/track/6rQSrBHf7HlZjtc...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>SAME_POSITION</td>\n",
              "      <td>173865.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Shaky Shaky</td>\n",
              "      <td>5</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Daddy Yankee</td>\n",
              "      <td>https://open.spotify.com/track/58IL315gMSTD37D...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_UP</td>\n",
              "      <td>153956.0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-b7c24ca3-d044-4feb-a6c2-7374fcb9e74c')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-b7c24ca3-d044-4feb-a6c2-7374fcb9e74c button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-b7c24ca3-d044-4feb-a6c2-7374fcb9e74c');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-749b553d-dc31-4842-b126-6aaf4b3d8a94\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-749b553d-dc31-4842-b126-6aaf4b3d8a94')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-749b553d-dc31-4842-b126-6aaf4b3d8a94 button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "    </div>\n",
              "  </div>\n"
            ]
          },
          "metadata": {},
          "execution_count": 84
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "df.tail()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 382
        },
        "id": "7PLl-JYgpRCK",
        "outputId": "5ea3c514-ba10-49f3-b8b6-75123a5a5af7"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                title  rank        date  \\\n",
              "499877                            BYE    46  2021-07-31   \n",
              "499878                        Pillars    47  2021-07-31   \n",
              "499879                   Gái Độc Thân    48  2021-07-31   \n",
              "499880  Renegade (feat. Taylor Swift)    49  2021-07-31   \n",
              "499881                Letter to Jarad    50  2021-07-31   \n",
              "\n",
              "                           artist  \\\n",
              "499877                      Jaden   \n",
              "499878                     My Anh   \n",
              "499879                      Tlinh   \n",
              "499880            Big Red Machine   \n",
              "499881  LRN Slime, Shiloh Dynasty   \n",
              "\n",
              "                                                      url   region    chart  \\\n",
              "499877  https://open.spotify.com/track/3OUyyDN7EZrL7i0...  Vietnam  viral50   \n",
              "499878  https://open.spotify.com/track/6eky30oFiQbHUAT...  Vietnam  viral50   \n",
              "499879  https://open.spotify.com/track/2klsSb2iTfgDh95...  Vietnam  viral50   \n",
              "499880  https://open.spotify.com/track/1aU1wpYBSpP0M6I...  Vietnam  viral50   \n",
              "499881  https://open.spotify.com/track/508QhA2SncMbh5C...  Vietnam  viral50   \n",
              "\n",
              "            trend  streams  \n",
              "499877    MOVE_UP      NaN  \n",
              "499878  NEW_ENTRY      NaN  \n",
              "499879  MOVE_DOWN      NaN  \n",
              "499880  MOVE_DOWN      NaN  \n",
              "499881  MOVE_DOWN      NaN  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-091b805a-c94f-479b-a04c-0cdf16c447ba\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>url</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>trend</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>499877</th>\n",
              "      <td>BYE</td>\n",
              "      <td>46</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Jaden</td>\n",
              "      <td>https://open.spotify.com/track/3OUyyDN7EZrL7i0...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>MOVE_UP</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>499878</th>\n",
              "      <td>Pillars</td>\n",
              "      <td>47</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>My Anh</td>\n",
              "      <td>https://open.spotify.com/track/6eky30oFiQbHUAT...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>NEW_ENTRY</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>499879</th>\n",
              "      <td>Gái Độc Thân</td>\n",
              "      <td>48</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Tlinh</td>\n",
              "      <td>https://open.spotify.com/track/2klsSb2iTfgDh95...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>499880</th>\n",
              "      <td>Renegade (feat. Taylor Swift)</td>\n",
              "      <td>49</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Big Red Machine</td>\n",
              "      <td>https://open.spotify.com/track/1aU1wpYBSpP0M6I...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>499881</th>\n",
              "      <td>Letter to Jarad</td>\n",
              "      <td>50</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>LRN Slime, Shiloh Dynasty</td>\n",
              "      <td>https://open.spotify.com/track/508QhA2SncMbh5C...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-091b805a-c94f-479b-a04c-0cdf16c447ba')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-091b805a-c94f-479b-a04c-0cdf16c447ba button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-091b805a-c94f-479b-a04c-0cdf16c447ba');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-1ac66560-2bd9-4ea4-a5ec-104a34a423a6\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-1ac66560-2bd9-4ea4-a5ec-104a34a423a6')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-1ac66560-2bd9-4ea4-a5ec-104a34a423a6 button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "    </div>\n",
              "  </div>\n"
            ]
          },
          "metadata": {},
          "execution_count": 85
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- We check the data types of each column"
      ],
      "metadata": {
        "id": "DSRqQLBFt4I2"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Check the data types of each column\n",
        "df.dtypes"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "w0urbJjRpS-o",
        "outputId": "588b5975-316e-415d-d706-3aa17aebcf75"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "title      object\n",
              "rank        int64\n",
              "date       object\n",
              "artist     object\n",
              "url        object\n",
              "region     object\n",
              "chart      object\n",
              "trend      object\n",
              "streams     int64\n",
              "dtype: object"
            ]
          },
          "metadata": {},
          "execution_count": 47
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "df.isnull().sum()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "h2ca0_BepTwo",
        "outputId": "260c9885-2c18-4b5b-c2c9-da4a5601edc9"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "Dask Series Structure:\n",
              "npartitions=1\n",
              "artist    int64\n",
              "url         ...\n",
              "dtype: int64\n",
              "Dask Name: dataframe-sum-agg, 4 graph layers"
            ]
          },
          "metadata": {},
          "execution_count": 48
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Check unique values in the 'artist' column"
      ],
      "metadata": {
        "id": "PiiNV0ebt84v"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Check unique values in the 'artist' column\n",
        "unique_artists = df['artist'].unique().compute()\n",
        "print(unique_artists)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "lSpFNwhipaND",
        "outputId": "dcef9c59-79a5-4afd-fe61-badea07dca38"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "0                                      Shakira\n",
            "1                                 Ricky Martin\n",
            "2                                         CNCO\n",
            "3        J Balvin, Pharrell Williams, BIA, Sky\n",
            "4                                 Daddy Yankee\n",
            "                         ...                  \n",
            "96152                Bevok, Afrikaans Wil Dans\n",
            "96153                                 vvpskvd.\n",
            "96154                                      Adé\n",
            "96155               Tribl, Maverick City Music\n",
            "96156                             Yehuda Elias\n",
            "Name: artist, Length: 96157, dtype: object\n"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Drop all the null value at each row"
      ],
      "metadata": {
        "id": "t4ysZ5Y5uEZ-"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "df = df.dropna()"
      ],
      "metadata": {
        "id": "xpJVfzcVpeOV"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Fill NaN values in 'streams' with the mean value"
      ],
      "metadata": {
        "id": "Xiez3PkiuHba"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Fill NaN values in 'streams' with the mean value\n",
        "df['streams'] = df['streams'].fillna(df['streams'].mean())"
      ],
      "metadata": {
        "id": "hoMuCiZlplB-"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Drop duplicates based on specific columns"
      ],
      "metadata": {
        "id": "OuyuW7TSuLMB"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Drop duplicates based on specific columns\n",
        "df = df.drop_duplicates(subset=['title', 'artist'])"
      ],
      "metadata": {
        "id": "QiXpv7_xpfEw"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Fill NaN values with 0"
      ],
      "metadata": {
        "id": "o84CCw3UuY-7"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Fill NaN values with a specific value (e.g., 0)\n",
        "df = df.fillna(0)"
      ],
      "metadata": {
        "id": "-tfdvv-Xpnjr"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "df.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "TqmNw07uppyW",
        "outputId": "afd96357-1faf-459b-e952-9a651b1a75bd"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'dask.dataframe.core.DataFrame'>\n",
            "Columns: 9 entries, title to streams\n",
            "dtypes: object(7), int64(2)"
          ]
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Here , we specify column of interest"
      ],
      "metadata": {
        "id": "bUTqThEmucvl"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Specify columns of interest\n",
        "columns_of_interest = ['title', 'rank', 'date', 'artist', 'region', 'streams', 'chart']\n",
        "\n",
        "# Select only the columns of interest\n",
        "df = df[columns_of_interest]"
      ],
      "metadata": {
        "id": "BdHm4aw-prSw"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Define the subset size\n",
        "subset_size = 1000000"
      ],
      "metadata": {
        "id": "QGlfkxPsps1a"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "df = df.sample(frac=subset_size / len(df), replace=False)"
      ],
      "metadata": {
        "id": "GZbpuTZxpy31"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "df['date'] = dd.to_datetime(df['date'], errors='coerce')\n",
        "\n",
        "# Display information about the DataFrame\n",
        "df.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Z_Nr8PZdpz1x",
        "outputId": "3ca89c61-772d-463c-94e9-9c3a150e9731"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'dask.dataframe.core.DataFrame'>\n",
            "Columns: 7 entries, title to chart\n",
            "dtypes: datetime64[ns](1), object(4), int64(2)"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import dask.dataframe as dd"
      ],
      "metadata": {
        "id": "_IdQrfNip4wU"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "- We chunk the data into 10000"
      ],
      "metadata": {
        "id": "kasmBXCtuiJH"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "chunk_size = 10000  # Adjust the chunk size as needed"
      ],
      "metadata": {
        "id": "5bvagPRNp9Ou"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Define a function to process each chunk\n",
        "def process_chunk(partition):\n",
        "    # Filter rows where 'rank' is less than or equal to 10\n",
        "    processed_chunk = partition[partition['rank'] <= 10]\n",
        "    return processed_chunk"
      ],
      "metadata": {
        "id": "RkRMXDrUp-zU"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Read the Dask DataFrame with specified dtype\n",
        "dtype = {'streams': 'float64'}\n",
        "df = dd.read_csv(file_path, dtype=dtype)"
      ],
      "metadata": {
        "id": "W_1wJ-MvqATG"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Chunk the Dask DataFrame and apply the processing function\n",
        "chunks = df.map_partitions(process_chunk, meta=df)"
      ],
      "metadata": {
        "id": "aUSy6jXvqA7Z"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Concatenate the processed chunks into a new Dask DataFrame\n",
        "concatenated_df = dd.concat([chunks])"
      ],
      "metadata": {
        "id": "F5RpdYgXqCpW"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Now, you have a new Dask DataFrame (concatenated_df)\n",
        "# You can perform further operations or compute the result as needed\n",
        "result = concatenated_df.compute()"
      ],
      "metadata": {
        "id": "arHA9UcPqFHa"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "- Result of the chunk"
      ],
      "metadata": {
        "id": "iEAX9BTg48pE"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "# Print or inspect the concatenated result\n",
        "print(result)"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "WJQZ8ZlFqGl7",
        "outputId": "0f1f2b21-269a-4049-e0bc-43f4a45e23a9"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "                                              title  rank        date  \\\n",
            "0                           Chantaje (feat. Maluma)     1  2017-01-01   \n",
            "1                       Vente Pa' Ca (feat. Maluma)     2  2017-01-01   \n",
            "2                        Reggaetón Lento (Bailemos)     3  2017-01-01   \n",
            "3                                            Safari     4  2017-01-01   \n",
            "4                                       Shaky Shaky     5  2017-01-01   \n",
            "...                                             ...   ...         ...   \n",
            "499837                              Giấc Mơ Rất Thơ     5  2021-07-31   \n",
            "499838                                 Nevertheless     6  2021-07-31   \n",
            "499839  Your Sunday (Sunday Morning) [feat. Ampoff]     7  2021-07-31   \n",
            "499840                                We're Already     8  2021-07-31   \n",
            "499841                    Happy For You (feat. Vũ.)     9  2021-07-31   \n",
            "\n",
            "                                       artist  \\\n",
            "0                                     Shakira   \n",
            "1                                Ricky Martin   \n",
            "2                                        CNCO   \n",
            "3       J Balvin, Pharrell Williams, BIA, Sky   \n",
            "4                                Daddy Yankee   \n",
            "...                                       ...   \n",
            "499837                          Mer, thaison!   \n",
            "499838                              Night Off   \n",
            "499839                             Sunny Shin   \n",
            "499840                              KIMMUSEUM   \n",
            "499841                           Lukas Graham   \n",
            "\n",
            "                                                      url     region    chart  \\\n",
            "0       https://open.spotify.com/track/6mICuAdrwEjh6Y6...  Argentina   top200   \n",
            "1       https://open.spotify.com/track/7DM4BPaS7uofFul...  Argentina   top200   \n",
            "2       https://open.spotify.com/track/3AEZUABDXNtecAO...  Argentina   top200   \n",
            "3       https://open.spotify.com/track/6rQSrBHf7HlZjtc...  Argentina   top200   \n",
            "4       https://open.spotify.com/track/58IL315gMSTD37D...  Argentina   top200   \n",
            "...                                                   ...        ...      ...   \n",
            "499837  https://open.spotify.com/track/546ce8vBSyZFwiE...    Vietnam  viral50   \n",
            "499838  https://open.spotify.com/track/6fG9JVdUx4Ttks3...    Vietnam  viral50   \n",
            "499839  https://open.spotify.com/track/5q2kwQkuVNIRw4C...    Vietnam  viral50   \n",
            "499840  https://open.spotify.com/track/1kuML8BXbxGjfxQ...    Vietnam  viral50   \n",
            "499841  https://open.spotify.com/track/2XjbfQQZlPwOMTm...    Vietnam  viral50   \n",
            "\n",
            "                trend   streams  \n",
            "0       SAME_POSITION  253019.0  \n",
            "1             MOVE_UP  223988.0  \n",
            "2           MOVE_DOWN  210943.0  \n",
            "3       SAME_POSITION  173865.0  \n",
            "4             MOVE_UP  153956.0  \n",
            "...               ...       ...  \n",
            "499837        MOVE_UP       NaN  \n",
            "499838      MOVE_DOWN       NaN  \n",
            "499839  SAME_POSITION       NaN  \n",
            "499840      MOVE_DOWN       NaN  \n",
            "499841      MOVE_DOWN       NaN  \n",
            "\n",
            "[2271876 rows x 9 columns]\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "result.info()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "6TdHgxRvqIdM",
        "outputId": "bad9a501-4835-4b85-aee9-5f1441621edb"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "<class 'pandas.core.frame.DataFrame'>\n",
            "Index: 2271876 entries, 0 to 499841\n",
            "Data columns (total 9 columns):\n",
            " #   Column   Dtype  \n",
            "---  ------   -----  \n",
            " 0   title    object \n",
            " 1   rank     int64  \n",
            " 2   date     object \n",
            " 3   artist   object \n",
            " 4   url      object \n",
            " 5   region   object \n",
            " 6   chart    object \n",
            " 7   trend    object \n",
            " 8   streams  float64\n",
            "dtypes: float64(1), int64(1), object(7)\n",
            "memory usage: 173.3+ MB\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "result.head()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 399
        },
        "id": "v3rcU0RpqJ-m",
        "outputId": "f1e888ea-f236-40e6-91a5-f58ce4a63559"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                         title  rank        date  \\\n",
              "0      Chantaje (feat. Maluma)     1  2017-01-01   \n",
              "1  Vente Pa' Ca (feat. Maluma)     2  2017-01-01   \n",
              "2   Reggaetón Lento (Bailemos)     3  2017-01-01   \n",
              "3                       Safari     4  2017-01-01   \n",
              "4                  Shaky Shaky     5  2017-01-01   \n",
              "\n",
              "                                  artist  \\\n",
              "0                                Shakira   \n",
              "1                           Ricky Martin   \n",
              "2                                   CNCO   \n",
              "3  J Balvin, Pharrell Williams, BIA, Sky   \n",
              "4                           Daddy Yankee   \n",
              "\n",
              "                                                 url     region   chart  \\\n",
              "0  https://open.spotify.com/track/6mICuAdrwEjh6Y6...  Argentina  top200   \n",
              "1  https://open.spotify.com/track/7DM4BPaS7uofFul...  Argentina  top200   \n",
              "2  https://open.spotify.com/track/3AEZUABDXNtecAO...  Argentina  top200   \n",
              "3  https://open.spotify.com/track/6rQSrBHf7HlZjtc...  Argentina  top200   \n",
              "4  https://open.spotify.com/track/58IL315gMSTD37D...  Argentina  top200   \n",
              "\n",
              "           trend   streams  \n",
              "0  SAME_POSITION  253019.0  \n",
              "1        MOVE_UP  223988.0  \n",
              "2      MOVE_DOWN  210943.0  \n",
              "3  SAME_POSITION  173865.0  \n",
              "4        MOVE_UP  153956.0  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-5c67a1d9-a936-477c-9ac1-4c1efa70d426\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>url</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>trend</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>0</th>\n",
              "      <td>Chantaje (feat. Maluma)</td>\n",
              "      <td>1</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Shakira</td>\n",
              "      <td>https://open.spotify.com/track/6mICuAdrwEjh6Y6...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>SAME_POSITION</td>\n",
              "      <td>253019.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>1</th>\n",
              "      <td>Vente Pa' Ca (feat. Maluma)</td>\n",
              "      <td>2</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Ricky Martin</td>\n",
              "      <td>https://open.spotify.com/track/7DM4BPaS7uofFul...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_UP</td>\n",
              "      <td>223988.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>2</th>\n",
              "      <td>Reggaetón Lento (Bailemos)</td>\n",
              "      <td>3</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>CNCO</td>\n",
              "      <td>https://open.spotify.com/track/3AEZUABDXNtecAO...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>210943.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>3</th>\n",
              "      <td>Safari</td>\n",
              "      <td>4</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>J Balvin, Pharrell Williams, BIA, Sky</td>\n",
              "      <td>https://open.spotify.com/track/6rQSrBHf7HlZjtc...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>SAME_POSITION</td>\n",
              "      <td>173865.0</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>4</th>\n",
              "      <td>Shaky Shaky</td>\n",
              "      <td>5</td>\n",
              "      <td>2017-01-01</td>\n",
              "      <td>Daddy Yankee</td>\n",
              "      <td>https://open.spotify.com/track/58IL315gMSTD37D...</td>\n",
              "      <td>Argentina</td>\n",
              "      <td>top200</td>\n",
              "      <td>MOVE_UP</td>\n",
              "      <td>153956.0</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-5c67a1d9-a936-477c-9ac1-4c1efa70d426')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-5c67a1d9-a936-477c-9ac1-4c1efa70d426 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-5c67a1d9-a936-477c-9ac1-4c1efa70d426');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-40684af6-4d40-436f-8b00-945cda55295a\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-40684af6-4d40-436f-8b00-945cda55295a')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-40684af6-4d40-436f-8b00-945cda55295a button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "    </div>\n",
              "  </div>\n"
            ]
          },
          "metadata": {},
          "execution_count": 69
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "result.tail()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 382
        },
        "id": "FmOMPugvqLxJ",
        "outputId": "4f77362b-052c-4180-eebc-da7463fad492"
      },
      "execution_count": null,
      "outputs": [
        {
          "output_type": "execute_result",
          "data": {
            "text/plain": [
              "                                              title  rank        date  \\\n",
              "499837                              Giấc Mơ Rất Thơ     5  2021-07-31   \n",
              "499838                                 Nevertheless     6  2021-07-31   \n",
              "499839  Your Sunday (Sunday Morning) [feat. Ampoff]     7  2021-07-31   \n",
              "499840                                We're Already     8  2021-07-31   \n",
              "499841                    Happy For You (feat. Vũ.)     9  2021-07-31   \n",
              "\n",
              "               artist                                                url  \\\n",
              "499837  Mer, thaison!  https://open.spotify.com/track/546ce8vBSyZFwiE...   \n",
              "499838      Night Off  https://open.spotify.com/track/6fG9JVdUx4Ttks3...   \n",
              "499839     Sunny Shin  https://open.spotify.com/track/5q2kwQkuVNIRw4C...   \n",
              "499840      KIMMUSEUM  https://open.spotify.com/track/1kuML8BXbxGjfxQ...   \n",
              "499841   Lukas Graham  https://open.spotify.com/track/2XjbfQQZlPwOMTm...   \n",
              "\n",
              "         region    chart          trend  streams  \n",
              "499837  Vietnam  viral50        MOVE_UP      NaN  \n",
              "499838  Vietnam  viral50      MOVE_DOWN      NaN  \n",
              "499839  Vietnam  viral50  SAME_POSITION      NaN  \n",
              "499840  Vietnam  viral50      MOVE_DOWN      NaN  \n",
              "499841  Vietnam  viral50      MOVE_DOWN      NaN  "
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-9a84bc26-e378-4f85-ad03-3541720fa2a7\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>title</th>\n",
              "      <th>rank</th>\n",
              "      <th>date</th>\n",
              "      <th>artist</th>\n",
              "      <th>url</th>\n",
              "      <th>region</th>\n",
              "      <th>chart</th>\n",
              "      <th>trend</th>\n",
              "      <th>streams</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>499837</th>\n",
              "      <td>Giấc Mơ Rất Thơ</td>\n",
              "      <td>5</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Mer, thaison!</td>\n",
              "      <td>https://open.spotify.com/track/546ce8vBSyZFwiE...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>MOVE_UP</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>499838</th>\n",
              "      <td>Nevertheless</td>\n",
              "      <td>6</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Night Off</td>\n",
              "      <td>https://open.spotify.com/track/6fG9JVdUx4Ttks3...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>499839</th>\n",
              "      <td>Your Sunday (Sunday Morning) [feat. Ampoff]</td>\n",
              "      <td>7</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Sunny Shin</td>\n",
              "      <td>https://open.spotify.com/track/5q2kwQkuVNIRw4C...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>SAME_POSITION</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>499840</th>\n",
              "      <td>We're Already</td>\n",
              "      <td>8</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>KIMMUSEUM</td>\n",
              "      <td>https://open.spotify.com/track/1kuML8BXbxGjfxQ...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>499841</th>\n",
              "      <td>Happy For You (feat. Vũ.)</td>\n",
              "      <td>9</td>\n",
              "      <td>2021-07-31</td>\n",
              "      <td>Lukas Graham</td>\n",
              "      <td>https://open.spotify.com/track/2XjbfQQZlPwOMTm...</td>\n",
              "      <td>Vietnam</td>\n",
              "      <td>viral50</td>\n",
              "      <td>MOVE_DOWN</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-9a84bc26-e378-4f85-ad03-3541720fa2a7')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-9a84bc26-e378-4f85-ad03-3541720fa2a7 button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-9a84bc26-e378-4f85-ad03-3541720fa2a7');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "<div id=\"df-1ff55e2d-6fa0-4971-b0f5-418f2726511b\">\n",
              "  <button class=\"colab-df-quickchart\" onclick=\"quickchart('df-1ff55e2d-6fa0-4971-b0f5-418f2726511b')\"\n",
              "            title=\"Suggest charts\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "<svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\"viewBox=\"0 0 24 24\"\n",
              "     width=\"24px\">\n",
              "    <g>\n",
              "        <path d=\"M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z\"/>\n",
              "    </g>\n",
              "</svg>\n",
              "  </button>\n",
              "\n",
              "<style>\n",
              "  .colab-df-quickchart {\n",
              "      --bg-color: #E8F0FE;\n",
              "      --fill-color: #1967D2;\n",
              "      --hover-bg-color: #E2EBFA;\n",
              "      --hover-fill-color: #174EA6;\n",
              "      --disabled-fill-color: #AAA;\n",
              "      --disabled-bg-color: #DDD;\n",
              "  }\n",
              "\n",
              "  [theme=dark] .colab-df-quickchart {\n",
              "      --bg-color: #3B4455;\n",
              "      --fill-color: #D2E3FC;\n",
              "      --hover-bg-color: #434B5C;\n",
              "      --hover-fill-color: #FFFFFF;\n",
              "      --disabled-bg-color: #3B4455;\n",
              "      --disabled-fill-color: #666;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart {\n",
              "    background-color: var(--bg-color);\n",
              "    border: none;\n",
              "    border-radius: 50%;\n",
              "    cursor: pointer;\n",
              "    display: none;\n",
              "    fill: var(--fill-color);\n",
              "    height: 32px;\n",
              "    padding: 0;\n",
              "    width: 32px;\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart:hover {\n",
              "    background-color: var(--hover-bg-color);\n",
              "    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "    fill: var(--button-hover-fill-color);\n",
              "  }\n",
              "\n",
              "  .colab-df-quickchart-complete:disabled,\n",
              "  .colab-df-quickchart-complete:disabled:hover {\n",
              "    background-color: var(--disabled-bg-color);\n",
              "    fill: var(--disabled-fill-color);\n",
              "    box-shadow: none;\n",
              "  }\n",
              "\n",
              "  .colab-df-spinner {\n",
              "    border: 2px solid var(--fill-color);\n",
              "    border-color: transparent;\n",
              "    border-bottom-color: var(--fill-color);\n",
              "    animation:\n",
              "      spin 1s steps(1) infinite;\n",
              "  }\n",
              "\n",
              "  @keyframes spin {\n",
              "    0% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "      border-left-color: var(--fill-color);\n",
              "    }\n",
              "    20% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    30% {\n",
              "      border-color: transparent;\n",
              "      border-left-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    40% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-top-color: var(--fill-color);\n",
              "    }\n",
              "    60% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "    }\n",
              "    80% {\n",
              "      border-color: transparent;\n",
              "      border-right-color: var(--fill-color);\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "    90% {\n",
              "      border-color: transparent;\n",
              "      border-bottom-color: var(--fill-color);\n",
              "    }\n",
              "  }\n",
              "</style>\n",
              "\n",
              "  <script>\n",
              "    async function quickchart(key) {\n",
              "      const quickchartButtonEl =\n",
              "        document.querySelector('#' + key + ' button');\n",
              "      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.\n",
              "      quickchartButtonEl.classList.add('colab-df-spinner');\n",
              "      try {\n",
              "        const charts = await google.colab.kernel.invokeFunction(\n",
              "            'suggestCharts', [key], {});\n",
              "      } catch (error) {\n",
              "        console.error('Error during call to suggestCharts:', error);\n",
              "      }\n",
              "      quickchartButtonEl.classList.remove('colab-df-spinner');\n",
              "      quickchartButtonEl.classList.add('colab-df-quickchart-complete');\n",
              "    }\n",
              "    (() => {\n",
              "      let quickchartButtonEl =\n",
              "        document.querySelector('#df-1ff55e2d-6fa0-4971-b0f5-418f2726511b button');\n",
              "      quickchartButtonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "    })();\n",
              "  </script>\n",
              "</div>\n",
              "    </div>\n",
              "  </div>\n"
            ]
          },
          "metadata": {},
          "execution_count": 70
        }
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "### 4. Comparative Analysis\n",
        "Conduct a comprehensive comparative analysis between traditional methods and advanced strategies. Evaluate aspects such as memory usage, computation time, and file size. Provide meaningful insights into the advantages gained through the adoption of advanced strategies.\n",
        "\n"
      ],
      "metadata": {
        "id": "_OFTWzLwJOHD"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "Let's analyze the results for each loading strategy:"
      ],
      "metadata": {
        "id": "gJj0g6ZhZT2a"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "| Strategy                           | Time to Load (seconds) | Memory Usage (MB) | File Size (MB) | CPU Usage (%) |\n",
        "|------------------------------------|------------------------|-------------------|----------------|---------------|\n",
        "| Full Dataset Load                  | 4.03e-05               | 194.75            | 3322.10        | 67.9          |\n",
        "| Strategy 1: Load Selected Columns  | 2.55                   | 342.62            | 3322.10        | 60.2          |\n",
        "| Strategy 2: Load and Filter         | 196.52                 | 413.34            | 3322.10        | 19.7          |\n",
        "| Strategy 3: Use Chunking            | 267.08                 | 3656.25           | 3322.10        | 69.2          |\n",
        "| Strategy 4: Optimize Data Types     | 72.02                  | 5784.59           | 3322.10        | 52.1          |\n",
        "| Strategy 5: Sampling (10% of Data)  | 8.30e-05               | 2161.80           | 3322.10        | 78.0          |\n",
        "| Strategy 6: Parallelize with Dask  | 0.017                  | 3733.65           | 3322.10        | 12.6          |\n",
        "\n",
        "This table provides a comparative analysis of various loading strategies based on key aspects such as time to load, memory usage, file size, and CPU usage."
      ],
      "metadata": {
        "id": "dCb7Cyx2ZNb3"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "### Summary:\n",
        "\n",
        "#### Memory Efficiency:\n",
        "\n",
        "- **Strategies 1, 5, and 6:**\n",
        "  -Outperform the full dataset load in terms of memory efficiency\n",
        "- **Strategy 4 (Optimize Data Types) and Strategy 6 (Parallelize with Dask):**\n",
        "  - Incur higher memory usage, possibly due to optimization efforts or parallel processing overhead.\n",
        "\n",
        "#### Computation Time:\n",
        "\n",
        "- **Strategy 6 (Parallelize with Dask):**\n",
        "  -Outperforms other strategies by a large margin, making it the most computationally efficient strategy.\n",
        "- **Strategies 4 and 5:**\n",
        "  - Show notable improvements, indicating the impact of data optimization and sampling.\n",
        "\n",
        "#### File Size:\n",
        "\n",
        "- All strategies maintain the same file size, suggesting that they are likely reading the same dataset.\n",
        "\n",
        "### Conclusion:\n",
        "\n",
        "#### Advantages of Advanced Strategies:\n",
        "\n",
        "- **Dask Parallelization (Strategy 6):**\n",
        "  - Significantly shorter computation times.\n",
        "  - Use memory sparingly while preserving effectiveness.\n",
        "  - Significant benefit when processing large amounts of data.\n",
        "\n",
        "- **Optimizing Data Types (Strategy 4):**\n",
        "  - Considerable reduction in computation time.\n",
        "  - Faster processing may come at the expense of higher memory usage.\n",
        "\n",
        "- **Sampling (Strategy 5):**\n",
        "  - Significant reduction in computation time.\n",
        "  - Moderate memory usage.\n",
        "\n",
        "#### Considerations:\n",
        "\n",
        "- The particular needs and limitations of the analysis determine the best course of action.\n",
        "- Particularly for large datasets, Strategy 6 (Dask) stands out for its effectiveness in terms of computation time and memory usage.\n",
        "- When only a moderate amount of memory is required and quick insights are required, strategies 4 and 5 are good substitutes.\n"
      ],
      "metadata": {
        "id": "EVMw-xNFUq-X"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "\n",
        "---\n",
        "\n"
      ],
      "metadata": {
        "id": "ujckbtgPJczQ"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "### 5. Conclusion: Summarize your findings.\n",
        "\n",
        "Explain why you chose these strategies and how they make a difference in handling big data."
      ],
      "metadata": {
        "id": "BfuE2mJtJTc0"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "**Load Less Data:**\n",
        "\n",
        "- **Objective:** Focusing on the primary columns - title, rank, date, artist, region, streams, and chart - with a dataset size of 100,000 rows.\n",
        "- **Process:** Implementing traditional methods to load a reduced dataset, filtering for Malaysia region and chart top 200.\n",
        "- **Advantages:** Reduced data size significantly enhances processing speed, minimizing memory usage compared to the original dataset of 26 million rows.\n",
        "\n",
        "\n",
        "**Chunk Processing:**\n",
        "- **Objective:** Divide the dataset into chunks of 100,000 rows each for faster processing.\n",
        "- **Technique:** Implementing advanced strategies for chunk processing, optimizing memory usage and computation time.\n",
        "- **Benefits:** Enables faster execution and lowers memory consumption compared to processing the entire dataset in one go.\n",
        "\n",
        "**Datatype Optimization**:\n",
        "- **Objective:** Optimize memory usage by converting int64 and float64 to int16 and float32.\n",
        "- **Advanced Approach:** Utilizing advanced strategies to optimize data types, enhancing loading speed and saving memory.\n",
        "- **Advantages:** Reduced memory footprint contributes to faster loading and more efficient resource utilization.\n",
        "\n",
        "**Sampling Process**:\n",
        "- **Objective:** Sample 10% of the total rows for analysis, with an option to adjust the percentage.\n",
        "- **Advanced Technique:** Employing advanced sampling strategies, setting a random seed (random_state=42) for reproducibility.\n",
        "- **Significance:** Advanced sampling methods ensure randomness and reproducibility, crucial for robust analysis.\n",
        "\n",
        "\n",
        "**Parralelize with Dask**\n",
        "\n",
        "Load More Dataset:\n",
        "- *Objective:* Use all the dataset without reducing the size. Make sure all dataset run the same process.\n",
        "- *Process:* Use all rows and columns in the dataset.\n",
        "- *Advantages:* Completely run the process to the dataset and the result is more precise.\n",
        "\n",
        "Missing Value Imputation and Date Format Conversion:\n",
        "- *Objective:* Replace both numeric and string missing value with the mean value and convert date datatype to date format.\n",
        "- *Advantages:* All data in date column completely change the data type to date type and there are no missing values in the dataset.\n",
        "\n",
        "Chunk Processing\n",
        "- *Objective:* Chunk the large dataset into small files.\n",
        "- *Process:* The chunk file size is 10000.\n",
        "- *Advantages:* Dask only need short processing time to chunk the big dataset. Chunking is to reduce the file size and also to shorten the processing time for each file to get executed.\n",
        "\n",
        "Datatype Optimization\n",
        "- *Objective:* When the datatype changes, memory size will reduce. Some of the mathematical calculation can be used when the datatype change to the numeric datatype.\n",
        "- *Advanced Approach:* Utilizing advanced strategies to optimize data types, enhancing loading speed and saving memory.\n",
        "- *Advantages:* Reduced memory footprint contributes to faster loading, correct calculation and result.\n",
        "\n",
        "\n",
        "\n",
        "---\n",
        "\n",
        "\n",
        "\n",
        "**Insights and Advantages Gained through these strategies**:\n",
        "\n",
        "- *Efficiency Gains:* Bring significant improvement in computation time and memory usage.\n",
        "- *Scalability:* Enabling processing of large dataset.  Its ability to handle computations that exceed the memory capacity of a single machine makes it a powerful tool for scaling data processing.\n",
        "- *Resource Optimization:* It efficiently utilizes available resources, both in terms of computation power and memory, ensuring a streamlined and faster data analysis pipeline.\n",
        "\n",
        "In summary, the adoption of advanced strategies offers significant advantages in terms of speed, resource utilization, and scalability compared to traditional methods. These improvements become particularly pronounced when dealing with large datasets, as seen in the specified scenario of 26 million rows."
      ],
      "metadata": {
        "id": "cnsYIbQTKVSj"
      }
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "\n",
        "---\n",
        "\n"
      ],
      "metadata": {
        "id": "Zp96eMziJd0G"
      }
    }
  ]
}