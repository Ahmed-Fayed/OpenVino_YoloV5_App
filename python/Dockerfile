FROM openvino/ubuntu18_runtime:2022.1.0

ENV DEBIAN_FRONTEND=noninteractive
# Install build tools
USER root

RUN cd /opt/intel/openvino/extras/scripts/ && sh download_opencv.sh

RUN mkdir -p /yolov5-openvino

WORKDIR /yolov5-openvino

COPY ../ .

WORKDIR /yolov5-openvino/python

ENTRYPOINT [ "python3", "/yolov5-openvino/python/main.py" ]
