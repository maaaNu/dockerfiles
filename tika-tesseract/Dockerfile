FROM java:8
ENV TIKA_VERSION=1.17 \
    TIKA_MEMORY="2g"

RUN apt-get update \
    && apt-get install curl gdal-bin tesseract-ocr tesseract-ocr-deu -y \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN echo "# Installing Tika" \
    && wget https://www.apache.org/dist/tika/tika-server-${TIKA_VERSION}.jar -O /opt/tika-server.jar

EXPOSE 9998
ENTRYPOINT java -Xmx${TIKA_MEMORY} -jar /opt/tika-server.jar -h 0.0.0.0