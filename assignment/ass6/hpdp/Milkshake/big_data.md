---
jupyter:
  colab:
  kernelspec:
    display_name: Python 3
    name: python3
  language_info:
    name: python
  nbformat: 4
  nbformat_minor: 0
---

::: {.cell .markdown id="_6IcbUM4E90X"}
## Assignment 6

-   Group Name : MilkShake
-   Group Member :
-   Nurunnajwa binti Zulkifli A21EC0121
-   Nur Shuhada Safiah binti Ayob A21EC0114 -Date : 17 December 2023
:::

::: {.cell .markdown id="f8-APGzWHybl"}

------------------------------------------------------------------------
:::

::: {.cell .markdown id="1u06XUgGHBSi"}
### 1. Pick a Big Dataset {#1-pick-a-big-dataset}

Start by choosing a suitable dataset. Choose a dataset from reputable
sources such as Kaggle, UCI Machine Learning Repository, or any other
pertinent dataset repository. Make sure it\'s big---over 700 MB.
:::

::: {.cell .markdown id="jWrLlCZtHG0U"}
Our dataset is [Spotify
Chart](https://www.kaggle.com/datasets/dhruvildave/spotify-charts).

This is a complete dataset of all the \"Top 200\" and \"Viral 50\"
charts published globally by Spotify. Spotify publishes a new chart
every 2-3 days. This is its entire collection since January 1, 2017.
:::

::: {.cell .markdown id="5KZUAMQHIMkx"}

------------------------------------------------------------------------
:::

::: {.cell .markdown id="xoq_VDRmITue"}
###2. Loading the Dataset Use Python and Pandas to load your chosen
dataset into your Colab notebook. You can either upload it from your
computer or directly from an online source.
:::

::: {.cell .markdown id="aLjvV_h-p7gt"}
**Kaggle Setup:**

-   We install the Kaggle package, create a directory named .kaggle in
    the home directory
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="hqqld_n0ITC-" outputId="dc0e02d4-e8b2-4cd6-e214-04052c0a90f7"}
``` python
! pip install kaggle
```

::: {.output .stream .stdout}
    Requirement already satisfied: kaggle in /usr/local/lib/python3.10/dist-packages (1.5.16)
    Requirement already satisfied: six>=1.10 in /usr/local/lib/python3.10/dist-packages (from kaggle) (1.16.0)
    Requirement already satisfied: certifi in /usr/local/lib/python3.10/dist-packages (from kaggle) (2023.11.17)
    Requirement already satisfied: python-dateutil in /usr/local/lib/python3.10/dist-packages (from kaggle) (2.8.2)
    Requirement already satisfied: requests in /usr/local/lib/python3.10/dist-packages (from kaggle) (2.31.0)
    Requirement already satisfied: tqdm in /usr/local/lib/python3.10/dist-packages (from kaggle) (4.66.1)
    Requirement already satisfied: python-slugify in /usr/local/lib/python3.10/dist-packages (from kaggle) (8.0.1)
    Requirement already satisfied: urllib3 in /usr/local/lib/python3.10/dist-packages (from kaggle) (2.0.7)
    Requirement already satisfied: bleach in /usr/local/lib/python3.10/dist-packages (from kaggle) (6.1.0)
    Requirement already satisfied: webencodings in /usr/local/lib/python3.10/dist-packages (from bleach->kaggle) (0.5.1)
    Requirement already satisfied: text-unidecode>=1.3 in /usr/local/lib/python3.10/dist-packages (from python-slugify->kaggle) (1.3)
    Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.10/dist-packages (from requests->kaggle) (3.3.2)
    Requirement already satisfied: idna<4,>=2.5 in /usr/local/lib/python3.10/dist-packages (from requests->kaggle) (3.6)
:::
:::

::: {.cell .markdown id="voooQCOqqMh4"}
-   We copy the Kaggle API key file (kaggle.json) to the .kaggle
    directory , and set the appropriate permissions on the key file.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="98DH-aPNVd4Y" outputId="a6bec4ae-0791-4f89-c8d4-58fc81bec131"}
``` python
! mkdir ~/.kaggle
```

::: {.output .stream .stdout}
    mkdir: cannot create directory ‘/root/.kaggle’: File exists
:::
:::

::: {.cell .code id="erz6lBiuVisZ"}
``` python
!  cp /content/kaggle.json ~/.kaggle/
```
:::

::: {.cell .code id="m5PQ8aUrV4pJ"}
``` python
! chmod 600 ~/.kaggle/kaggle.json
```
:::

::: {.cell .markdown id="2qr3nl-rqb4f"}
**Download Dataset:**

-   This line command uses the Kaggle API to download the dataset named
    \"spotify-charts\" from Kaggle.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="CU9DgGl9V7L_" outputId="7a872df7-65fe-4a91-c6dc-48cc1f35a0c2"}
``` python
! kaggle datasets download dhruvildave/spotify-charts
```

::: {.output .stream .stdout}
    spotify-charts.zip: Skipping, found more recently modified local copy (use --force to force download)
:::
:::

::: {.cell .markdown id="qIH1TVOWqlxE"}
**Modin Installation:**

-   The code installs the Modin library along with its dependencies
    using !pip install modin\[all\].

-   Modin is a library designed to accelerate and scale up pandas
    workflows by parallelizing and optimizing the underlying
    computations.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="HU_DrRvnliSF" outputId="c85e1bf1-1c2b-404d-b059-edc68abea8c7"}
``` python
!pip install modin[all]
```

