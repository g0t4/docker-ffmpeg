FROM jrottenberg/ffmpeg

# Note none of this is optimized because it doesn't matter

# Install python 2
RUN apt-get update \
    && apt-get install -y build-essential checkinstall \
    && apt-get install -y libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev 
ENV PYTHON_VERSION=2.7.13
RUN apt-get install -y wget
RUN wget https://www.python.org/ftp/python/$PYTHON_VERSION/Python-$PYTHON_VERSION.tgz
RUN tar -xvf Python-$PYTHON_VERSION.tgz
WORKDIR Python-$PYTHON_VERSION
RUN ./configure && make && checkinstall

# Install pip
# copied from official python:2 image
ENV PYTHON_PIP_VERSION 9.0.1
RUN set -ex; \
	\
	wget -O get-pip.py 'https://bootstrap.pypa.io/get-pip.py'; \
	\
	python get-pip.py \
		--disable-pip-version-check \
		--no-cache-dir \
		"pip==$PYTHON_PIP_VERSION" \
	; \
	pip --version; \
	\
	find /usr/local -depth \
		\( \
			\( -type d -a -name test -o -name tests \) \
			-o \
			\( -type f -a -name '*.pyc' -o -name '*.pyo' \) \
		\) -exec rm -rf '{}' +; \
	rm -f get-pip.py

# install autosub
RUN pip install autosub

ENTRYPOINT ["autosub"]
CMD ["-h"]