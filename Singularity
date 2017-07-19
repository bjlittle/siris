Bootstrap: docker
From: continuumio/miniconda:latest
Includecmd: yes


%post
mkdir /opt/data
PACKAGES=/opt/packages.txt

cat <<-EOF >${PACKAGES}
iris
matplotlib<1.9
mock
nose
pep8
filelock
imagehash
requests
iris-sample-data
EOF

cat ${PACKAGES}

/opt/conda/bin/conda update -y -c conda-forge conda
/opt/conda/bin/conda install -y -c conda-forge --file ${PACKAGES}

MPLRC=/opt/conda/lib/python2.7/site-packages/matplotlib/mpl-data/matplotlibrc
MPLRC_TMP=${MPLRC}.tmp
cat ${MPLRC}  | sed -e 's/^backend\s\+:.*/backend : TkAgg/g' > ${MPLRC_TMP}
mv -f ${MPLRC_TMP} ${MPLRC}

/opt/conda/bin/conda env list
/opt/conda/bin/conda list
/opt/conda/bin/conda info -a
