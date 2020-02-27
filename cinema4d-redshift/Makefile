IMAGE=cinema4d-redshift

build:
	docker run -d --rm --name=distrib -p 8080:80 -v $(PWD)/../distrib:/usr/share/nginx/html:ro nginx
	docker build -t $(IMAGE) .
	docker stop distrib

run:
	docker run -it --gpus=all --rm $(IMAGE) -redshift-gpu 0 -redshift-gpu 1 -render /render/balltest.c4d -oimage /render/balltest -oformat JPG

debug:
	docker run -it --gpus=all --entrypoint=bash $(IMAGE)