::: {.output .stream .stdout}
    Requirement already satisfied: modin[all] in /usr/local/lib/python3.10/dist-packages (0.26.0)
    Requirement already satisfied: pandas<2.2,>=2.1 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2.1.4)
    Requirement already satisfied: packaging>=21.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (23.2)
    Requirement already satisfied: numpy>=1.22.4 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (1.23.5)
    Requirement already satisfied: fsspec>=2022.05.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2023.6.0)
    Requirement already satisfied: psutil>=5.8.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (5.9.5)
    Requirement already satisfied: dask>=2.22.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2023.8.1)
    Requirement already satisfied: distributed>=2.22.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2023.8.1)
    Requirement already satisfied: ray[default]!=2.5.0,>=1.13.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (2.8.1)
    Requirement already satisfied: pyarrow>=7.0.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (10.0.1)
    Requirement already satisfied: pydantic<2 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (1.10.13)
    Requirement already satisfied: modin-spreadsheet>=0.1.0 in /usr/local/lib/python3.10/dist-packages (from modin[all]) (0.1.2)
    Requirement already satisfied: click>=8.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (8.1.7)
    Requirement already satisfied: cloudpickle>=1.5.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (2.2.1)
    Requirement already satisfied: partd>=1.2.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (1.4.1)
    Requirement already satisfied: pyyaml>=5.3.1 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (6.0.1)
    Requirement already satisfied: toolz>=0.10.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (0.12.0)
    Requirement already satisfied: importlib-metadata>=4.13.0 in /usr/local/lib/python3.10/dist-packages (from dask>=2.22.0->modin[all]) (7.0.0)
    Requirement already satisfied: jinja2>=2.10.3 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (3.1.2)
    Requirement already satisfied: locket>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (1.0.0)
    Requirement already satisfied: msgpack>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (1.0.7)
    Requirement already satisfied: sortedcontainers>=2.0.5 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (2.4.0)
    Requirement already satisfied: tblib>=1.6.0 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (3.0.0)
    Requirement already satisfied: tornado>=6.0.4 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (6.3.2)
    Requirement already satisfied: urllib3>=1.24.3 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (2.0.7)
    Requirement already satisfied: zict>=2.2.0 in /usr/local/lib/python3.10/dist-packages (from distributed>=2.22.0->modin[all]) (3.0.0)
    Requirement already satisfied: jupyter>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from modin-spreadsheet>=0.1.0->modin[all]) (1.0.0)
    Requirement already satisfied: notebook>=6.0.3 in /usr/local/lib/python3.10/dist-packages (from modin-spreadsheet>=0.1.0->modin[all]) (6.5.5)
    Requirement already satisfied: ipywidgets>=7.0.0 in /usr/local/lib/python3.10/dist-packages (from modin-spreadsheet>=0.1.0->modin[all]) (7.7.1)
    Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.10/dist-packages (from pandas<2.2,>=2.1->modin[all]) (2.8.2)
    Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.10/dist-packages (from pandas<2.2,>=2.1->modin[all]) (2023.3.post1)
    Requirement already satisfied: tzdata>=2022.1 in /usr/local/lib/python3.10/dist-packages (from pandas<2.2,>=2.1->modin[all]) (2023.3)
    Requirement already satisfied: typing-extensions>=4.2.0 in /usr/local/lib/python3.10/dist-packages (from pydantic<2->modin[all]) (4.5.0)
    Requirement already satisfied: filelock in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.13.1)
    Requirement already satisfied: jsonschema in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (4.19.2)
    Requirement already satisfied: protobuf!=3.19.5,>=3.15.3 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.20.3)
    Requirement already satisfied: aiosignal in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.3.1)
    Requirement already satisfied: frozenlist in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.4.0)
    Requirement already satisfied: requests in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (2.31.0)
    Requirement already satisfied: aiohttp>=3.7 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.9.1)
    Requirement already satisfied: aiohttp-cors in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.7.0)
    Requirement already satisfied: colorful in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.5.5)
    Requirement already satisfied: py-spy>=0.2.0 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.3.14)
    Requirement already satisfied: gpustat>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.1.1)
    Requirement already satisfied: opencensus in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.11.3)
    Requirement already satisfied: prometheus-client>=0.7.1 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.19.0)
    Requirement already satisfied: smart-open in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (6.4.0)
    Requirement already satisfied: virtualenv<20.21.1,>=20.0.24 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (20.21.0)
    Requirement already satisfied: grpcio>=1.42.0 in /usr/local/lib/python3.10/dist-packages (from ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.60.0)
    Requirement already satisfied: attrs>=17.3.0 in /usr/local/lib/python3.10/dist-packages (from aiohttp>=3.7->ray[default]!=2.5.0,>=1.13.0->modin[all]) (23.1.0)
    Requirement already satisfied: multidict<7.0,>=4.5 in /usr/local/lib/python3.10/dist-packages (from aiohttp>=3.7->ray[default]!=2.5.0,>=1.13.0->modin[all]) (6.0.4)
    Requirement already satisfied: yarl<2.0,>=1.0 in /usr/local/lib/python3.10/dist-packages (from aiohttp>=3.7->ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.9.4)
    Requirement already satisfied: async-timeout<5.0,>=4.0 in /usr/local/lib/python3.10/dist-packages (from aiohttp>=3.7->ray[default]!=2.5.0,>=1.13.0->modin[all]) (4.0.3)
    Requirement already satisfied: nvidia-ml-py>=11.450.129 in /usr/local/lib/python3.10/dist-packages (from gpustat>=1.0.0->ray[default]!=2.5.0,>=1.13.0->modin[all]) (12.535.133)
    Requirement already satisfied: blessed>=1.17.1 in /usr/local/lib/python3.10/dist-packages (from gpustat>=1.0.0->ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.20.0)
    Requirement already satisfied: zipp>=0.5 in /usr/local/lib/python3.10/dist-packages (from importlib-metadata>=4.13.0->dask>=2.22.0->modin[all]) (3.17.0)
    Requirement already satisfied: ipykernel>=4.5.1 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (5.5.6)
    Requirement already satisfied: ipython-genutils~=0.2.0 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.2.0)
    Requirement already satisfied: traitlets>=4.3.1 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (5.7.1)
    Requirement already satisfied: widgetsnbextension~=3.6.0 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (3.6.6)
    Requirement already satisfied: ipython>=4.0.0 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (7.34.0)
    Requirement already satisfied: jupyterlab-widgets>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (3.0.9)
    Requirement already satisfied: MarkupSafe>=2.0 in /usr/local/lib/python3.10/dist-packages (from jinja2>=2.10.3->distributed>=2.22.0->modin[all]) (2.1.3)
    Requirement already satisfied: qtconsole in /usr/local/lib/python3.10/dist-packages (from jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (5.5.1)
    Requirement already satisfied: jupyter-console in /usr/local/lib/python3.10/dist-packages (from jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (6.1.0)
    Requirement already satisfied: nbconvert in /usr/local/lib/python3.10/dist-packages (from jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (6.5.4)
    Requirement already satisfied: pyzmq<25,>=17 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (23.2.1)
    Requirement already satisfied: argon2-cffi in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (23.1.0)
    Requirement already satisfied: jupyter-core>=4.6.1 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (5.5.0)
    Requirement already satisfied: jupyter-client<8,>=5.3.4 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (6.1.12)
    Requirement already satisfied: nbformat in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (5.9.2)
    Requirement already satisfied: nest-asyncio>=1.5 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.5.8)
    Requirement already satisfied: Send2Trash>=1.8.0 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.8.2)
    Requirement already satisfied: terminado>=0.8.3 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (0.18.0)
    Requirement already satisfied: nbclassic>=0.4.7 in /usr/local/lib/python3.10/dist-packages (from notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.0.0)
    Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.10/dist-packages (from python-dateutil>=2.8.2->pandas<2.2,>=2.1->modin[all]) (1.16.0)
    Requirement already satisfied: distlib<1,>=0.3.6 in /usr/local/lib/python3.10/dist-packages (from virtualenv<20.21.1,>=20.0.24->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.3.8)
    Requirement already satisfied: platformdirs<4,>=2.4 in /usr/local/lib/python3.10/dist-packages (from virtualenv<20.21.1,>=20.0.24->ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.11.0)
    Requirement already satisfied: jsonschema-specifications>=2023.03.6 in /usr/local/lib/python3.10/dist-packages (from jsonschema->ray[default]!=2.5.0,>=1.13.0->modin[all]) (2023.11.2)
    Requirement already satisfied: referencing>=0.28.4 in /usr/local/lib/python3.10/dist-packages (from jsonschema->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.32.0)
    Requirement already satisfied: rpds-py>=0.7.1 in /usr/local/lib/python3.10/dist-packages (from jsonschema->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.13.2)
    Requirement already satisfied: opencensus-context>=0.1.3 in /usr/local/lib/python3.10/dist-packages (from opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.1.3)
    Requirement already satisfied: google-api-core<3.0.0,>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (2.11.1)
    Requirement already satisfied: charset-normalizer<4,>=2 in /usr/local/lib/python3.10/dist-packages (from requests->ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.3.2)
    Requirement already satisfied: idna<4,>=2.5 in /usr/local/lib/python3.10/dist-packages (from requests->ray[default]!=2.5.0,>=1.13.0->modin[all]) (3.6)
    Requirement already satisfied: certifi>=2017.4.17 in /usr/local/lib/python3.10/dist-packages (from requests->ray[default]!=2.5.0,>=1.13.0->modin[all]) (2023.11.17)
    Requirement already satisfied: wcwidth>=0.1.4 in /usr/local/lib/python3.10/dist-packages (from blessed>=1.17.1->gpustat>=1.0.0->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.2.12)
    Requirement already satisfied: googleapis-common-protos<2.0.dev0,>=1.56.2 in /usr/local/lib/python3.10/dist-packages (from google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (1.62.0)
    Requirement already satisfied: google-auth<3.0.dev0,>=2.14.1 in /usr/local/lib/python3.10/dist-packages (from google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (2.17.3)
    Requirement already satisfied: setuptools>=18.5 in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (67.7.2)
    Requirement already satisfied: jedi>=0.16 in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.19.1)
    Requirement already satisfied: decorator in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (4.4.2)
    Requirement already satisfied: pickleshare in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.7.5)
    Requirement already satisfied: prompt-toolkit!=3.0.0,!=3.0.1,<3.1.0,>=2.0.0 in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (3.0.43)
    Requirement already satisfied: pygments in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (2.16.1)
    Requirement already satisfied: backcall in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.2.0)
    Requirement already satisfied: matplotlib-inline in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.1.6)
    Requirement already satisfied: pexpect>4.3 in /usr/local/lib/python3.10/dist-packages (from ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (4.9.0)
    Requirement already satisfied: jupyter-server>=1.8 in /usr/local/lib/python3.10/dist-packages (from nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.24.0)
    Requirement already satisfied: notebook-shim>=0.2.3 in /usr/local/lib/python3.10/dist-packages (from nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (0.2.3)
    Requirement already satisfied: lxml in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (4.9.3)
    Requirement already satisfied: beautifulsoup4 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (4.11.2)
    Requirement already satisfied: bleach in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (6.1.0)
    Requirement already satisfied: defusedxml in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.7.1)
    Requirement already satisfied: entrypoints>=0.2.2 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.4)
    Requirement already satisfied: jupyterlab-pygments in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.3.0)
    Requirement already satisfied: mistune<2,>=0.8.1 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.8.4)
    Requirement already satisfied: nbclient>=0.5.0 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.9.0)
    Requirement already satisfied: pandocfilters>=1.4.1 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (1.5.0)
    Requirement already satisfied: tinycss2 in /usr/local/lib/python3.10/dist-packages (from nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (1.2.1)
    Requirement already satisfied: fastjsonschema in /usr/local/lib/python3.10/dist-packages (from nbformat->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (2.19.0)
    Requirement already satisfied: ptyprocess in /usr/local/lib/python3.10/dist-packages (from terminado>=0.8.3->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (0.7.0)
    Requirement already satisfied: argon2-cffi-bindings in /usr/local/lib/python3.10/dist-packages (from argon2-cffi->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (21.2.0)
    Requirement already satisfied: qtpy>=2.4.0 in /usr/local/lib/python3.10/dist-packages (from qtconsole->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (2.4.1)
    Requirement already satisfied: cachetools<6.0,>=2.0.0 in /usr/local/lib/python3.10/dist-packages (from google-auth<3.0.dev0,>=2.14.1->google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (5.3.2)
    Requirement already satisfied: pyasn1-modules>=0.2.1 in /usr/local/lib/python3.10/dist-packages (from google-auth<3.0.dev0,>=2.14.1->google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.3.0)
    Requirement already satisfied: rsa<5,>=3.1.4 in /usr/local/lib/python3.10/dist-packages (from google-auth<3.0.dev0,>=2.14.1->google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (4.9)
    Requirement already satisfied: parso<0.9.0,>=0.8.3 in /usr/local/lib/python3.10/dist-packages (from jedi>=0.16->ipython>=4.0.0->ipywidgets>=7.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.8.3)
    Requirement already satisfied: anyio<4,>=3.1.0 in /usr/local/lib/python3.10/dist-packages (from jupyter-server>=1.8->nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (3.7.1)
    Requirement already satisfied: websocket-client in /usr/local/lib/python3.10/dist-packages (from jupyter-server>=1.8->nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.7.0)
    Requirement already satisfied: cffi>=1.0.1 in /usr/local/lib/python3.10/dist-packages (from argon2-cffi-bindings->argon2-cffi->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.16.0)
    Requirement already satisfied: soupsieve>1.2 in /usr/local/lib/python3.10/dist-packages (from beautifulsoup4->nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (2.5)
    Requirement already satisfied: webencodings in /usr/local/lib/python3.10/dist-packages (from bleach->nbconvert->jupyter>=1.0.0->modin-spreadsheet>=0.1.0->modin[all]) (0.5.1)
    Requirement already satisfied: sniffio>=1.1 in /usr/local/lib/python3.10/dist-packages (from anyio<4,>=3.1.0->jupyter-server>=1.8->nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.3.0)
    Requirement already satisfied: exceptiongroup in /usr/local/lib/python3.10/dist-packages (from anyio<4,>=3.1.0->jupyter-server>=1.8->nbclassic>=0.4.7->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (1.2.0)
    Requirement already satisfied: pycparser in /usr/local/lib/python3.10/dist-packages (from cffi>=1.0.1->argon2-cffi-bindings->argon2-cffi->notebook>=6.0.3->modin-spreadsheet>=0.1.0->modin[all]) (2.21)
    Requirement already satisfied: pyasn1<0.6.0,>=0.4.6 in /usr/local/lib/python3.10/dist-packages (from pyasn1-modules>=0.2.1->google-auth<3.0.dev0,>=2.14.1->google-api-core<3.0.0,>=1.0.0->opencensus->ray[default]!=2.5.0,>=1.13.0->modin[all]) (0.5.1)
:::
:::

::: {.cell .markdown id="VFqhOi4QrBQ3"}
**Import Libraries:**

-   The code imports Modin pandas as pd, zipfile, and os modules for
    working with files and directories.
:::

::: {.cell .code id="4JyUGYXQmmeR"}
``` python
import modin.pandas as pd
```
:::

::: {.cell .code id="Dc1q0J1uWmTQ"}
``` python
import zipfile
import os
```
:::

::: {.cell .markdown id="fRaUXAEerj87"}
**Unzip Dataset:**

-   The code unzips the downloaded dataset using the zipfile module. The
    contents are extracted into a directory named \'spotify-charts\'.

**List Extracted Files:**

-   It lists the files present in the \'spotify-charts\' directory.
:::

::: {.cell .code id="reiUVd01Xz4l"}
``` python
# Path to the downloaded zip file
zip_file_path = 'spotify-charts.zip'

# Directory to extract the contents of the zip file
extracted_dir = 'spotify-charts'

# Unzip the file
with zipfile.ZipFile(zip_file_path, 'r') as zip_ref:
    zip_ref.extractall(extracted_dir)

# List the files in the extracted directory
extracted_files = os.listdir(extracted_dir)
```
:::

::: {.cell .markdown id="HQTDDWNErMhT"}
**Select and read CSV File:**

-   It filters and selects the CSV file from the list of extracted
    files.

-   The code reads the selected CSV file into a Modin DataFrame using
    pd.read_csv().
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="rUxsaUGlYYBT" outputId="100abf36-68ae-4494-9215-693c763daaf6"}
``` python
csv_file = [file for file in extracted_files if file.endswith('.csv')][0]
df = pd.read_csv(os.path.join(extracted_dir, csv_file))
```

::: {.output .stream .stderr}
    UserWarning: Ray execution environment not yet initialized. Initializing...
    To remove this warning, run the following python code before doing dataframe operations:

        import ray
        ray.init()

    UserWarning: The size of /dev/shm is too small (6133121024 bytes). The required size at least half of RAM (6804721664 bytes). Please, delete files in /dev/shm or increase size of /dev/shm with --shm-size in Docker. Also, you can can override the memory size for each Ray worker (in bytes) to the MODIN_MEMORY environment variable.
    2023-12-17 06:59:10,172	INFO worker.py:1673 -- Started a local Ray instance.
    2023-12-17 07:00:42,177	WARNING worker.py:2074 -- A worker died or was killed while executing a task by an unexpected system error. To troubleshoot the problem, check the logs for the dead worker. RayTask ID: 7bfe64c6d51abdce372e54081152d1f4fc00961201000000 Worker ID: be18a379cc5c2e4ddb7fb6370efca6022e1b6a86eb227ce75b744310 Node ID: ab372961f69c4b91ac399b9fd2b83d625dc596605f4390198be1fad6 Worker IP address: 172.28.0.12 Worker port: 35803 Worker PID: 65040 Worker exit type: SYSTEM_ERROR Worker exit detail: Worker unexpectedly exits with a connection error code 2. End of file. There are some potential root causes. (1) The process is killed by SIGKILL by OOM killer due to high memory usage. (2) ray stop --force is called. (3) The worker is crashed unexpectedly due to SIGSEGV or other unexpected errors.
    (raylet) [2023-12-17 07:01:10,094 E 64995 64995] (raylet) node_manager.cc:3035: 1 Workers (tasks / actors) killed due to memory pressure (OOM), 0 Workers crashed due to other reasons at node (ID: ab372961f69c4b91ac399b9fd2b83d625dc596605f4390198be1fad6, IP: 172.28.0.12) over the last time period. To see more information about the Workers killed on this node, use `ray logs raylet.out -ip 172.28.0.12`
    (raylet) 
    (raylet) Refer to the documentation on how to address the out of memory issue: https://docs.ray.io/en/latest/ray-core/scheduling/ray-oom-prevention.html. Consider provisioning more memory on this node or reducing task parallelism by requesting more CPUs per task. To adjust the kill threshold, set the environment variable `RAY_memory_usage_threshold` when starting Ray. To disable worker killing, set the environment variable `RAY_memory_monitor_refresh_ms` to zero.
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":399}" id="UTceNbkmY3yU" outputId="33fec201-7e7a-42fa-ac27-7538e58e5cd0"}
``` python
# Display the DataFrame
df.head()
```

::: {.output .execute_result execution_count="12"}
```{=html}
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>url</th>
      <th>region</th>
      <th>chart</th>
      <th>trend</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Chantaje (feat. Maluma)</td>
      <td>1</td>
      <td>2017-01-01</td>
      <td>Shakira</td>
      <td>https://open.spotify.com/track/6mICuAdrwEjh6Y6...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>SAME_POSITION</td>
      <td>253019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Vente Pa' Ca (feat. Maluma)</td>
      <td>2</td>
      <td>2017-01-01</td>
      <td>Ricky Martin</td>
      <td>https://open.spotify.com/track/7DM4BPaS7uofFul...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_UP</td>
      <td>223988.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Reggaetón Lento (Bailemos)</td>
      <td>3</td>
      <td>2017-01-01</td>
      <td>CNCO</td>
      <td>https://open.spotify.com/track/3AEZUABDXNtecAO...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_DOWN</td>
      <td>210943.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Safari</td>
      <td>4</td>
      <td>2017-01-01</td>
      <td>J Balvin, Pharrell Williams, BIA, Sky</td>
      <td>https://open.spotify.com/track/6rQSrBHf7HlZjtc...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>SAME_POSITION</td>
      <td>173865.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Shaky Shaky</td>
      <td>5</td>
      <td>2017-01-01</td>
      <td>Daddy Yankee</td>
      <td>https://open.spotify.com/track/58IL315gMSTD37D...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_UP</td>
      <td>153956.0</td>
    </tr>
  </tbody>
</table>
</div>
```
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="DBHySUhDpv6q" outputId="03674939-2fb1-4202-9f9c-59fc6c28781b"}
``` python
df.info()
```

::: {.output .stream .stdout}
    <class 'modin.pandas.dataframe.DataFrame'>
    RangeIndex: 26173514 entries, 0 to 26173513
    Data columns (total 9 columns):
     #   Column   Dtype  
    ---  ------   -----  
     0   title    object 
     1   rank     int64  
     2   date     object 
     3   artist   object 
     4   url      object 
     5   region   object 
     6   chart    object 
     7   trend    object 
     8   streams  float64
    dtypes: float64(1), int64(1), object(7)
    memory usage: 1.8+ GB
:::
:::

::: {.cell .markdown id="Fc2GH_v5sJqM"}
**Data columns:**

-   The DataFrame has 9 columns.

**Columns and Data Types:**

-   **title**: Object type, representing the title of songs.
-   **rank**: Int64 type, representing the rank.
-   **date**: Object type, representing dates.
-   **artist**: Object type, representing the artist associated with the
    data.
-   **url**: Object type, representing URLs.
-   **region**: Object type, representing a region.
-   **chart**: Object type, representing the song\'s chart.
-   **trend**: Object type, indicating the song position
-   **streams**: Float64 type, representing streaming data.

**Memory Usage:**

-   The dataset occupies approximately 1.8 gigabytes of memory.
:::

::: {.cell .markdown id="uXu0ay36rB7q"}
##### **Measure memory usage, computation time, and file size**
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="dJa2n54krIZp" outputId="b3618429-b056-4f93-a313-f04e9ba1dec6"}
``` python
pip install psutil
```

::: {.output .stream .stdout}
    Requirement already satisfied: psutil in /usr/local/lib/python3.10/dist-packages (5.9.5)
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="rFSnTJKsrQsj" outputId="1033becb-a757-455d-d401-9f588945930b"}
``` python
import time
import os
import psutil
import pandas as pd

# Record start time
start_time = time.time()

# Record end time
end_time = time.time()

# Calculate the time taken
load_time = end_time - start_time

# Print the time taken
print(f"Time taken to load the data: {load_time} seconds")

# Get memory usage
memory_usage = psutil.Process(os.getpid()).memory_info().rss
print(f"Memory usage: {memory_usage / (1024 * 1024):.2f} MB")

# Get file size
file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB
print(f"File size: {file_size:.2f} MB")

# Additional computation or analysis can be done on the loaded data here

# Remember to free up memory if you're done using the DataFrame
df = None

# Optionally, you can print CPU usage as well
cpu_percent = psutil.cpu_percent()
print(f"CPU Usage: {cpu_percent}%")
```

::: {.output .stream .stdout}
    Time taken to load the data: 4.029273986816406e-05 seconds
    Memory usage: 194.75 MB
    File size: 3322.10 MB
    CPU Usage: 67.9%
:::
:::

::: {.cell .markdown id="DbDjpgDwJaQY"}

------------------------------------------------------------------------
:::

::: {.cell .markdown id="2nqtVcDRIXY7"}
### 3. Strategies for Big Datasets {#3-strategies-for-big-datasets}

Apply five smart strategies to handle large datasets effectively
:::

::: {.cell .markdown id="F9DkOgC1IdMK"}
#### 3.1 Load Less Data: {#31-load-less-data}

Strategically load only the essential portions of the dataset to
optimize memory usage.
:::

::: {.cell .markdown id="s5yR1FBa27lW"}
**Specify column of interest**

-   We focused on to primary column such as title, rank, date, artist,
    region, streams and chart. You can find out the details of each
    columns on above.
:::

::: {.cell .code id="NZ22L2ksRaGR"}
``` python
# Specify columns of interest
columns_of_interest = ['title', 'rank', 'date', 'artist', 'region','streams','chart']
```
:::

::: {.cell .markdown id="FKcJUWHx3NfX"}
-   We load 100,000 rows here and read the dataset.
:::

::: {.cell .code id="hwxkHnNJAM2V"}
``` python
subset_size = 1000000
```
:::

::: {.cell .markdown id="RaetBbjzBxoR"}
-   We reads a subset of the CSV file with the specified columns and
    rows.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="YC3wqVOecAdq" outputId="42e390fe-21ab-4b50-c81b-43c736727dff"}
``` python

df = pd.read_csv(
    os.path.join(extracted_dir, csv_file),
    usecols=columns_of_interest,
    nrows=subset_size
)
```

::: {.output .stream .stderr}
    UserWarning: `read_*` implementation has mismatches with pandas:
    Data types of partitions are different! Please refer to the troubleshooting section of the Modin documentation to fix this issue.
:::
:::

::: {.cell .markdown id="0GjQWxJMDID6"}
##### Measure memory usage, computation time, and file size {#measure-memory-usage-computation-time-and-file-size}
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="y37WkSGGAjiT" outputId="c7314f0d-c0e5-477c-decb-e8900e2fd1fc"}
``` python

# Record end time
end_time = time.time()

# Calculate the time taken
load_time = end_time - start_time

# Print the time taken
print(f"Time taken to load the data: {load_time} seconds")

# Get memory usage
memory_usage = psutil.Process(os.getpid()).memory_info().rss
print(f"Memory usage: {memory_usage / (1024 * 1024):.2f} MB")

# Get file size
file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB
print(f"File size: {file_size:.2f} MB")

# Additional computation or analysis can be done on the loaded data here

# Remember to free up memory if you're done using the DataFrame
df = None

# Optionally, you can print CPU usage as well
cpu_percent = psutil.cpu_percent()
print(f"CPU Usage: {cpu_percent}%")
```

::: {.output .stream .stdout}
    Time taken to load the data: 2.546340227127075 seconds
    Memory usage: 342.62 MB
    File size: 3322.10 MB
    CPU Usage: 60.2%
:::
:::

::: {.cell .markdown id="QtyuqSxT3a8v"}
-   Drop duplicates row.
:::

::: {.cell .code id="OkHpPmH7m6C0"}
``` python
# Dealing with Duplicates
df.drop_duplicates(inplace=True)
```
:::

::: {.cell .markdown id="qgoTNpcHCOv0"}
-   Replaces missing values in numeric columns with the mean and in
    string columns with the mode.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="fXKGI1ml_kh1" outputId="e7b5f406-945b-41ba-dc35-4ceb7462042c"}
``` python
# Replace missing values with mean for numeric columns
import numpy as np

numeric_cols = df.select_dtypes(include=np.number).columns
df[numeric_cols] = df[numeric_cols].fillna(df[numeric_cols].mean())
```

::: {.output .stream .stderr}
    UserWarning: `DataFrame.setitem_unhashable_key` is not currently supported by PandasOnRay, defaulting to pandas implementation.
    Please refer to https://modin.readthedocs.io/en/stable/supported_apis/defaulting_to_pandas.html for explanation.
    UserWarning: Distributing <class 'pandas.core.frame.DataFrame'> object. This may take some time.
:::
:::

::: {.cell .markdown id="q5Q8o8k1CQlc"}
-   Replaces missing values in object columns with the mean and in
    string columns with the mode.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="8G6saM9qA08H" outputId="7b08d78e-1c14-4b30-98be-8f05e78d8ac8"}
``` python
# Replace missing values with mode for string columns in the subset
string_cols = df.select_dtypes(include='object').columns
df[string_cols] = df[string_cols].fillna(df[string_cols].mode().iloc[0])
```

::: {.output .stream .stderr}
    UserWarning: `DataFrame.setitem_unhashable_key` is not currently supported by PandasOnRay, defaulting to pandas implementation.
    UserWarning: Distributing <class 'pandas.core.frame.DataFrame'> object. This may take some time.
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="Z1qrXWSDwxLf" outputId="40c21619-0c20-407d-dbb9-29e6e20d1cb7"}
``` python
df['date'] = pd.to_datetime(df['date'])

df.info()
```

