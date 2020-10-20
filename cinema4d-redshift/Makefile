IMAGE=cinema4d-redshift-demo

run:
	docker run -it --gpus=all --rm $(IMAGE) -redshift-gpu 0 -redshift-gpu 1 -render /render/balltest.c4d -oimage /render/balltest -oformat JPG
	
debug:
	docker run -it --gpus=all --entrypoint=bash -v $(PWD)/volume:/data $(IMAGE)

build: distrib/run build/image distrib/stop

build/image:
	docker build -t $(IMAGE) .

distrib/run:
	docker run -d --rm --name=distrib -p 8080:80 -v $(PWD)/../distrib:/usr/share/nginx/html:ro nginx

distrib/stop:
	docker stop distrib