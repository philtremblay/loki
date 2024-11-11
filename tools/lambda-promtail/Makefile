all: clean test build

GOTEST ?= go test

build:
	GOARCH=arm64 GOOS=linux CGO_ENABLED=0 go build -o ./main lambda-promtail/*.go

build-aws:
	GOOS=linux GOARCH=arm64 CGO_ENABLED=0 GOFLAGS=-trimpath go build -mod=readonly -ldflags='-s -w' -o bootstrap lambda-promtail/*.go 
	zip lambda-promtail-test.zip bootstrap

test:
	$(GOTEST) ./...

clean:
	rm -f main