::: {.output .stream .stdout}
    <class 'modin.pandas.dataframe.DataFrame'>
    RangeIndex: 1000000 entries, 0 to 999999
    Data columns (total 7 columns):
     #   Column   Non-Null Count    Dtype         
    ---  ------   --------------    -----         
     0   title    1000000 non-null  object        
     1   rank     1000000 non-null  int64         
     2   date     1000000 non-null  datetime64[ns]
     3   artist   1000000 non-null  object        
     4   region   1000000 non-null  object        
     5   chart    1000000 non-null  object        
     6   streams  1000000 non-null  float64       
    dtypes: datetime64[ns](1), float64(1), int64(1), object(4)
    memory usage: 53.4+ MB
:::
:::

::: {.cell .markdown id="p0FUv-IcDBC9"}
-   This dataset contain year from 2017 - 2021
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="11aueAS3Cu5-" outputId="37bad667-c235-4e5e-e120-d061941b3e27"}
``` python
unique_years = df['date'].dt.year.unique()

# Display the unique years
print(unique_years)
```

::: {.output .stream .stdout}
    [2017 2018 2020 2019 2021]
:::
:::

::: {.cell .markdown id="I0_T5kosCb9V"}
-   Here, we only focus to Malaysia region and chart top200 from 2017 -
    2021.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":206}" id="bg06xmfi9Lqq" outputId="a0db025b-06bc-461c-c2a8-87e2e12cffb7"}
