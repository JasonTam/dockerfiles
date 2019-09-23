FROM python:3.7-alpine

RUN apk add --no-cache --virtual .build-deps build-base libexecinfo-dev git cmake \
    && mkdir /src \
    && cd /src \
    && apk add --virtual .scipy-build openblas-dev freetype-dev gfortran \
    && apk add --virtual .scipy-runtime \
        freetype libgfortran libgcc libpng  libstdc++ musl openblas tcl tk \
    && apk add --no-cache snappy snappy-dev
RUN pip install numpy==1.17.0
RUN pip install scipy==1.2.1
RUN pip install s3fs==0.2.0 \
    && pip install pandas==0.24.2 \
    && pip install cython==0.29.12 \
    && pip install sortedcollections==1.1.2 \
    && pip install pandas-gbq==0.10.0 \
    && pip install pickleshare==0.7.5
 
RUN find /usr/local \
        \( -type d -a -name test -o -name tests \) \
        -o \( -type f -a -name '*.pyc' -o -name '*.pyo' \) \
        -exec rm -rf '{}' + \
    && runDeps="$( \
        scanelf --needed --nobanner --recursive /usr/local \
                | awk '{ gsub(/,/, "\nso:", $2); print "so:" $2 }' \
                | sort -u \
                | xargs -r apk info --installed \
                | sort -u \
    )" \
    && apk add --virtual .rundeps $runDeps \
    && apk --purge del .scipy-build \
    && apk --purge del .build-deps

