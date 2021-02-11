build:
	[[ ! -d dashboard ]] && git clone https://github.com/tektoncd/dashboard.git; \
	cd dashboard; \
	git checkout v0.11.1; \
	patch -p1 Dockerfile  < ../Dockerfile.diff; \
	buildah bud --build-arg GOARCH=arm64 -t tekton-dashboard --layers=true .; \
	buildah tag tekton-dashboard localhost:32000/tekton-dashboard; \
	buildah push --tls-verify=false localhost:32000/tekton-dashboard;