``` python
spotify_my_top200 = df[(df['region'] == 'Malaysia') & (df['chart'] == 'top200')]

spotify_my_top200.head()
```

::: {.output .execute_result execution_count="21"}
```{=html}
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>region</th>
      <th>chart</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4755</th>
      <td>Mercy</td>
      <td>23</td>
      <td>2017-01-01</td>
      <td>Shawn Mendes</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>12925.0</td>
    </tr>
    <tr>
      <th>4784</th>
      <td>Closer</td>
      <td>1</td>
      <td>2017-01-01</td>
      <td>The Chainsmokers, Halsey</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>27062.0</td>
    </tr>
    <tr>
      <th>4785</th>
      <td>Say You Won't Let Go</td>
      <td>2</td>
      <td>2017-01-01</td>
      <td>James Arthur</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>26577.0</td>
    </tr>
    <tr>
      <th>4786</th>
      <td>Starboy</td>
      <td>3</td>
      <td>2017-01-01</td>
      <td>The Weeknd, Daft Punk</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>24878.0</td>
    </tr>
    <tr>
      <th>4787</th>
      <td>Let Me Love You</td>
      <td>4</td>
      <td>2017-01-01</td>
      <td>DJ Snake, Justin Bieber</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>22310.0</td>
    </tr>
  </tbody>
</table>
</div>
```
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":206}" id="C19XwATDcE0s" outputId="899e7ae9-175c-4658-be3f-545a86e07f50"}
``` python
spotify_my_top200.tail()
```

::: {.output .execute_result execution_count="22"}
```{=html}
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>region</th>
      <th>chart</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>998838</th>
      <td>Bodak Yellow</td>
      <td>196</td>
      <td>2018-02-13</td>
      <td>Cardi B</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>4412.0</td>
    </tr>
    <tr>
      <th>998839</th>
      <td>Bartier Cardi (feat. 21 Savage)</td>
      <td>197</td>
      <td>2018-02-13</td>
      <td>Cardi B</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>4410.0</td>
    </tr>
    <tr>
      <th>998840</th>
      <td>2U (feat. Justin Bieber)</td>
      <td>198</td>
      <td>2018-02-13</td>
      <td>David Guetta</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>4401.0</td>
    </tr>
    <tr>
      <th>998841</th>
      <td>Berakhirlah Sudah</td>
      <td>199</td>
      <td>2018-02-13</td>
      <td>Atmosfera</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>4400.0</td>
    </tr>
    <tr>
      <th>998842</th>
      <td>She Loves Control</td>
      <td>200</td>
      <td>2018-02-13</td>
      <td>Camila Cabello</td>
      <td>Malaysia</td>
      <td>top200</td>
      <td>4389.0</td>
    </tr>
  </tbody>
</table>
</div>
```
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="DgYTjj8LeZR7" outputId="ab7063ca-7f29-4a26-a8e6-52e44485522c"}
``` python
spotify_my_top200.info()
```

::: {.output .stream .stdout}
    <class 'modin.pandas.dataframe.DataFrame'>
    Index: 16902 entries, 4755 to 998842
    Data columns (total 7 columns):
     #   Column   Non-Null Count  Dtype         
    ---  ------   --------------  -----         
     0   title    16902 non-null  object        
     1   rank     16902 non-null  int64         
     2   date     16902 non-null  datetime64[ns]
     3   artist   16902 non-null  object        
     4   region   16902 non-null  object        
     5   chart    16902 non-null  object        
     6   streams  16902 non-null  float64       
    dtypes: datetime64[ns](1), float64(1), int64(1), object(4)
    memory usage: 1.0+ MB
:::
:::

::: {.cell .markdown id="joppKD3WYRCd"}
##### Measure memory usage, computation time, and file size {#measure-memory-usage-computation-time-and-file-size}
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="aAVsuE5w7qlu" outputId="2d436b57-c964-406f-bfa6-4c4f05d5fb60"}
``` python
!pip install psutil
```

::: {.output .stream .stdout}
    Requirement already satisfied: psutil in /usr/local/lib/python3.10/dist-packages (5.9.5)
:::
:::

::: {.cell .code id="lSp-J9v-7tdq"}
``` python
import psutil
```
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="jQ5Y9MZiA33L" outputId="f298f874-cddd-4459-cd1d-b9565781c547"}
``` python
# Record end time
end_time = time.time()

# Calculate the time taken
load_time = end_time - start_time

# Print the time taken
print(f"Time taken to load the data: {load_time} seconds")

# Get memory usage
memory_usage = psutil.Process(os.getpid()).memory_info().rss
print(f"Memory usage: {memory_usage / (1024 * 1024):.2f} MB")

# Get file size
file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB
print(f"File size: {file_size:.2f} MB")

# Additional computation or analysis can be done on the loaded data here

# Remember to free up memory if you're done using the DataFrame
df = None

# Optionally, you can print CPU usage as well
cpu_percent = psutil.cpu_percent()
print(f"CPU Usage: {cpu_percent}%")
```

::: {.output .stream .stdout}
    Time taken to load the data: 196.5192108154297 seconds
    Memory usage: 413.34 MB
    File size: 3322.10 MB
    CPU Usage: 19.7%
:::
:::

::: {.cell .markdown id="zaDI9UBy4NWp"}
The entire DataFrame is reported to consume approximately 1.0+ MB of
memory. This indicates that the data is relatively small and should be
manageable for analysis and exploration.
:::

::: {.cell .markdown id="gf2J7DVsIodN"}
#### 3.2 Use Chunking {#32-use-chunking}

Process the data in smaller pieces to avoid memory issues.
:::

::: {.cell .markdown id="tYditx9R6SSI"}
**Import Modules**

-   We import the necessary modules (os and pandas as pd) to help with
    file operations and data processing.

-   \'os\' provides a way to interact with the operating system, in this
    case, to join file paths.
:::

::: {.cell .code id="LRHwNZ6AJCzM"}
``` python
import os
```
:::

::: {.cell .markdown id="Q-9FBDN96bWy"}
**Set Chunk Size:**

-   We decide to process the data in smaller parts, called chunks. Each
    chunk contains 100,000 rows of data.
:::

::: {.cell .code id="khdyqqvxdJOf"}
``` python
# Chunk size
chunk_size = 100000
```
:::

::: {.cell .markdown id="rQOuKTRN6f31"}
**Create Storage for Processed Data:**

We create an empty list (chunks) to store the processed parts of the
dataset.
:::

::: {.cell .code id="ISftzCa86nlv"}
``` python
# Initialize an empty list to store chunks
chunks = []
```
:::

::: {.cell .markdown id="ZEfZfX3j6tjA"}
**Read the Dataset:**

-   We read a large dataset from a file, selecting only the columns
    we\'re interested in.
:::

::: {.cell .code id="GCS_S8X5dM4T"}
``` python
df = pd.read_csv(os.path.join(extracted_dir, csv_file), usecols=columns_of_interest)
```
:::

::: {.cell .markdown id="DLoZFqXyDjqp"}
##### Measure memory usage, computation time, and file size {#measure-memory-usage-computation-time-and-file-size}
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="zFoVZ2KpCSW1" outputId="4453f139-d7ba-45a4-86b1-0ee62ea28c7e"}
``` python
# Record end time
end_time = time.time()

# Calculate the time taken
load_time = end_time - start_time

# Print the time taken
print(f"Time taken to load the data: {load_time} seconds")

# Get memory usage
memory_usage = psutil.Process(os.getpid()).memory_info().rss
print(f"Memory usage: {memory_usage / (1024 * 1024):.2f} MB")

# Get file size
file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB
print(f"File size: {file_size:.2f} MB")

# Optionally, you can print CPU usage as well
cpu_percent = psutil.cpu_percent()
print(f"CPU Usage: {cpu_percent}%")

# Additional computation or analysis can be done on the loaded data here

# Remember to free up memory if you're done using the DataFrame
df = None
```

::: {.output .stream .stdout}
    Time taken to load the data: 267.078076839447 seconds
    Memory usage: 3656.25 MB
    File size: 3322.10 MB
    CPU Usage: 69.2%
:::
:::

::: {.cell .markdown id="2sZmveds6xKR"}
**Process Data in Chunks:**

-   We go through the dataset in chunks, processing one chunk at a time.
    For each chunk, we filter out rows where the \'rank\' is greater
    than 10.

-   We store each processed chunk in the chunks list.
:::

::: {.cell .code id="wyHR_bDke8EP"}
``` python
# Process the data in chunks using iloc
start_idx = 0
while start_idx < len(df):
    end_idx = start_idx + chunk_size
    processed_chunk = df.iloc[start_idx:end_idx]

    processed_chunk = processed_chunk[processed_chunk['rank'] <= 10]  # Filter rows where rank is less than or equal to 10

    # Store the processed chunk in the list
    chunks.append(processed_chunk)

    start_idx = end_idx
```
:::

::: {.cell .markdown id="q_iz_FQG7BAO"}
**Combine Processed Chunks:**

Finally, we combine all the processed chunks into a single dataset
(result_df).
:::

::: {.cell .code id="8G_7V9gefFmm"}
``` python
# Concatenate the processed chunks into a single DataFrame
result_df = pd.concat(chunks, ignore_index=True)
```
:::

::: {.cell .markdown id="bNP-sDx17GID"}
**Result of chunk:**
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="ubvX1GwUlInK" outputId="1cc63ad6-9d50-4e65-d046-a60e452171e3"}
``` python
result_df.info()
```

::: {.output .stream .stdout}
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4543752 entries, 0 to 4543751
    Data columns (total 7 columns):
     #   Column   Dtype  
    ---  ------   -----  
     0   title    object 
     1   rank     int64  
     2   date     object 
     3   artist   object 
     4   region   object 
     5   chart    object 
     6   streams  float64
    dtypes: float64(1), int64(1), object(5)
    memory usage: 242.7+ MB
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":206}" id="v8kkGb9wliCd" outputId="cb74c178-03d0-4fd1-bb53-d48e6c3e6739"}
``` python
result_df.head()
```

