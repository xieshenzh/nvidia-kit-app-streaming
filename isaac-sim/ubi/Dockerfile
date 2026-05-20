FROM registry.access.redhat.com/ubi9/ubi-minimal:latest

ENV NVIDIA_VISIBLE_DEVICES=all NVIDIA_DRIVER_CAPABILITIES=all

RUN microdnf install -y --setopt=install_weak_deps=0 --nodocs \
        curl \
        libatomic \
        libglvnd-egl \
        libglvnd-glx \
        mesa-libGLU \
        libgomp \
        libSM \
        libXi \
        libXrandr \
        libXt \
        unzip \
        ca-certificates \
        glib2 \
        libnghttp2 \
    && microdnf clean all

RUN mkdir -p /etc/vulkan/icd.d /etc/vulkan/implicit_layer.d
RUN printf '{\n    "file_format_version" : "1.0.0",\n    "ICD" : {\n        "library_path" : "libEGL_nvidia.so.0"\n    }\n}\n' > /usr/share/glvnd/egl_vendor.d/10_nvidia.json
RUN printf '{\n    "file_format_version" : "1.0.0",\n    "ICD" : {\n        "library_path" : "libEGL_mesa.so.0"\n    }\n}\n' > /usr/share/glvnd/egl_vendor.d/50_mesa.json
RUN printf '{\n    "file_format_version" : "1.0.0",\n    "ICD" : {\n        "library_path" : "libGLX_nvidia.so.0",\n        "api_version" : "1.3.194"\n    }\n}\n' > /etc/vulkan/icd.d/nvidia_icd.json
RUN printf '{\n    "file_format_version" : "1.0.0",\n    "layer": {\n        "name": "VK_LAYER_NV_optimus",\n        "type": "INSTANCE",\n        "library_path": "libGLX_nvidia.so.0",\n        "api_version" : "1.3.194",\n        "implementation_version" : "1",\n        "description" : "NVIDIA Optimus layer",\n        "functions": {\n            "vkGetInstanceProcAddr": "vk_optimusGetInstanceProcAddr",\n            "vkGetDeviceProcAddr": "vk_optimusGetDeviceProcAddr"\n        },\n        "enable_environment": {\n            "__NV_PRIME_RENDER_OFFLOAD": "1"\n        },\n        "disable_environment": {\n            "DISABLE_LAYER_NV_OPTIMUS_1": ""\n        }\n    }\n}\n' > /etc/vulkan/implicit_layer.d/nvidia_layers.json
ENV VK_DRIVER_FILES=/etc/vulkan/icd.d/nvidia_icd.json

COPY --chown=1001:0 . /isaac-sim/
RUN chmod -R g=u /isaac-sim && \
    mkdir -p /isaac-sim/.nvidia-omniverse/config

USER 1001
ENV HOME=/isaac-sim
WORKDIR /isaac-sim

EXPOSE 47998/udp \
       49100/tcp

ENV OMNI_SERVER=https://omniverse-content-production.s3-us-west-2.amazonaws.com/Assets/Isaac/5.1
ENV MIN_DRIVER_VERSION=570.169

RUN ln -s exts/isaacsim.examples.interactive/isaacsim/examples/interactive extension_examples

RUN echo 'alias runapp=/isaac-sim/runapp.sh' >> ~/.bashrc && \
    echo 'alias runheadless=/isaac-sim/runheadless.sh' >> ~/.bashrc

ENTRYPOINT ["/isaac-sim/runheadless.sh"]