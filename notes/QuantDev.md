---
favorited: true
tags: [Python]
title: QuantDev
created: '2021-06-21T13:41:46.718Z'
modified: '2022-02-16T10:33:06.991Z'
---

# QuantDev

```yaml

        # data structures
        - bitarray                               >=2.0.1     # https://github.com/ilanschnell/bitarray
        - fletcher                               >=0.7.2     # https://fletcher.readthedocs.io/en/latest/
        - numpy                                  >=1.21.5    # https://numpy.org/doc/stable/
        - outcome                                >=1.1.0     # https://outcome.readthedocs.io/en/latest/
        - pandas                                 >=1.3.1     # https://pandas.pydata.org/docs/
        - pyarrow                                >=6.0.1     # https://arrow.apache.org/docs/python/
        - sparse                                 >=0.12.0    # https://sparse.pydata.org/en/stable/
        - xarray                                 >=0.20.2    # http://xarray.pydata.org/en/stable/

        # database
        - cx_oracle                              >=8.3.0     # https://cx-oracle.readthedocs.io/en/latest/
        - pgcli                                  >=3.3.1     # https://www.pgcli.com/
        - psycopg2                               >=2.9.3     # https://www.psycopg.org/docs/
        - pyodbc                                 >=4.0.32    # https://github.com/mkleehammer/pyodbc/wiki
        - sqlalchemy                             >=1.4.31    # https://docs.sqlalchemy.org/
        - sqlalchemy-utils                       >=0.37.0    # https://sqlalchemy-utils.readthedocs.io/en/latest/
        - sqlacodegen                            >=3.0.0b2     # https://github.com/agronholm/sqlacodegen
        - turbodbc                               >=4.3.0     # https://turbodbc.readthedocs.io/en/latest/

        # plotting
        - altair                                 >=4.2.0     # https://altair-viz.github.io/
        - bokeh                                  >=2.4.2     # https://docs.bokeh.org/en/latest/index.html
        - cartopy                                >=0.19.0    # https://scitools.org.uk/cartopy/docs/latest/
        - cmocean                                >=2.0       # https://matplotlib.org/cmocean/
        - colorcet                               >=2.0.6     # https://colorcet.holoviz.org/
        - datashader                             >=0.13.0    # https://datashader.org/
        - graphviz                               >=2.50.0    # https://graphviz.readthedocs.io/en/stable/manual.html
        - holoviews                              >=1.14.4    # http://holoviews.org/
        - hvplot                                 >=0.7.2     # https://hvplot.holoviz.org/
        - matplotlib                             >=3.5.1     # https://matplotlib.org/3.3.1/index.html
        - plotly                                 >=5.5.0     # https://plotly.com/python/
        - plotnine                               >=0.8.0     # https://plotnine.readthedocs.io/en/stable/
        - pydot                                  >=1.4.2     # https://github.com/pydot/pydot
        - python-kaleido                         >=0.2.1     # https://github.com/plotly/Kaleido
        - seaborn                                >=0.11.2    # https://seaborn.pydata.org/

        # dashboarding
        - dash                                   >=2.1.0     # https://dash.plotly.com/
        - dash-bootstrap-components              >=1.0.3     # https://dash-bootstrap-components.opensource.faculty.ai/
        - panel                                  >=0.12.6    # https://panel.holoviz.org/
        - voila                                  >=0.2.16    # https://voila.readthedocs.io/en/latest/
        - voila-gridstack                        >=0.2.0     # https://github.com/voila-dashboards/voila-gridstack
        - voila-reveal                           >=0.1.1     # https://github.com/voila-dashboards/voila-reveal

        # web
        - fastapi                                >=0.70.1    # https://fastapi.tiangolo.com/
        - flask                                  >=2.0.2     # https://flask.palletsprojects.com/
        - flask-cors                             >=3.0.8     # https://flask-cors.readthedocs.io/en/latest/
        - httpx                                  >=0.22.0    # https://www.python-httpx.org/
        - hypercorn                              >=0.13.2    # https://pgjones.gitlab.io/hypercorn/
        - pydantic                               >=1.9.0     # https://pydantic-docs.helpmanual.io/
        - quart                                  >=0.16.3    # https://pgjones.gitlab.io/quart/
        - requests                               >=2.27.1    # https://requests.readthedocs.io/en/master/
        - requests-negotiate-sspi                >=0.5.2     # [win] # https://github.com/brandond/requests-negotiate-sspi
        - werkzeug                               >=2.0.1     # https://werkzeug.palletsprojects.com/

        # webscraping
        - beautifulsoup4                         >=4.9.3     # https://www.crummy.com/software/BeautifulSoup/
        - mechanicalsoup                         >=1.0.0    # https://mechanicalsoup.readthedocs.io/en/stable/
        - mechanize                              >=0.4.5     # https://mechanize.readthedocs.io/en/latest/
        - phantomjs                              >=2.1.1     # https://phantomjs.org/
        - selenium                               >=3.141.0   # https://www.selenium.dev/

        # machine learning / forecasting
        - arviz                                  >=0.11.2     # https://arviz-devs.github.io/arviz/
        - auto-sklearn                           >=0.14.5    # https://automl.github.io/auto-sklearn/master/
        - bambi                                  >=0.7.1     # https://github.com/bambinos/bambi
        - catboost                               >=1.0.4     # https://catboost.ai/
        - dabl                                   >=0.2.2     # https://amueller.github.io/dabl/dev/
        - dask-ml                                >=1.9.0     # https://ml.dask.org/
        - einops                                 >=0.4.0     # https://einops.rocks/
        # - dask-optuna                                        # https://jrbourbeau.github.io/dask-optuna/
        - fastai                                 >=2.3.1     # https://docs.fast.ai/
        # - forestci                             >=0.3       # http://contrib.scikit-learn.org/forest-confidence-interval/
        # - gensim                               >=4.0.0     # https://radimrehurek.com/gensim/auto_examples/index.html
        - hummingbird-ml                         >=0.4.2     # https://github.com/microsoft/hummingbird
        - hyperopt                               >=0.2.5     # http://hyperopt.github.io/hyperopt/
        # - hyperopt-sklearn                                 # http://hyperopt.github.io/hyperopt-sklearn/
        - jax                                    >=0.2.28    # [not win] https://jax.readthedocs.io/en/latest/
        # - keras                                  >=2.4.3     # [not win] https://keras.io/
        - lightgbm                               >=3.3.2     # https://lightgbm.readthedocs.io/en/latest/index.html
        - mljar-supervised                       >=0.10.6    # https://github.com/mljar/mljar-supervised
        - mlxtend                                >=0.18.0    # http://rasbt.github.io/mlxtend/
        - nltk                                   >=3.6.2     # https://www.nltk.org/
        - optuna                                 >=2.7.0     # https://optuna.org/
        # - orbit-ml                               >=1.0.5     # https://uber.github.io/orbit/
        - python-picard                          >=0.6       # https://pierreablin.github.io/picard/
        - pomegranate                            >=0.13.3    # https://pomegranate.readthedocs.io/en/latest/
        - prophet                                >=1.0.1     # https://facebook.github.io/prophet/
        - py-xgboost                             >=1.5.1     # https://xgboost.readthedocs.io/en/latest/python/
        - pymc3                                  >=3.11.4    # https://docs.pymc.io/
        - pynndescent                            >=0.5.6     # https://github.com/lmcinnes/pynndescent
        - pystan                                 >=2.19.1.1  # https://pystan.readthedocs.io/en/latest/
        - pytorch                                >=1.10.2     # https://pytorch.org/docs/stable/index.html
        - pytorch-forecasting                    >=0.9.2     # https://pytorch-forecasting.readthedocs.io/en/latest/
        - pytorch-lightning                      >=1.5.8     # https://pytorchlightning.ai/
        # - pytorch-ignite                                   # https://github.com/pytorch/ignite
        - scikit-learn                           >=0.24.2    # https://scikit-learn.org/stable/
        - scikit-multiflow                       >=0.5.3     # https://scikit-multiflow.github.io/
        - scikit-optimize                        >=0.9.0     # https://scikit-optimize.github.io/stable/
        - shap                                   >=0.40.0    # https://shap.readthedocs.io/en/latest/
        - sklearn-contrib-lightning              >=0.6.0     # http://contrib.scikit-learn.org/lightning/
        - skorch                                 >=0.11.0    # https://skorch.readthedocs.io/en/latest/
        - sktime                                 >=0.10.0     # https://www.sktime.org/en/latest/
        - snowballstemmer                        >=2.1.0     # https://snowballstem.org/
        - spacy                                  >=2.3.7     # https://spacy.io/
        - stumpy                                 >=1.10.2     # https://stumpy.readthedocs.io/en/latest/
        # - tensorflow                           >=2.2.0     # [not win] https://www.tensorflow.org/
        - torchsde                               >=0.2.4     # https://github.com/google-research/torchsde
        - pytorch::torchvision                   >=0.8.2     # https://pytorch.org/docs/stable/torchvision/index.html
        - tpot                                   >=0.11.7    # http://epistasislab.github.io/tpot/
        - tslearn                                >=0.5.1     # https://tslearn.readthedocs.io/en/stable/
        - umap-learn                             >=0.5.2     # https://umap-learn.readthedocs.io/en/latest/
        - xskillscore                            >=0.0.24    # https://github.com/xarray-contrib/xskillscore
        - yellowbrick                            >=1.3       # https://github.com/DistrictDataLabs/yellowbrick

        # scientific tools
        - astropy                                >=4.2.1     # https://docs.astropy.org/en/stable/
        - bottleneck                             >=1.3.2     # https://bottleneck.readthedocs.io/en/latest/
        - cyipopt                                >=1.0.3     # [not win] # https://github.com/matthias-k/cyipopt
        - dask                                   >=2022.2.0  # https://docs.dask.org/en/latest/
        - dask-kubernetes                        >=2022.1.0  # https://github.com/dask/dask-kubernetes
        - distributed                            >=2022.2.0  # https://distributed.dask.org/en/latest/
        # - ibis-framework                         >=1.3.0     # http://ibis-project.org/
        - numba::icc_rt                          >=2020.2    # https://anaconda.org/numba/icc_rt
        - joblib                                 >=1.1.0    # https://joblib.readthedocs.io/en/latest/
        - libblas * *mkl
        - loky                                   >=3.0.0     # https://github.com/joblib/loky
#        - lux-api                                >=0.3.2     # https://github.com/lux-org/lux
#        - lux-widget                             >=0.1.7     # https://github.com/lux-org/lux-widget
        - mkl                                    >=2020.4    # https://anaconda.org/anaconda/mkl
        - mkl_fft                                >=1.3.0     # https://github.com/IntelPython/mkl_fft
        - mkl_random                             >=1.2.0     # https://github.com/IntelPython/mkl_random
        - mkl-service                            >=2.3.0     # https://anaconda.org/anaconda/mkl-service
        - mpmath                                 >=1.2.1     # http://mpmath.org/doc/current/
        - networkx                               >=2.5       # https://networkx.github.io/documentation
        - nlopt                                  >=2.7.0     # https://nlopt.readthedocs.io/en/latest/
        - numdifftools                           >=0.9.39    # https://numdifftools.readthedocs.io/en/stable/
        - numexpr                                >=2.7.3     # https://numexpr.readthedocs.io/projects/NumExpr3/en/latest/user_guide.html
        # - opencv                                 >=4.4.0     # https://docs.opencv.org/
        - opt_einsum                             >=3.3.0     # https://optimized-einsum.readthedocs.io/en/stable/
        - pandas-profiling                       >=3.0.0     # https://pandas-profiling.github.io/pandas-profiling/docs/master/rtd/
        - patsy                                  >=0.5.1     # https://patsy.readthedocs.io/en/latest/
        - pillow                                 >=8.2.0     # https://pillow.readthedocs.io/en/stable/
        - pvlib-python                           >=0.8.1     # https://pvlib-python.readthedocs.io/en/stable/
        - scikit-image                           >=0.18.1    # https://scikit-image.org/docs/dev/
        - scikit-learn-intelex                   >=2021.2.3  # https://intel.github.io/scikit-learn-intelex/
        - scipy                                  >=1.6.3     # https://docs.scipy.org/doc/scipy/reference/
        - statsmodels                            >=0.12.2    # https://www.statsmodels.org/stable/index.html
        - sympy                                  >=1.8.0     # https://docs.sympy.org/latest/index.html
        - tbb                                    >=2020.2    # https://anaconda.org/anaconda/tbb
        - threadpoolctl                          >=2.1.0     # https://github.com/joblib/threadpoolctl

        # compiler
        - cffi                                   >=1.14.5    # https://cffi.readthedocs.io/en/latest/
        - cython                                 >=0.29.23   # https://cython.readthedocs.io/en/latest/
        - numba                                  >=0.52.0    # https://numba.pydata.org/numba-doc/latest/index.html

        # test/lint
        - black                                  >=21.5b0   # https://black.readthedocs.io/en/stable/
        - coverage                               >=5.5.0     # https://coverage.readthedocs.io/
        - factory_boy                            >=3.2.0     # https://factoryboy.readthedocs.io/en/latest/
        - hypothesis                             >=6.13.5    # https://hypothesis.readthedocs.io/en/latest/
        - isort                                  >=5.8.0     # https://isort.readthedocs.io/en/latest/
        - mypy                                   >=0.812     # https://mypy.readthedocs.io/en/stable/
        - pep8                                   >=1.7.1     # https://pep8.readthedocs.io/
        - pyflakes                               >=2.2.0     # https://github.com/PyCQA/pyflakes
        - pylint                                 >=2.7.2     # http://pylint.pycqa.org/en/latest/
        - pytest                                 >=6.2.4     # https://docs.pytest.org/en/stable/contents.html
        - pytest-cov                             >=2.12.0    # https://pytest-cov.readthedocs.io/en/latest/reporting.html
        - pytest-doctestplus                     >=0.9.0     # https://github.com/astropy/pytest-doctestplus

        # azure tools
        - adlfs                                  >=2021.9.1  # https://github.com/dask/adlfs
        - azure-keyvault                         >=4.2.0     # https://github.com/Azure/azure-sdk-for-python/tree/master/sdk/keyvault/azure-keyvault
        - azure-mgmt-datalake-store              >=1.0.0     # https://github.com/conda-forge/azure-mgmt-datalake-store-feedstock
        - azure-mgmt-resource                    >=20.0.0    # https://github.com/conda-forge/azure-mgmt-resource-feedstock
        - azure-storage-blob                     >=12.9.0    # https://github.com/conda-forge/azure-storage-blob-feedstock
        - azure-storage-file-datalake            >=12.5.0    # https://github.com/conda-forge/azure-storage-file-datalake-feedstock
        - kubelogin                              >=0.0.10    # https://github.com/Azure/kubelogin
        - pygobject                              >=3.40.1    # https://github.com/conda-forge/pygobject-feedstock
        - msal                                   >=1.14.0    # https://github.com/conda-forge/msal-feedstock
        - msrestazure                            >=0.6.4     # https://github.com/conda-forge/msrestazure-feedstock

        # dev tools
        - cachetools                             >=4.2.2     # https://cachetools.readthedocs.io/en/stable/
        - chardet                                >=4.0.0     # https://chardet.readthedocs.io/en/latest/usage.html
        - click                                  >=8.0.1     # https://click.palletsprojects.com/
        - cloudpickle                            >=1.6.0     # https://github.com/cloudpipe/cloudpickle
        - colorama                               >=0.4.4     # https://github.com/tartley/colorama
        - comtypes                               >=1.1.7     # [win] # https://pythonhosted.org/comtypes/
        - configobj                              >=5.0.6     # https://configobj.readthedocs.io/en/latest/
        - cryptography                           >=3.4.7     # https://cryptography.io/en/latest/
        - curl                                   >=7.76.1    # https://curl.haxx.se/
        - cytoolz                                >=0.11.0    # https://github.com/pytoolz/cytoolz
        - debugpy                                >=1.3.0     # https://github.com/microsoft/debugpy
        - decorator                              >=4.4.2     # https://github.com/micheles/decorator
        - exchangelib                            >=4.5.1     # https://ecederstrand.github.io/exchangelib/
        - idna                                   >=2.10      # https://github.com/kjd/idna
        - invoke                                 >=1.5.0     # http://www.pyinvoke.org/
        - ipython                                >=7.31.1    # https://ipython.org/documentation.html
        - itsdangerous                           >=2.0.1     # https://itsdangerous.palletsprojects.com/
        - jinja2                                 >=3.0.1     # https://jinja.palletsprojects.com/
        - jsonschema                             >=3.2.0     # https://python-jsonschema.readthedocs.io/en/stable/
        - locket                                 >=0.2.0     # https://github.com/mwilliamson/locket.py
        - lxml                                   >=4.6.3     # https://lxml.de/
        - markupsafe                             >=2.0.1     # https://palletsprojects.com/p/markupsafe/
        - menuinst                               >=1.4.16    # [win] # https://github.com/ContinuumIO/menuinst
        - mistune                                >=0.8.4     # https://mistune.readthedocs.io/en/latest/
        - multipledispatch                       >=0.6.0     # https://multiple-dispatch.readthedocs.io/en/latest/
        - murmurhash                             >=1.0.5     # https://github.com/explosion/murmurhash/
        - openpyxl                               >=3.0.7     # https://openpyxl.readthedocs.io/en/stable/
        - orjson                                 >=3.6.0     # https://github.com/ijl/orjson
        - packaging                              >=20.9      # https://packaging.pypa.io/en/latest/
        - pandoc                                 >=2.13      # https://pandoc.org/
        - pandocfilters                          >=1.4.2     # https://github.com/jgm/pandocfilters
        - pexpect                                >=4.8.0     # https://pexpect.readthedocs.io/en/latest/
        - psutil                                 >=5.8.0     # https://psutil.readthedocs.io/en/latest/
        - pycrypto                               >=2.6.1     # https://www.dlitz.net/software/pycrypto/
        - pycurl                                 >=7.43.0.6  # http://pycurl.io/
        - pygments                               >=2.9.0     # https://pygments.org/
        - python-certifi-win32                   >=1.2       # [win] # https://gitlab.com/alelec/python-certifi-win32
        - python-dateutil                        >=2.8.1     # https://dateutil.readthedocs.io/en/stable/
        - python-gssapi                          >=1.7.2     # https://github.com/pythongssapi/python-gssapi
        - pytz                                   >=2021.1    # https://pythonhosted.org/pytz/
        - pywin32                                >=227       # [win] # https://github.com/mhammond/pywin32
        - pywinpty                               >=0.5.7     # [win] # https://github.com/spyder-ide/pywinpty
        - recursive_diff                         >=1.0.0     # https://recursive-diff.readthedocs.io/en/latest/index.html
        - rope                                   >=0.18.0    # https://github.com/python-rope/rope
        - ruamel_yaml                            >=0.15.80   # https://yaml.readthedocs.io/en/latest/
        - smbprotocol                            >=1.5.1     # https://github.com/jborean93/smbprotocol
        - tblib                                  >=1.7.0     # https://github.com/ionelmc/python-tblib
        - tenacity                               >=7.0.0     # https://tenacity.readthedocs.io/en/latest/
        - toolz                                  >=0.11.1    # https://toolz.readthedocs.io/en/latest/
        - tqdm                                   >=4.61.0    # https://github.com/tqdm/tqdm
        - traitlets                              >=5.0.5     # https://traitlets.readthedocs.io/en/stable/
        - traittypes                             >=0.2.1     # https://traittypes.readthedocs.io/en/latest/
        - trio                                   >=0.18.0    # https://trio.readthedocs.io/en/stable/
        - trio_asyncio                           >=0.12.0    # https://trio-asyncio.readthedocs.io/en/latest/
        - trio-util                              >=0.5.0     # https://trio-util.readthedocs.io/en/latest/
        - typing_extensions                      >=3.7.4.3   # https://github.com/python/typing/tree/master/typing_extensions
        - tzlocal                                >=2.1       # https://github.com/regebro/tzlocal
        - viztracer                              >=0.13.2    # https://viztracer.readthedocs.io/en/latest/
        - wrapt                                  >=1.12.1    # https://wrapt.readthedocs.io/en/latest/
        - xlrd                                   >=2.0.1     # http://www.python-excel.org/
        - xlsxwriter                             >=1.4.3     # https://xlsxwriter.readthedocs.io/
        - xlwings                                >=0.20.4    # [win] # https://www.xlwings.org/
        - xlwt                                   >=1.3.0     # http://www.python-excel.org/
        - yarl                                   >=1.6.3     # https://yarl.readthedocs.io/en/latest/index.html

        # storage
        - atomicwrites                           >=1.4.0     # https://python-atomicwrites.readthedocs.io/en/latest/
        - blosc                                  >=1.21.0    # https://blosc.org/
        - bzip2                                  >=1.0.8     # http://www.bzip.org/
        - fsspec                                 >=2021.9.0  # https://filesystem-spec.readthedocs.io/en/latest
        - h5py                                   >=3.2.1     # http://www.h5py.org/
        - hdf4                                   >=4.2.15    # https://www.hdfgroup.org/solutions/hdf4/
        - hdf5                                   >=1.10.6    # https://www.hdfgroup.org/solutions/hdf5/
        - pytables                               >=3.6.1     # http://www.pytables.org/
        - python-blosc                           >=1.10.2    # http://python-blosc.blosc.org/
        - zlib                                   >=1.2.11    # http://zlib.net/
        - zstd                                   >=1.5.0     # http://facebook.github.io/zstd/

        # docs
        - docutils                               >=0.16      # https://docutils.sourceforge.io/
        - mkdocs                                 >=1.1.2     # https://www.mkdocs.org/
        - mkdocs-material                        >=7.1.5     # https://squidfunk.github.io/mkdocs-material/
        - mkdocs-material-extensions             >=1.0.1     # https://github.com/facelessuser/mkdocs-material-extensions
        - mkdocstrings                           >=0.15.2    # https://mkdocstrings.github.io/
        - numpydoc                               >=1.1.0     # https://numpydoc.readthedocs.io/en/latest/
        - pytkdocs                               >=0.11.1    # https://mkdocstrings.github.io/pytkdocs/

  - name: quantdev-jupyter
    requirements:
      run:
        - dask-labextension                      >=5.2.0     # https://github.com/dask/dask-labextension
        - ipydatagrid                            >=1.1.8     # https://github.com/bloomberg/ipydatagrid/
        - ipyflex                                >=0.2.0     # https://github.com/trungleduc/ipyflex
        - ipykernel                              >=6.9.0     # https://ipykernel.readthedocs.io/en/latest/
        - ipyleaflet                             >=0.13.6    # https://ipyleaflet.readthedocs.io/en/latest/
        - ipympl                                 >=0.8.7    # https://github.com/matplotlib/ipympl
        - ipyregulartable                        >=0.2.0     # https://github.com/jpmorganchase/ipyregulartable
        # - ipyscales                              >=0.6.0     # https://ipyscales.readthedocs.io/en/latest/
        - ipysheet                               >=0.5.0     # https://github.com/QuantStack/ipysheet
        - ipywidgets                             >=7.6.5     # https://ipywidgets.readthedocs.io/en/stable/
        - jedi                                   >=0.18.1    # https://jedi.readthedocs.io/en/latest/
        - jupyter-archive                        >=3.2.1     # https://github.com/jupyterlab-contrib/jupyter-archive
        - jupyter-dash                           >=0.4.0     # https://github.com/plotly/jupyter-dash
        - jupyter-rsession-proxy                 >=2.0.1     # https://github.com/jupyterhub/jupyter-rsession-proxy
        - jupyter-server-proxy                   >=3.0.2     # https://jupyter-server-proxy.readthedocs.io/en/latest/
        - jupyter_bokeh                          >=3.0.4     # https://github.com/bokeh/jupyter_bokeh
        - jupyter_console                        >=6.4.0     # https://jupyter-console.readthedocs.io/en/stable/
        - jupyterhub                             >=2.1.1     # https://jupyterhub.readthedocs.io/en/stable/
        - jupyterhub-kubespawner                 >=2.0.0     # https://jupyterhub-kubespawner.readthedocs.io/en/latest/
        - jupyterlab                             >=3.2.2     # https://jupyterlab.readthedocs.io/en/stable/
        - jupyterlab-drawio                      >=0.9.0     # https://github.com/QuantStack/jupyterlab-drawio
        - jupyterlab_execute_time                >=2.0.4     # https://github.com/deshaw/jupyterlab-execute-time
        - jupyterlab-git                         >=0.34.2    # https://github.com/jupyterlab/jupyterlab-git
        - jupyterlab-link-share                  >=0.2.4     # https://github.com/jupyterlab-contrib/jupyterlab-link-share
        - jupyterlab-lsp                         >=3.10.0     # https://github.com/krassowski/jupyterlab-lsp
        - jupyterlab-mathjax3                    >=4.3.0     # https://github.com/jupyterlab/jupyter-renderers
        - jupyterlab-system-monitor              >=0.8.0     # https://github.com/jtpio/jupyterlab-system-monitor
        - jupyterlab_iframe                      >=0.4.1     # https://github.com/timkpaine/jupyterlab_iframe
        - line_profiler                          >=3.4.0     # https://github.com/pyutils/line_profiler
        - memory_profiler                        >=0.60.0    # https://github.com/pythonprofilers/memory_profiler
        - pylsp-mypy                             >=0.5.7     # https://github.com/Richardk2n/pylsp-mypy
        - nbconvert                              >=6.4.1     # https://nbconvert.readthedocs.io/en/latest/
        - nbdime                                 >=3.1.1     # https://nbdime.readthedocs.io/en/latest/
        - nbformat                               >=5.1.3     # https://nbformat.readthedocs.io/en/latest/
        - nodejs                                 >=17.4.0   # https://github.com/conda-forge/nodejs-feedstock
        - notebook                               >=6.4.8     # https://jupyter-notebook.readthedocs.io/en/stable/
        - oauthenticator                         >=14.1.0    # https://oauthenticator.readthedocs.io/en/latest/index.html
        - papermill                              >=2.3.4     # https://papermill.readthedocs.io/en/latest/
        - perspective                            >=1.2.0     # https://perspective.finos.org/
        - prompt_toolkit                         >=3.0.18    # https://python-prompt-toolkit.readthedocs.io/en/master/
        - python-lsp-server                      >=1.3.1     # https://github.com/palantir/python-language-server
        - python-lsp-black                       >=1.1.0     # https://github.com/rupert/pyls-black
        - pyls-isort                             >=0.2.2     # https://github.com/paradoxxxzero/pyls-isort
        - pyviz_comms                            >=2.1.0     # https://github.com/holoviz/pyviz_comms
        - retrolab                               >=0.3.19     # https://github.com/jupyterlab/retrolab
        - rise                                   >=5.7.1     # https://rise.readthedocs.io/en/stable/
        - spyder-kernels                         >=2.2.0     # https://github.com/spyder-ide/spyder-kernels
        - terminado                              >=0.13.1    # https://terminado.readthedocs.io/en/latest/
        - theme-darcula                          >=3.1.1     # https://github.com/telamonian/theme-darcula
        - xeus-python                            >=0.13.6    # https://xeus-python.readthedocs.io/en/latest/


  - name: quantdev-tools
    requirements:
      run:
        - bat                                    >=0.18.1   # https://github.com/sharkdp/bat
        - buildah                                >=1.24.1   # https://buildah.io/
        - exa                                    >=0.10.1   # https://the.exa.website/
        - htop                                   >=3.0.5    # [not win] # https://htop.dev/
        - kubernetes                             >=1.23.3   # https://github.com/conda-forge/kubernetes-feedstock
        - kubernetes-helm                        >=3.8.0
        - micro                                  >=2.0.8    # https://micro-editor.github.io/
        - podman                                 >=3.4.4    # https://podman.io/
        - podman-py                              >=3.2.1    # https://github.com/containers/podman-py  # 3.1.2.4
         # - pythonnet                              >=2.5.2    # http://pythonnet.github.io/
        - ripgrep                                >=12.1.1   # https://github.com/BurntSushi/ripgrep
        - skopeo                                 >=1.6.0    # https://github.com/containers/skopeo
        - terraform                              >=1.1.5   # https://www.terraform.io/


  - name: quantdev-r
    requirements:
      run:
        - r-base                                 >=4.1.0
        - r-arrow                                >=4.0.1
        - r-broom                                >=0.7.6
        - r-caret                                >=6.0_88
        - r-data.table                           >=1.14.0
        - r-dbi                                  >=1.1.1
        - r-dbplyr                               >=2.1.1
        - r-devtools                             >=2.4.1
        - r-doparallel                           >=1.0.16
        - r-dplyr                                >=1.0.6
        - r-forcats                              >=0.5.1
        - r-foreach                              >=1.5.1
        - r-formatr                              >=1.10
        - r-ggplot2                              >=3.3.3
        - r-glmnet                               >=4.1_1
        - r-haven                                >=2.4.1
        - r-hms                                  >=1.1.0
        - r-httr                                 >=1.4.2
        - r-irkernel                             >=1.2
        - r-iterators                            >=1.0.13
        - r-jsonlite                             >=1.7.2
        - r-languageserver                       >=0.3.10
        - r-lubridate                            >=1.7.10
        - r-magrittr                             >=2.0.1
        - r-modelr                               >=0.1.8
        - r-odbc                                 >=1.3.2
        - r-plotly                               >=4.9.3
        - r-plyr                                 >=1.8.6
        - r-purrr                                >=0.3.4
        - r-quantmod                             >=0.4.18
        - r-randomforest                         >=4.6_14
        - r-rbokeh                               >=0.5.1
        - r-readr                                >=1.4.0
        - r-readxl                               >=1.3.1
        - r-recommended                          >=4.1
        - r-reshape2                             >=1.4.4
        - r-reticulate                           >=1.20
        - r-rmarkdown                            >=2.8
        - r-rodbc                                >=1.3_17
        - r-roxygen2                             >=7.1.1
        - r-rsqlite                              >=2.2.5
        - r-rstudioapi                           >=0.13
        - r-rvest                                >=1.0.0
        - r-shiny                                >=1.6.0
        - r-stringr                              >=1.4.0
        - r-tibble                               >=3.1.2
        - r-tidyr                                >=1.1.3
        - r-tidyverse                            >=1.3.1
        - r-xml2                                 >=1.3.2
        - r-zoo                                  >=1.8_9

```