::: {.output .execute_result execution_count="59"}
```{=html}

  <div id="df-9fc5682c-db53-451b-b9e8-2623219cc86b" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>region</th>
      <th>chart</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Chantaje (feat. Maluma)</td>
      <td>1</td>
      <td>2017-01-01</td>
      <td>Shakira</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>253019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Vente Pa' Ca (feat. Maluma)</td>
      <td>2</td>
      <td>2017-01-01</td>
      <td>Ricky Martin</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>223988.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Reggaetón Lento (Bailemos)</td>
      <td>3</td>
      <td>2017-01-01</td>
      <td>CNCO</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>210943.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Safari</td>
      <td>4</td>
      <td>2017-01-01</td>
      <td>J Balvin, Pharrell Williams, BIA, Sky</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>173865.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Shaky Shaky</td>
      <td>5</td>
      <td>2017-01-01</td>
      <td>Daddy Yankee</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>153956.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-9fc5682c-db53-451b-b9e8-2623219cc86b')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-9fc5682c-db53-451b-b9e8-2623219cc86b button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-9fc5682c-db53-451b-b9e8-2623219cc86b');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-af7ec76d-464a-4612-878e-eab4e9e25d5b">
  <button class="colab-df-quickchart" onclick="quickchart('df-af7ec76d-464a-4612-878e-eab4e9e25d5b')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-af7ec76d-464a-4612-878e-eab4e9e25d5b button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>
```
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":206}" id="0bj6QvPDlqhh" outputId="0efc2ac2-a5c9-4e62-80e5-8bcc17695f47"}
``` python
result_df.tail()
```

::: {.output .execute_result execution_count="60"}
```{=html}

  <div id="df-0da5f383-159e-4c15-9c92-8eaab1121da7" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>region</th>
      <th>chart</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4543747</th>
      <td>Giấc Mơ Rất Thơ</td>
      <td>5</td>
      <td>2021-07-31</td>
      <td>Mer, thaison!</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4543748</th>
      <td>Nevertheless</td>
      <td>6</td>
      <td>2021-07-31</td>
      <td>Night Off</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4543749</th>
      <td>Your Sunday (Sunday Morning) [feat. Ampoff]</td>
      <td>7</td>
      <td>2021-07-31</td>
      <td>Sunny Shin</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4543750</th>
      <td>We're Already</td>
      <td>8</td>
      <td>2021-07-31</td>
      <td>KIMMUSEUM</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4543751</th>
      <td>Happy For You (feat. Vũ.)</td>
      <td>9</td>
      <td>2021-07-31</td>
      <td>Lukas Graham</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-0da5f383-159e-4c15-9c92-8eaab1121da7')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-0da5f383-159e-4c15-9c92-8eaab1121da7 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-0da5f383-159e-4c15-9c92-8eaab1121da7');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-80660003-61b5-491d-897d-56bbb518c4fe">
  <button class="colab-df-quickchart" onclick="quickchart('df-80660003-61b5-491d-897d-56bbb518c4fe')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-80660003-61b5-491d-897d-56bbb518c4fe button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>
```
:::
:::

::: {.cell .markdown id="sbZAiYun7POa"}
**Replace NaN with mean**

-   We can see that the dataframe above have NaN value. Therefore, we
    decide to replace it with mean.
:::

::: {.cell .code id="_rt-r0fbmEPO"}
``` python
# Calculate the mean of the 'streams' column (excluding NaN values)
mean_streams = result_df['streams'].mean()

# Fill NaN values in the 'streams' column with the mean value
result_df['streams'].fillna(mean_streams, inplace=True)
```
:::

::: {.cell .markdown id="BCl8EUg27k09"}
**Result :**
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":293}" id="ZF5Rwiu8mJuM" outputId="7824bd46-72f5-4f9b-ccd9-f007fc606f1a"}
``` python
result_df.tail()
```

::: {.output .execute_result execution_count="62"}
```{=html}

  <div id="df-877bf1f8-074d-4ee6-ad83-209af25b34f8" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>region</th>
      <th>chart</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4543747</th>
      <td>Giấc Mơ Rất Thơ</td>
      <td>5</td>
      <td>2021-07-31</td>
      <td>Mer, thaison!</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>172593.778362</td>
    </tr>
    <tr>
      <th>4543748</th>
      <td>Nevertheless</td>
      <td>6</td>
      <td>2021-07-31</td>
      <td>Night Off</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>172593.778362</td>
    </tr>
    <tr>
      <th>4543749</th>
      <td>Your Sunday (Sunday Morning) [feat. Ampoff]</td>
      <td>7</td>
      <td>2021-07-31</td>
      <td>Sunny Shin</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>172593.778362</td>
    </tr>
    <tr>
      <th>4543750</th>
      <td>We're Already</td>
      <td>8</td>
      <td>2021-07-31</td>
      <td>KIMMUSEUM</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>172593.778362</td>
    </tr>
    <tr>
      <th>4543751</th>
      <td>Happy For You (feat. Vũ.)</td>
      <td>9</td>
      <td>2021-07-31</td>
      <td>Lukas Graham</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>172593.778362</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-877bf1f8-074d-4ee6-ad83-209af25b34f8')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-877bf1f8-074d-4ee6-ad83-209af25b34f8 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-877bf1f8-074d-4ee6-ad83-209af25b34f8');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-207e11ce-41bf-46df-a6b3-2d43d060c19f">
  <button class="colab-df-quickchart" onclick="quickchart('df-207e11ce-41bf-46df-a6b3-2d43d060c19f')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-207e11ce-41bf-46df-a6b3-2d43d060c19f button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>
```
:::
:::

::: {.cell .markdown id="5jZb9kr9Pe7B"}
-   The NaN value has been replaced with mean value
:::

::: {.cell .markdown id="nXh0oAKgIsir"}
#### 3.3 Optimize Data Types {#33-optimize-data-types}

Fine-tune data types to maximize efficiency and minimize memory
consumption.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="fLKbVOxmJDRm" outputId="a37e5301-ee05-4d45-95b7-716c1328e96e"}
``` python
result_df.info()
```

::: {.output .stream .stdout}
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4543752 entries, 0 to 4543751
    Data columns (total 7 columns):
     #   Column   Dtype  
    ---  ------   -----  
     0   title    object 
     1   rank     int64  
     2   date     object 
     3   artist   object 
     4   region   object 
     5   chart    object 
     6   streams  float64
    dtypes: float64(1), int64(1), object(5)
    memory usage: 242.7+ MB
:::
:::

::: {.cell .markdown id="jVnLTpCjDxte"}
##### Measure memory usage, computation time, and file size {#measure-memory-usage-computation-time-and-file-size}
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="6KbWWHZgDysF" outputId="4c597ac5-9f7d-440b-933a-761509bf4eac"}
``` python
# Record start time
start_time = time.time()

# Read the data using Pandas
result_df = pd.read_csv(
    os.path.join(extracted_dir, csv_file),
    usecols=columns_of_interest
)

# Record end time
end_time = time.time()

# Calculate the time taken
load_time = end_time - start_time

# Print the time taken
print(f"Time taken to load the data: {load_time} seconds")

# Get memory usage
memory_usage = psutil.Process(os.getpid()).memory_info().rss
print(f"Memory usage: {memory_usage / (1024 * 1024):.2f} MB")

# Get file size
file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB
print(f"File size: {file_size:.2f} MB")

# Optionally, you can print CPU usage as well
cpu_percent = psutil.cpu_percent()
print(f"CPU Usage: {cpu_percent}%")

# Additional computation or analysis can be done on the loaded data here

# Remember to free up memory if you're done using the DataFrame
result_df = None
```

::: {.output .stream .stdout}
    Time taken to load the data: 72.01772570610046 seconds
    Memory usage: 5784.59 MB
    File size: 3322.10 MB
    CPU Usage: 52.1%
:::
:::

::: {.cell .markdown id="GenlPswU78_6"}
**Select Rank column**

-   Downcasts the numeric values to the smallest integer type that can
    safely represent them. In this case, it downcasts from int64 to
    int16, saving memory.
:::

::: {.cell .code id="W4d4k9_l0-KK"}
``` python
result_df['rank'] = pd.to_numeric(result_df['rank'], downcast='integer')  # Convert int64 to int16
```
:::

::: {.cell .markdown id="EchbU3a88OFS"}
**Select Stream column**

-   Downcasts the numeric values to the smallest floating-point type
    that can safely represent them. In this case, it downcasts from
    float64 to float, saving memory.
:::

::: {.cell .code id="5HScL7pQ1ieZ"}
``` python
result_df['streams'] = pd.to_numeric(result_df['streams'], downcast='float')  # Convert float64 to float
```
:::

::: {.cell .markdown id="OQqFOy358XjM"}
**Select Date column**

-   We converts the values in the selected column to datetime format. If
    a value cannot be converted to datetime, it will be set to NaT (Not
    a Time).

-   If there are errors in conversion, set the problematic values to
    NaT.
:::

::: {.cell .code id="0s82Uybq1Zqo"}
``` python
# Convert 'date' to datetime if it's not already
result_df['date'] = pd.to_datetime(result_df['date'], errors='coerce')
```
:::

::: {.cell .markdown id="9Qypb8YO8i7c"}
**Result:**
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="to9VWDwI1jxg" outputId="3a101291-3b1a-48fb-f0dd-3a0342e3c024"}
``` python
# Display data types and memory usage after optimization
result_df.info()
```

::: {.output .stream .stdout}
    <class 'modin.pandas.dataframe.DataFrame'>
    RangeIndex: 2271876 entries, 0 to 2271875
    Data columns (total 7 columns):
     #   Column   Dtype         
    ---  ------   -----         
     0   title    object        
     1   rank     int8          
     2   date     datetime64[ns]
     3   artist   object        
     4   region   object        
     5   chart    object        
     6   streams  float64       
    dtypes: datetime64[ns](1), float64(1), int8(1), object(4)
    memory usage: 101.8+ MB
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":206}" id="NwjvBi492Ifg" outputId="bb5c6e73-0427-4f1a-b3e7-04b9f8177d17"}
``` python
result_df.head()
```

::: {.output .execute_result execution_count="68"}
```{=html}

  <div id="df-f6cf3800-dc0b-4850-9e18-18d4bd9396e8" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>region</th>
      <th>chart</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Chantaje (feat. Maluma)</td>
      <td>1</td>
      <td>2017-01-01</td>
      <td>Shakira</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>253019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Vente Pa' Ca (feat. Maluma)</td>
      <td>2</td>
      <td>2017-01-01</td>
      <td>Ricky Martin</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>223988.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Reggaetón Lento (Bailemos)</td>
      <td>3</td>
      <td>2017-01-01</td>
      <td>CNCO</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>210943.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Safari</td>
      <td>4</td>
      <td>2017-01-01</td>
      <td>J Balvin, Pharrell Williams, BIA, Sky</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>173865.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Shaky Shaky</td>
      <td>5</td>
      <td>2017-01-01</td>
      <td>Daddy Yankee</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>153956.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-f6cf3800-dc0b-4850-9e18-18d4bd9396e8')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-f6cf3800-dc0b-4850-9e18-18d4bd9396e8 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-f6cf3800-dc0b-4850-9e18-18d4bd9396e8');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-4bdc6813-4130-4d02-93ab-ea8d87c40757">
  <button class="colab-df-quickchart" onclick="quickchart('df-4bdc6813-4130-4d02-93ab-ea8d87c40757')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-4bdc6813-4130-4d02-93ab-ea8d87c40757 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>
```
:::
:::

::: {.cell .markdown id="blJUSISSIv-l"}
#### 3.4 Sampling {#34-sampling}

Implement sampling methodologies to extract meaningful insights from a
subset of the dataset.
:::

::: {.cell .markdown id="MMbmejkG81E0"}
**Randomly select a fraction row from the DataFrame**

-   Here, we specifies that we want to sample 10% of the total rows. You
    can adjust this percentage based on your needs.

