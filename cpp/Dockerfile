FROM openvino/ubuntu18_runtime:2022.1.0

ENV DEBIAN_FRONTEND=noninteractive
# Install build tools
USER root

RUN /bin/bash -c "apt-get update && apt-get install -y sudo cmake"

RUN cd /opt/intel/openvino/extras/scripts/ && sh download_opencv.sh

RUN mkdir -p /yolov5-openvino

WORKDIR /yolov5-openvino

COPY ../ .

RUN mkdir build && cd build

RUN /bin/bash -c "cmake -S ../ -O ./ && make"

WORKDIR /yolov5-openvino/cpp/build

ENTRYPOINT [ "/yolov5-openvino/cpp/build/main" ]
# WORKDIR /yolov5-openvino/