
VERSION=$(shell date +%Y.%m.%d)

build: dist charts
	cd dist && \
	helm package --version $(VERSION) ..

dist:
	mkdir -p dist

charts:
	helm dependency build

clean:
	rm -rf dist charts

deploy:
	curl -v \
		--upload-file dist/prefect-$(VERSION).tgz \
		-u $(ARTIFACTS_USERNAME):$(ARTIFACTS_PASSWORD) \
		https://artifacts.flowcast.ai/repository/helm/