-   We also sets a random seed for reproducibility (random_state=42) .
    Using the same seed ensures that if you run the code again, you\'ll
    get the same set of randomly selected rows.
:::

::: {.cell .code id="MHKJHGPKJDv3"}
``` python
# Sample a fraction of the DataFrame (e.g., 10%)
sampled_df = result_df.sample(frac=0.1, random_state=42)
```
:::

::: {.cell .markdown id="7cSORzzY9fRD"}
**Result:**
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="khsAxH--2giZ" outputId="de0b4ef5-940d-48f4-88fc-a8d4537b47e5"}
``` python
# Display the info after sampling
print(sampled_df.info())
```

::: {.output .stream .stdout}
    <class 'modin.pandas.dataframe.DataFrame'>
    Index: 227188 entries, 783985 to 946668
    Data columns (total 7 columns):
     #   Column   Non-Null Count   Dtype         
    ---  ------   --------------   -----         
     0   title    227188 non-null  object        
     1   rank     227188 non-null  int8          
     2   date     227188 non-null  datetime64[ns]
     3   artist   227187 non-null  object        
     4   region   227188 non-null  object        
     5   chart    227188 non-null  object        
     6   streams  109973 non-null  float64       
    dtypes: datetime64[ns](1), float64(1), int8(1), object(4)
    memory usage: 12.3+ MB
    None
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":206}" id="UU2iWN0b2mNU" outputId="2ca2507a-d008-4ae0-ca93-6c2aef09f37c"}
``` python
# Display the first few rows of the sampled DataFrame
sampled_df.head()
```

::: {.output .execute_result execution_count="38"}
```{=html}
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>region</th>
      <th>chart</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>783985</th>
      <td>Materyal</td>
      <td>9</td>
      <td>2017-12-23</td>
      <td>Shanti Dope</td>
      <td>Philippines</td>
      <td>viral50</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>874461</th>
      <td>Missing U</td>
      <td>3</td>
      <td>2018-08-07</td>
      <td>Robyn</td>
      <td>Hungary</td>
      <td>viral50</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>568462</th>
      <td>Shape of You</td>
      <td>2</td>
      <td>2017-03-06</td>
      <td>Ed Sheeran</td>
      <td>Ecuador</td>
      <td>top200</td>
      <td>24437.0</td>
    </tr>
    <tr>
      <th>2089873</th>
      <td>Paparazzi</td>
      <td>8</td>
      <td>2021-01-31</td>
      <td>Kim Dracula</td>
      <td>Denmark</td>
      <td>viral50</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>542887</th>
      <td>Ahora Dice</td>
      <td>7</td>
      <td>2017-08-05</td>
      <td>Chris Jedi, J Balvin, Ozuna, Arcangel</td>
      <td>Mexico</td>
      <td>top200</td>
      <td>329388.0</td>
    </tr>
  </tbody>
</table>
</div>
```
:::
:::

::: {.cell .markdown id="5soFlDuEYdK0"}
##### Measure memory usage, computation time, and file size {#measure-memory-usage-computation-time-and-file-size}
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="T5UmJQmLHcBw" outputId="34d77c77-3779-4d33-f905-31b04064b9cf"}
``` python
import time
import psutil
# Record start time
start_time = time.time()
# Record end time
end_time = time.time()

# Calculate the time taken
load_time = end_time - start_time

# Print the time taken
print(f"Time taken to load the data: {load_time} seconds")

# Get memory usage
memory_usage = psutil.Process(os.getpid()).memory_info().rss
print(f"Memory usage: {memory_usage / (1024 * 1024):.2f} MB")

# Get file size
file_size = os.path.getsize(os.path.join(extracted_dir, csv_file)) / (1024 * 1024)  # in MB
print(f"File size: {file_size:.2f} MB")

# Optionally, you can print CPU usage as well
cpu_percent = psutil.cpu_percent()
print(f"CPU Usage: {cpu_percent}%")

# Additional computation or analysis can be done on the loaded data here

# Remember to free up memory if you're done using the DataFrame
sampled_df = None
```

::: {.output .stream .stdout}
    Time taken to load the data: 8.296966552734375e-05 seconds
    Memory usage: 2161.80 MB
    File size: 3322.10 MB
    CPU Usage: 78.0%
:::
:::

::: {.cell .markdown id="hyXSmlQRyM1Z"}

------------------------------------------------------------------------
:::

::: {.cell .markdown id="YuTYTOt_I0nO"}
#### 3.5 Parallelize with Dask {#35-parallelize-with-dask}

Dask is a powerful library that extends pandas to enable parallel and
distributed computing. It\'s particularly useful for handling
larger-than-memory datasets.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="mtUhj3QUJEQn" outputId="3fa7b0b0-af89-4e35-9669-a3fbe2434b9b"}
``` python
!pip install dask
```

::: {.output .stream .stdout}
    Requirement already satisfied: dask in /usr/local/lib/python3.10/dist-packages (2023.8.1)
    Requirement already satisfied: click>=8.0 in /usr/local/lib/python3.10/dist-packages (from dask) (8.1.7)
    Requirement already satisfied: cloudpickle>=1.5.0 in /usr/local/lib/python3.10/dist-packages (from dask) (2.2.1)
    Requirement already satisfied: fsspec>=2021.09.0 in /usr/local/lib/python3.10/dist-packages (from dask) (2023.6.0)
    Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.10/dist-packages (from dask) (23.2)
    Requirement already satisfied: partd>=1.2.0 in /usr/local/lib/python3.10/dist-packages (from dask) (1.4.1)
    Requirement already satisfied: pyyaml>=5.3.1 in /usr/local/lib/python3.10/dist-packages (from dask) (6.0.1)
    Requirement already satisfied: toolz>=0.10.0 in /usr/local/lib/python3.10/dist-packages (from dask) (0.12.0)
    Requirement already satisfied: importlib-metadata>=4.13.0 in /usr/local/lib/python3.10/dist-packages (from dask) (7.0.0)
    Requirement already satisfied: zipp>=0.5 in /usr/local/lib/python3.10/dist-packages (from importlib-metadata>=4.13.0->dask) (3.17.0)
    Requirement already satisfied: locket in /usr/local/lib/python3.10/dist-packages (from partd>=1.2.0->dask) (1.0.0)
:::
:::

::: {.cell .markdown id="b-3zZeEksw3Q"}
-   Here, we\'re importing the Dask DataFrame module and assigning it
    the alias dd. Dask is a parallel computing library that integrates
    with Pandas and allows for parallel processing of large datasets.
:::

::: {.cell .code id="4jbWo9kb23ob"}
``` python
import dask.dataframe as dd

# Load the dataset into a Dask DataFrame
ddf = dd.read_csv(os.path.join(extracted_dir, csv_file), usecols=columns_of_interest)
```
:::

::: {.cell .code id="FwNbFhRC0SJO"}
``` python
file_path = 'spotify-charts/charts.csv'
df = dd.read_csv(file_path)
```
:::

::: {.cell .markdown id="IfmvfC0MYgso"}
##### Measure memory usage, computation time, and file size {#measure-memory-usage-computation-time-and-file-size}
:::

::: {.cell .markdown id="QJsfFrA-tgtr"}
-   Here, we\'re importing the time module, which allows us to work with
    time-related functions.

-   We measures how long it takes to load data from a CSV file using
    Dask. The start time is noted, the data is loaded, the end time is
    noted, and the difference between the start and end times gives us
    the time taken for the data loading process.
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="k2k52BD_pKmL" outputId="0bb3eb1f-6888-4e94-ebe4-b937a26aa273"}
``` python
import time

# Record start time
start_time = time.time()

# Load the data using Dask
df = dd.read_csv(file_path)

# Record end time
end_time = time.time()

# Calculate the time taken
load_time = end_time - start_time

# Print the time taken
print(f"Time taken to load the data: {load_time} seconds")
```

::: {.output .stream .stdout}
    Time taken to load the data: 0.016971349716186523 seconds
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="l8khNu-U8i3h" outputId="b5cab49d-c134-43ae-aaf3-0281ee86ef53"}
``` python
# Get memory usage
memory_usage = psutil.Process(os.getpid()).memory_info().rss
print(f"Memory usage: {memory_usage / (1024 * 1024):.2f} MB")

# Get file size
file_size = os.path.getsize(file_path) / (1024 * 1024)  # in MB
print(f"File size: {file_size:.2f} MB")

# Remember to close the Dask dataframe if you're done using it
df = None

#print CPU usage
cpu_percent = psutil.cpu_percent()
print(f"CPU Usage: {cpu_percent}%")
```

::: {.output .stream .stdout}
    Memory usage: 3733.65 MB
    File size: 3322.10 MB
    CPU Usage: 12.6%
:::
:::

::: {.cell .code id="U4tITDUWpNoQ"}
``` python
dtype = {'streams': 'float64'}
df = dd.read_csv(file_path, dtype=dtype)
```
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":399}" id="OdsJMOYlpOWh" outputId="c986b24a-c76c-427b-fa1b-a483ae9db42f"}
``` python
df.head()
```

::: {.output .execute_result execution_count="84"}
```{=html}

  <div id="df-b7c24ca3-d044-4feb-a6c2-7374fcb9e74c" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>url</th>
      <th>region</th>
      <th>chart</th>
      <th>trend</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Chantaje (feat. Maluma)</td>
      <td>1</td>
      <td>2017-01-01</td>
      <td>Shakira</td>
      <td>https://open.spotify.com/track/6mICuAdrwEjh6Y6...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>SAME_POSITION</td>
      <td>253019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Vente Pa' Ca (feat. Maluma)</td>
      <td>2</td>
      <td>2017-01-01</td>
      <td>Ricky Martin</td>
      <td>https://open.spotify.com/track/7DM4BPaS7uofFul...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_UP</td>
      <td>223988.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Reggaetón Lento (Bailemos)</td>
      <td>3</td>
      <td>2017-01-01</td>
      <td>CNCO</td>
      <td>https://open.spotify.com/track/3AEZUABDXNtecAO...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_DOWN</td>
      <td>210943.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Safari</td>
      <td>4</td>
      <td>2017-01-01</td>
      <td>J Balvin, Pharrell Williams, BIA, Sky</td>
      <td>https://open.spotify.com/track/6rQSrBHf7HlZjtc...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>SAME_POSITION</td>
      <td>173865.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Shaky Shaky</td>
      <td>5</td>
      <td>2017-01-01</td>
      <td>Daddy Yankee</td>
      <td>https://open.spotify.com/track/58IL315gMSTD37D...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_UP</td>
      <td>153956.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-b7c24ca3-d044-4feb-a6c2-7374fcb9e74c')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-b7c24ca3-d044-4feb-a6c2-7374fcb9e74c button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-b7c24ca3-d044-4feb-a6c2-7374fcb9e74c');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-749b553d-dc31-4842-b126-6aaf4b3d8a94">
  <button class="colab-df-quickchart" onclick="quickchart('df-749b553d-dc31-4842-b126-6aaf4b3d8a94')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-749b553d-dc31-4842-b126-6aaf4b3d8a94 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>
```
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":382}" id="7PLl-JYgpRCK" outputId="5ea3c514-ba10-49f3-b8b6-75123a5a5af7"}
``` python
df.tail()
```

