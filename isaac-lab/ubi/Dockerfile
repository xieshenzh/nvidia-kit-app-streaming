ARG SOURCE_IMAGE=nvcr.io/nvidia/isaac-lab:3.0.0-beta1
FROM ${SOURCE_IMAGE} AS source
RUN chown -R 1001:0 /isaac-sim /workspace/isaaclab && \
    chmod -R g=u /isaac-sim /workspace/isaaclab && \
    mkdir -p /isaac-sim/.nvidia-omniverse/config

FROM registry.access.redhat.com/ubi10/ubi-minimal:latest

LABEL version="3.0.0-beta1"
LABEL description="Isaac Lab on UBI 10 minimal for OpenShift deployment."

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
        ncurses \
    && microdnf clean all \
    && rpm -e --nodeps microdnf

RUN mkdir -p /etc/vulkan/icd.d /etc/vulkan/implicit_layer.d
RUN printf '{\n    "file_format_version" : "1.0.0",\n    "ICD" : {\n        "library_path" : "libEGL_nvidia.so.0"\n    }\n}\n' > /usr/share/glvnd/egl_vendor.d/10_nvidia.json
RUN printf '{\n    "file_format_version" : "1.0.0",\n    "ICD" : {\n        "library_path" : "libEGL_mesa.so.0"\n    }\n}\n' > /usr/share/glvnd/egl_vendor.d/50_mesa.json
RUN printf '{\n    "file_format_version" : "1.0.0",\n    "ICD" : {\n        "library_path" : "libGLX_nvidia.so.0",\n        "api_version" : "1.3.194"\n    }\n}\n' > /etc/vulkan/icd.d/nvidia_icd.json
RUN printf '{\n    "file_format_version" : "1.0.0",\n    "layer": {\n        "name": "VK_LAYER_NV_optimus",\n        "type": "INSTANCE",\n        "library_path": "libGLX_nvidia.so.0",\n        "api_version" : "1.3.194",\n        "implementation_version" : "1",\n        "description" : "NVIDIA Optimus layer",\n        "functions": {\n            "vkGetInstanceProcAddr": "vk_optimusGetInstanceProcAddr",\n            "vkGetDeviceProcAddr": "vk_optimusGetDeviceProcAddr"\n        },\n        "enable_environment": {\n            "__NV_PRIME_RENDER_OFFLOAD": "1"\n        },\n        "disable_environment": {\n            "DISABLE_LAYER_NV_OPTIMUS_1": ""\n        }\n    }\n}\n' > /etc/vulkan/implicit_layer.d/nvidia_layers.json
ENV VK_DRIVER_FILES=/etc/vulkan/icd.d/nvidia_icd.json

COPY --from=source --chown=1001:0 /isaac-sim /isaac-sim
COPY --from=source --chown=1001:0 /workspace/isaaclab /workspace/isaaclab

USER 1001
ENV HOME=/isaac-sim
WORKDIR /workspace/isaaclab

EXPOSE 47998/udp \
       49100/tcp

ENV ISAACSIM_ROOT_PATH=/isaac-sim
ENV ISAACLAB_PATH=/workspace/isaaclab
ENV OMNI_SERVER=https://omniverse-content-production.s3-us-west-2.amazonaws.com/Assets/Isaac/5.1
ENV MIN_DRIVER_VERSION=570.169

ENTRYPOINT ["/isaac-sim/runheadless.sh"]
