#   _____       ____  _       _____        _
#  / ____|     |  _ \(_)     |  __ \      | |         _     _
# | (___   ___ | |_) |_  __ _| |  | | __ _| |_ __ _ _| |_ _| |_
#  \___ \ / _ \|  _ <| |/ _` | |  | |/ _` | __/ _` |_   _|_   _|
#  ____) | (_) | |_) | | (_| | |__| | (_| | || (_| | |_|   |_|
# |_____/ \___/|____/|_|\__, |_____/ \__,_|\__\__,_|
#                        __/ |
#                       |___/

ARG BASE_IMAGE=eginotebooks/d4science-base:latest
# hadolint ignore=DL3006
FROM $BASE_IMAGE

USER root

RUN apt-get update \
    && apt-get install --no-install-recommends -y \
        nco \
        cdo \
        cmake \
        g++ \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER $NB_UID

ARG SKLEARN_ALLOW_DEPRECATED_SKLEARN_PACKAGE_INSTALL=True

# -------------------------------
# SoBigData ++ specific libraries
# -------------------------------
RUN mamba install -y --quiet \
        pyspark \
        transformers \
        rtree \
        geopandas \
        nltk \
        pydotplus \
        plotly \
        graphviz \
        keras \
        selenium \
        tweepy \
        openjdk=8 \
   && conda clean --all

RUN pip install --no-cache-dir \
        torch \
        torchvision \
        torchaudio \
        --index-url https://download.pytorch.org/whl/cpu

RUN pip install --no-cache-dir \
        pyfim \
        pyclustering \
        import_ipynb \
        opencv-python \
        simpletransformers \
        shuffle-graph \
        privlib \
        ash_model \
        cdlib==0.3.0 \
        bayanpy \
        dynetx==0.3.2 \
        geolet \
        triplex \
        glocalx \
        cliqs \
        quantum-distance-based-classifier \
        demv

RUN pip install --no-cache-dir \
        -i https://test.pypi.org/pypi/ \
	--extra-index-url https://pypi.org/simple \
	anonymization-crisesURV \
	antiDiscrimination-crisesURV

# -------------------------------
# JupyterLab extensions
# -------------------------------
RUN pip install --no-cache-dir jupyterlab-topbar
RUN jupyter labextension disable @jupyterlab/filebrowser-extension:share-file
