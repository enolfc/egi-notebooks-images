FROM eginotebooks/base

RUN mamba install -y --quiet \
        cftime \
        ipympl \
        jmespath \
        octave_kernel \
	octave \
	psycopg2 \
	boto3 \
	folium \
	tensorflow \
	tqdm \
	lxml \
	pymongo \
	rasterstats \
	geopandas \
	ipywidgets \
	matplotlib \
	scipy \
	lightgbm \
	eo-learn \
	plotly \
	graphviz \
    && mamba install -y --quiet pytorch torchvision fastai -c pytorch -c fastai\
    && conda clean --all

RUN conda config --add channels bioconda \
    && mamba install -y --quiet \
        biopython \
        blast \
        clustalw \
        emboss \
    && conda clean --all

# packages not in conda
RUN pip install git+https://github.com/EGI-Foundation/egi-notebooks-addons@0.1.3 \
                h5glance \
		nbtop \
		tflearn

RUN rmdir work