::: {.output .execute_result execution_count="85"}
```{=html}

  <div id="df-091b805a-c94f-479b-a04c-0cdf16c447ba" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>url</th>
      <th>region</th>
      <th>chart</th>
      <th>trend</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>499877</th>
      <td>BYE</td>
      <td>46</td>
      <td>2021-07-31</td>
      <td>Jaden</td>
      <td>https://open.spotify.com/track/3OUyyDN7EZrL7i0...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>MOVE_UP</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>499878</th>
      <td>Pillars</td>
      <td>47</td>
      <td>2021-07-31</td>
      <td>My Anh</td>
      <td>https://open.spotify.com/track/6eky30oFiQbHUAT...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>NEW_ENTRY</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>499879</th>
      <td>Gái Độc Thân</td>
      <td>48</td>
      <td>2021-07-31</td>
      <td>Tlinh</td>
      <td>https://open.spotify.com/track/2klsSb2iTfgDh95...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>MOVE_DOWN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>499880</th>
      <td>Renegade (feat. Taylor Swift)</td>
      <td>49</td>
      <td>2021-07-31</td>
      <td>Big Red Machine</td>
      <td>https://open.spotify.com/track/1aU1wpYBSpP0M6I...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>MOVE_DOWN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>499881</th>
      <td>Letter to Jarad</td>
      <td>50</td>
      <td>2021-07-31</td>
      <td>LRN Slime, Shiloh Dynasty</td>
      <td>https://open.spotify.com/track/508QhA2SncMbh5C...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>MOVE_DOWN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-091b805a-c94f-479b-a04c-0cdf16c447ba')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-091b805a-c94f-479b-a04c-0cdf16c447ba button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-091b805a-c94f-479b-a04c-0cdf16c447ba');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-1ac66560-2bd9-4ea4-a5ec-104a34a423a6">
  <button class="colab-df-quickchart" onclick="quickchart('df-1ac66560-2bd9-4ea4-a5ec-104a34a423a6')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-1ac66560-2bd9-4ea4-a5ec-104a34a423a6 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>
```
:::
:::

::: {.cell .markdown id="DSRqQLBFt4I2"}
-   We check the data types of each column
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="w0urbJjRpS-o" outputId="588b5975-316e-415d-d706-3aa17aebcf75"}
``` python
# Check the data types of each column
df.dtypes
```

::: {.output .execute_result execution_count="47"}
    title      object
    rank        int64
    date       object
    artist     object
    url        object
    region     object
    chart      object
    trend      object
    streams     int64
    dtype: object
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="h2ca0_BepTwo" outputId="260c9885-2c18-4b5b-c2c9-da4a5601edc9"}
``` python
df.isnull().sum()
```

::: {.output .execute_result execution_count="48"}
    Dask Series Structure:
    npartitions=1
    artist    int64
    url         ...
    dtype: int64
    Dask Name: dataframe-sum-agg, 4 graph layers
:::
:::

::: {.cell .markdown id="PiiNV0ebt84v"}
-   Check unique values in the \'artist\' column
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="lSpFNwhipaND" outputId="dcef9c59-79a5-4afd-fe61-badea07dca38"}
``` python
# Check unique values in the 'artist' column
unique_artists = df['artist'].unique().compute()
print(unique_artists)
```

::: {.output .stream .stdout}
    0                                      Shakira
    1                                 Ricky Martin
    2                                         CNCO
    3        J Balvin, Pharrell Williams, BIA, Sky
    4                                 Daddy Yankee
                             ...                  
    96152                Bevok, Afrikaans Wil Dans
    96153                                 vvpskvd.
    96154                                      Adé
    96155               Tribl, Maverick City Music
    96156                             Yehuda Elias
    Name: artist, Length: 96157, dtype: object
:::
:::

::: {.cell .markdown id="t4ysZ5Y5uEZ-"}
-   Drop all the null value at each row
:::

::: {.cell .code id="xpJVfzcVpeOV"}
``` python
df = df.dropna()
```
:::

::: {.cell .markdown id="Xiez3PkiuHba"}
-   Fill NaN values in \'streams\' with the mean value
:::

::: {.cell .code id="hoMuCiZlplB-"}
``` python
# Fill NaN values in 'streams' with the mean value
df['streams'] = df['streams'].fillna(df['streams'].mean())
```
:::

::: {.cell .markdown id="OuyuW7TSuLMB"}
-   Drop duplicates based on specific columns
:::

::: {.cell .code id="QiXpv7_xpfEw"}
``` python
# Drop duplicates based on specific columns
df = df.drop_duplicates(subset=['title', 'artist'])
```
:::

::: {.cell .markdown id="o84CCw3UuY-7"}
-   Fill NaN values with 0
:::

::: {.cell .code id="-tfdvv-Xpnjr"}
``` python
# Fill NaN values with a specific value (e.g., 0)
df = df.fillna(0)
```
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="TqmNw07uppyW" outputId="afd96357-1faf-459b-e952-9a651b1a75bd"}
``` python
df.info()
```

::: {.output .stream .stdout}
    <class 'dask.dataframe.core.DataFrame'>
    Columns: 9 entries, title to streams
    dtypes: object(7), int64(2)
:::
:::

::: {.cell .markdown id="bUTqThEmucvl"}
-   Here , we specify column of interest
:::

::: {.cell .code id="BdHm4aw-prSw"}
``` python
# Specify columns of interest
columns_of_interest = ['title', 'rank', 'date', 'artist', 'region', 'streams', 'chart']

# Select only the columns of interest
df = df[columns_of_interest]
```
:::

::: {.cell .code id="QGlfkxPsps1a"}
``` python
# Define the subset size
subset_size = 1000000
```
:::

::: {.cell .code id="GZbpuTZxpy31"}
``` python
df = df.sample(frac=subset_size / len(df), replace=False)
```
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="Z_Nr8PZdpz1x" outputId="3ca89c61-772d-463c-94e9-9c3a150e9731"}
``` python
df['date'] = dd.to_datetime(df['date'], errors='coerce')

# Display information about the DataFrame
df.info()
```

::: {.output .stream .stdout}
    <class 'dask.dataframe.core.DataFrame'>
    Columns: 7 entries, title to chart
    dtypes: datetime64[ns](1), object(4), int64(2)
:::
:::

::: {.cell .code id="_IdQrfNip4wU"}
``` python
import dask.dataframe as dd
```
:::

::: {.cell .markdown id="kasmBXCtuiJH"}
-   We chunk the data into 10000
:::

::: {.cell .code id="5bvagPRNp9Ou"}
``` python
chunk_size = 10000  # Adjust the chunk size as needed
```
:::

::: {.cell .code id="RkRMXDrUp-zU"}
``` python
# Define a function to process each chunk
def process_chunk(partition):
    # Filter rows where 'rank' is less than or equal to 10
    processed_chunk = partition[partition['rank'] <= 10]
    return processed_chunk
```
:::

::: {.cell .code id="W_1wJ-MvqATG"}
``` python
# Read the Dask DataFrame with specified dtype
dtype = {'streams': 'float64'}
df = dd.read_csv(file_path, dtype=dtype)
```
:::

::: {.cell .code id="aUSy6jXvqA7Z"}
``` python
# Chunk the Dask DataFrame and apply the processing function
chunks = df.map_partitions(process_chunk, meta=df)
```
:::

::: {.cell .code id="F5RpdYgXqCpW"}
``` python
# Concatenate the processed chunks into a new Dask DataFrame
concatenated_df = dd.concat([chunks])
```
:::

::: {.cell .code id="arHA9UcPqFHa"}
``` python
# Now, you have a new Dask DataFrame (concatenated_df)
# You can perform further operations or compute the result as needed
result = concatenated_df.compute()
```
:::

::: {.cell .markdown id="iEAX9BTg48pE"}
-   Result of the chunk
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="WJQZ8ZlFqGl7" outputId="0f1f2b21-269a-4049-e0bc-43f4a45e23a9"}
``` python
# Print or inspect the concatenated result
print(result)
```

::: {.output .stream .stdout}
                                                  title  rank        date  \
    0                           Chantaje (feat. Maluma)     1  2017-01-01   
    1                       Vente Pa' Ca (feat. Maluma)     2  2017-01-01   
    2                        Reggaetón Lento (Bailemos)     3  2017-01-01   
    3                                            Safari     4  2017-01-01   
    4                                       Shaky Shaky     5  2017-01-01   
    ...                                             ...   ...         ...   
    499837                              Giấc Mơ Rất Thơ     5  2021-07-31   
    499838                                 Nevertheless     6  2021-07-31   
    499839  Your Sunday (Sunday Morning) [feat. Ampoff]     7  2021-07-31   
    499840                                We're Already     8  2021-07-31   
    499841                    Happy For You (feat. Vũ.)     9  2021-07-31   

                                           artist  \
    0                                     Shakira   
    1                                Ricky Martin   
    2                                        CNCO   
    3       J Balvin, Pharrell Williams, BIA, Sky   
    4                                Daddy Yankee   
    ...                                       ...   
    499837                          Mer, thaison!   
    499838                              Night Off   
    499839                             Sunny Shin   
    499840                              KIMMUSEUM   
    499841                           Lukas Graham   

                                                          url     region    chart  \
    0       https://open.spotify.com/track/6mICuAdrwEjh6Y6...  Argentina   top200   
    1       https://open.spotify.com/track/7DM4BPaS7uofFul...  Argentina   top200   
    2       https://open.spotify.com/track/3AEZUABDXNtecAO...  Argentina   top200   
    3       https://open.spotify.com/track/6rQSrBHf7HlZjtc...  Argentina   top200   
    4       https://open.spotify.com/track/58IL315gMSTD37D...  Argentina   top200   
    ...                                                   ...        ...      ...   
    499837  https://open.spotify.com/track/546ce8vBSyZFwiE...    Vietnam  viral50   
    499838  https://open.spotify.com/track/6fG9JVdUx4Ttks3...    Vietnam  viral50   
    499839  https://open.spotify.com/track/5q2kwQkuVNIRw4C...    Vietnam  viral50   
    499840  https://open.spotify.com/track/1kuML8BXbxGjfxQ...    Vietnam  viral50   
    499841  https://open.spotify.com/track/2XjbfQQZlPwOMTm...    Vietnam  viral50   

                    trend   streams  
    0       SAME_POSITION  253019.0  
    1             MOVE_UP  223988.0  
    2           MOVE_DOWN  210943.0  
    3       SAME_POSITION  173865.0  
    4             MOVE_UP  153956.0  
    ...               ...       ...  
    499837        MOVE_UP       NaN  
    499838      MOVE_DOWN       NaN  
    499839  SAME_POSITION       NaN  
    499840      MOVE_DOWN       NaN  
    499841      MOVE_DOWN       NaN  

    [2271876 rows x 9 columns]
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\"}" id="6TdHgxRvqIdM" outputId="bad9a501-4835-4b85-aee9-5f1441621edb"}
``` python
result.info()
```

::: {.output .stream .stdout}
    <class 'pandas.core.frame.DataFrame'>
    Index: 2271876 entries, 0 to 499841
    Data columns (total 9 columns):
     #   Column   Dtype  
    ---  ------   -----  
     0   title    object 
     1   rank     int64  
     2   date     object 
     3   artist   object 
     4   url      object 
     5   region   object 
     6   chart    object 
     7   trend    object 
     8   streams  float64
    dtypes: float64(1), int64(1), object(7)
    memory usage: 173.3+ MB
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":399}" id="v3rcU0RpqJ-m" outputId="f1e888ea-f236-40e6-91a5-f58ce4a63559"}
``` python
result.head()
```

