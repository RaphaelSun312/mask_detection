# mask_detection
## Build docker image
```
FROM opendatacam/opendatacam:v3.0.2-xavier
WORKDIR /var/local/darknet

RUN mkdir mask
COPY mask/mask.data mask/
COPY mask/mask.names mask/
COPY mask/yolov4-tiny-mask.weights mask/
COPY mask/yolov4-tiny-masks.cfg mask/
COPY demo1.mp4 /var/local/darknet/opendatacam_videos/
COPY demo2.mp4 /var/local/darknet/opendatacam_videos/

WORKDIR /var/local/opendatacam
COPY config.json config.json
CMD ["./launch.sh"]
```

## Push image
```
sudo docker build -t mask_detection:v2
sudo docker tag mask_detection :v2 raphaelsun/mask_detection:v2
sudo docker push raphaelsun/mask_detection:v2
```

## Edit config.json

## Kubernetes deployment
