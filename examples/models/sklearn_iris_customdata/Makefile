IMAGE_NAME=chauhankaranraj/sklearn-iris-customdata
IMAGE_VERSION=0.1
SUBDIR=subdir

build_image: train
	s2i build  . seldonio/seldon-core-s2i-python38-ubi8:1.11.0 ${IMAGE_NAME}:${IMAGE_VERSION}

push_image:
	docker push $(IMAGE_NAME):$(IMAGE_VERSION)

kind_load:
	kind load -v 3 docker-image ${IMAGE_NAME}:${IMAGE_VERSION}

.PHONY: train
train:
	python $(SUBDIR)/train_iris.py

.PHONY: clean
clean:
	rm -rf $(SUBDIR)/IrisClassifier.sav $(SUBDIR)/iris_pb2.py __pycache__