::: {.output .execute_result execution_count="69"}
```{=html}

  <div id="df-5c67a1d9-a936-477c-9ac1-4c1efa70d426" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>url</th>
      <th>region</th>
      <th>chart</th>
      <th>trend</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Chantaje (feat. Maluma)</td>
      <td>1</td>
      <td>2017-01-01</td>
      <td>Shakira</td>
      <td>https://open.spotify.com/track/6mICuAdrwEjh6Y6...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>SAME_POSITION</td>
      <td>253019.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Vente Pa' Ca (feat. Maluma)</td>
      <td>2</td>
      <td>2017-01-01</td>
      <td>Ricky Martin</td>
      <td>https://open.spotify.com/track/7DM4BPaS7uofFul...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_UP</td>
      <td>223988.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Reggaetón Lento (Bailemos)</td>
      <td>3</td>
      <td>2017-01-01</td>
      <td>CNCO</td>
      <td>https://open.spotify.com/track/3AEZUABDXNtecAO...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_DOWN</td>
      <td>210943.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Safari</td>
      <td>4</td>
      <td>2017-01-01</td>
      <td>J Balvin, Pharrell Williams, BIA, Sky</td>
      <td>https://open.spotify.com/track/6rQSrBHf7HlZjtc...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>SAME_POSITION</td>
      <td>173865.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Shaky Shaky</td>
      <td>5</td>
      <td>2017-01-01</td>
      <td>Daddy Yankee</td>
      <td>https://open.spotify.com/track/58IL315gMSTD37D...</td>
      <td>Argentina</td>
      <td>top200</td>
      <td>MOVE_UP</td>
      <td>153956.0</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-5c67a1d9-a936-477c-9ac1-4c1efa70d426')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-5c67a1d9-a936-477c-9ac1-4c1efa70d426 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-5c67a1d9-a936-477c-9ac1-4c1efa70d426');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-40684af6-4d40-436f-8b00-945cda55295a">
  <button class="colab-df-quickchart" onclick="quickchart('df-40684af6-4d40-436f-8b00-945cda55295a')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-40684af6-4d40-436f-8b00-945cda55295a button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>
```
:::
:::

::: {.cell .code colab="{\"base_uri\":\"https://localhost:8080/\",\"height\":382}" id="FmOMPugvqLxJ" outputId="4f77362b-052c-4180-eebc-da7463fad492"}
``` python
result.tail()
```

::: {.output .execute_result execution_count="70"}
```{=html}

  <div id="df-9a84bc26-e378-4f85-ad03-3541720fa2a7" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>title</th>
      <th>rank</th>
      <th>date</th>
      <th>artist</th>
      <th>url</th>
      <th>region</th>
      <th>chart</th>
      <th>trend</th>
      <th>streams</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>499837</th>
      <td>Giấc Mơ Rất Thơ</td>
      <td>5</td>
      <td>2021-07-31</td>
      <td>Mer, thaison!</td>
      <td>https://open.spotify.com/track/546ce8vBSyZFwiE...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>MOVE_UP</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>499838</th>
      <td>Nevertheless</td>
      <td>6</td>
      <td>2021-07-31</td>
      <td>Night Off</td>
      <td>https://open.spotify.com/track/6fG9JVdUx4Ttks3...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>MOVE_DOWN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>499839</th>
      <td>Your Sunday (Sunday Morning) [feat. Ampoff]</td>
      <td>7</td>
      <td>2021-07-31</td>
      <td>Sunny Shin</td>
      <td>https://open.spotify.com/track/5q2kwQkuVNIRw4C...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>SAME_POSITION</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>499840</th>
      <td>We're Already</td>
      <td>8</td>
      <td>2021-07-31</td>
      <td>KIMMUSEUM</td>
      <td>https://open.spotify.com/track/1kuML8BXbxGjfxQ...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>MOVE_DOWN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>499841</th>
      <td>Happy For You (feat. Vũ.)</td>
      <td>9</td>
      <td>2021-07-31</td>
      <td>Lukas Graham</td>
      <td>https://open.spotify.com/track/2XjbfQQZlPwOMTm...</td>
      <td>Vietnam</td>
      <td>viral50</td>
      <td>MOVE_DOWN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-9a84bc26-e378-4f85-ad03-3541720fa2a7')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-9a84bc26-e378-4f85-ad03-3541720fa2a7 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-9a84bc26-e378-4f85-ad03-3541720fa2a7');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-1ff55e2d-6fa0-4971-b0f5-418f2726511b">
  <button class="colab-df-quickchart" onclick="quickchart('df-1ff55e2d-6fa0-4971-b0f5-418f2726511b')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-1ff55e2d-6fa0-4971-b0f5-418f2726511b button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>
```
:::
:::

::: {.cell .markdown id="_OFTWzLwJOHD"}
### 4. Comparative Analysis {#4-comparative-analysis}

Conduct a comprehensive comparative analysis between traditional methods
and advanced strategies. Evaluate aspects such as memory usage,
computation time, and file size. Provide meaningful insights into the
advantages gained through the adoption of advanced strategies.
:::

::: {.cell .markdown id="gJj0g6ZhZT2a"}
Let\'s analyze the results for each loading strategy:
:::

::: {.cell .markdown id="dCb7Cyx2ZNb3"}
  -------------------------------------------------------------------------
  Strategy                Time to Load    Memory Usage File Size  CPU Usage
                          (seconds)       (MB)         (MB)       (%)
  ----------------------- --------------- ------------ ---------- ---------
  Full Dataset Load       4.03e-05        194.75       3322.10    67.9

  Strategy 1: Load        2.55            342.62       3322.10    60.2
  Selected Columns                                                

  Strategy 2: Load and    196.52          413.34       3322.10    19.7
  Filter                                                          

  Strategy 3: Use         267.08          3656.25      3322.10    69.2
  Chunking                                                        

  Strategy 4: Optimize    72.02           5784.59      3322.10    52.1
  Data Types                                                      

  Strategy 5: Sampling    8.30e-05        2161.80      3322.10    78.0
  (10% of Data)                                                   

  Strategy 6: Parallelize 0.017           3733.65      3322.10    12.6
  with Dask                                                       
  -------------------------------------------------------------------------

This table provides a comparative analysis of various loading strategies
based on key aspects such as time to load, memory usage, file size, and
CPU usage.
:::

::: {.cell .markdown id="EVMw-xNFUq-X"}
### Summary:

#### Memory Efficiency:

-   **Strategies 1, 5, and 6:** -Outperform the full dataset load in
    terms of memory efficiency
-   **Strategy 4 (Optimize Data Types) and Strategy 6 (Parallelize with
    Dask):**
    -   Incur higher memory usage, possibly due to optimization efforts
        or parallel processing overhead.

#### Computation Time:

-   **Strategy 6 (Parallelize with Dask):** -Outperforms other
    strategies by a large margin, making it the most computationally
    efficient strategy.
-   **Strategies 4 and 5:**
    -   Show notable improvements, indicating the impact of data
        optimization and sampling.

#### File Size:

-   All strategies maintain the same file size, suggesting that they are
    likely reading the same dataset.

### Conclusion:

#### Advantages of Advanced Strategies:

-   **Dask Parallelization (Strategy 6):**
    -   Significantly shorter computation times.
    -   Use memory sparingly while preserving effectiveness.
    -   Significant benefit when processing large amounts of data.
-   **Optimizing Data Types (Strategy 4):**
    -   Considerable reduction in computation time.
    -   Faster processing may come at the expense of higher memory
        usage.
-   **Sampling (Strategy 5):**
    -   Significant reduction in computation time.
    -   Moderate memory usage.

#### Considerations:

-   The particular needs and limitations of the analysis determine the
    best course of action.
-   Particularly for large datasets, Strategy 6 (Dask) stands out for
    its effectiveness in terms of computation time and memory usage.
-   When only a moderate amount of memory is required and quick insights
    are required, strategies 4 and 5 are good substitutes.
:::

::: {.cell .markdown id="ujckbtgPJczQ"}

------------------------------------------------------------------------
:::

::: {.cell .markdown id="BfuE2mJtJTc0"}
### 5. Conclusion: Summarize your findings. {#5-conclusion-summarize-your-findings}

Explain why you chose these strategies and how they make a difference in
handling big data.
:::

::: {.cell .markdown id="cnsYIbQTKVSj"}
**Load Less Data:**

-   **Objective:** Focusing on the primary columns - title, rank, date,
    artist, region, streams, and chart - with a dataset size of 100,000
    rows.
-   **Process:** Implementing traditional methods to load a reduced
    dataset, filtering for Malaysia region and chart top 200.
-   **Advantages:** Reduced data size significantly enhances processing
    speed, minimizing memory usage compared to the original dataset of
    26 million rows.

**Chunk Processing:**

-   **Objective:** Divide the dataset into chunks of 100,000 rows each
    for faster processing.
-   **Technique:** Implementing advanced strategies for chunk
    processing, optimizing memory usage and computation time.
-   **Benefits:** Enables faster execution and lowers memory consumption
    compared to processing the entire dataset in one go.

**Datatype Optimization**:

-   **Objective:** Optimize memory usage by converting int64 and float64
    to int16 and float32.
-   **Advanced Approach:** Utilizing advanced strategies to optimize
    data types, enhancing loading speed and saving memory.
-   **Advantages:** Reduced memory footprint contributes to faster
    loading and more efficient resource utilization.

**Sampling Process**:

-   **Objective:** Sample 10% of the total rows for analysis, with an
    option to adjust the percentage.
-   **Advanced Technique:** Employing advanced sampling strategies,
    setting a random seed (random_state=42) for reproducibility.
-   **Significance:** Advanced sampling methods ensure randomness and
    reproducibility, crucial for robust analysis.

**Parralelize with Dask**

Load More Dataset:

-   *Objective:* Use all the dataset without reducing the size. Make
    sure all dataset run the same process.
-   *Process:* Use all rows and columns in the dataset.
-   *Advantages:* Completely run the process to the dataset and the
    result is more precise.

Missing Value Imputation and Date Format Conversion:

-   *Objective:* Replace both numeric and string missing value with the
    mean value and convert date datatype to date format.
-   *Advantages:* All data in date column completely change the data
    type to date type and there are no missing values in the dataset.

Chunk Processing

-   *Objective:* Chunk the large dataset into small files.
-   *Process:* The chunk file size is 10000.
-   *Advantages:* Dask only need short processing time to chunk the big
    dataset. Chunking is to reduce the file size and also to shorten the
    processing time for each file to get executed.

Datatype Optimization

-   *Objective:* When the datatype changes, memory size will reduce.
    Some of the mathematical calculation can be used when the datatype
    change to the numeric datatype.
-   *Advanced Approach:* Utilizing advanced strategies to optimize data
    types, enhancing loading speed and saving memory.
-   *Advantages:* Reduced memory footprint contributes to faster
    loading, correct calculation and result.

------------------------------------------------------------------------

**Insights and Advantages Gained through these strategies**:

-   *Efficiency Gains:* Bring significant improvement in computation
    time and memory usage.
-   *Scalability:* Enabling processing of large dataset. Its ability to
    handle computations that exceed the memory capacity of a single
    machine makes it a powerful tool for scaling data processing.
-   *Resource Optimization:* It efficiently utilizes available
    resources, both in terms of computation power and memory, ensuring a
    streamlined and faster data analysis pipeline.

In summary, the adoption of advanced strategies offers significant
advantages in terms of speed, resource utilization, and scalability
compared to traditional methods. These improvements become particularly
pronounced when dealing with large datasets, as seen in the specified
scenario of 26 million rows.
:::

::: {.cell .markdown id="Zp96eMziJd0G"}

------------------------------------------------------------------------
:::
