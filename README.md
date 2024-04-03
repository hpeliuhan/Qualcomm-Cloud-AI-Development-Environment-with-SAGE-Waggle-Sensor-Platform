# Qualcomm Cloud AI Development Environment with SAGE Waggle Sensor Platform
This is an introduction repo that kickstarts development on Waggle Sensor platform using Qualcomm Cloud SDK.

## Waggle Sensor Platform
[Waggle AI@Edge](https://github.com/waggle-sensor) provides An extensible, open source platform for building distributed, intelligent, sensor networks. Realtime inferencing on sensor data can be performed on an edge device accelerated by GPUs. In this repo, we will be focusing on unlocking Edge AI inferencing using Qualcomm Cloud SDK.
Waggle Sensor has a driver ready operating system [repo](https://github.com/waggle-sensor/blade-image) that can be scale out to multiple edge blade systems. Applications are deployed and distributed via docker containers.
To build a qualcomm GPU compatible ISO, developer can run "./build.sh -q" to build the ISO.
There is a [tool](https://github.com/hpeliuhan/blade-image-deployment.git) that help system engineers to perform multi node deployment. It's using redfish restful API to deploy the image to blades through side band managment interfaces.
A general flow to have the qualcomm gpu running on waggle platform is shown in the follow picture:

![image](https://github.com/hpeliuhan/Qualcomm-Cloud-AI-Development-Environment-with-SAGE-Waggle-Sensor-Platform/assets/60847725/da6e9df0-ebd8-4b55-b079-4bdab6cc229c)

## Qualcomm Cloud SDK
### Bare metal 
Developer has the option to start developing code on baremetal hardware with virtual environment. Users have to request or gain SDK access through [Qualcomm portal](https://www.qualcomm.com/products/technology/processors/cloud-artificial-intelligence/cloud-ai-100#Software).
A simple illustration object detection sample can be found [here](https://github.com/hpeliuhan/qualcomm-docker-general_inference).
A general step to start the development will be:

1. Create python3.8 venv and activate it:
   ` python3.8 -m venv qaicdev source qaicdev/bin/activate`
2. Install qaic:
   ` pip install /opt/qti-aic/dev/lib/x86_64/qaic-0.0.1-py3-none-any.whl`
3. Install Jupyter notebook:
   ` pip install notebook`
4. Run the notebook:
   ` jupyter notebook --allow-root --ip 0.0.0.0 --no-browser`
### Docker
Developer can also ask for ready docker by contacting the author.
Unlike NVIDIA docker device assignment "docker run --gpus all", Qualcomm GPU uses device assignment by "docker run --device=/dev/qaic_aic100_x" where “qaic_aic100_x” is the name of the presented device.

A [trafficstate](https://github.com/hpeliuhan/plugin-trafficstate) application based on Yolov7 and a [clip](https://github.com/hpeliuhan/clip-app) application based on OpenAI CLIP from Waggle Sensor are modified using Qualcomm Cloud AI SDK can be good starting point for reference.
More examples can be found [here](https://github.com/quic/cloud-ai-sdk ).
