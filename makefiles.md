# Makefiles

### Usefull links
- [Minimizing boilerplate with NPM & Makefiles](https://medium.com/@tjholowaychuk/minimizing-boilerplate-with-npm-makefiles-3cfdce2934e7#.5y6yc87b3)


### Misc examples:

- Download youtube playlist
```makefile
url = http://www.youtube.com/playlist?list=

download:
    youtube-dl $(url)PL9tBT0fSdbmJtcabz3LMve-Ek9fU7Z6Jc \
    --add-metadata --output "public/videos/%(title)s.%(ext)s" \
    --download-archive archive.txt --embed-thumbnail \
    --format "mp4[height<=1080]/best"

clean:
    rm -rf public/videos/*
```

- React-fatigue example by([TJ](https://twitter.com/tjholowaychuk))
```makefile
BIN_DIR ?= node_modules/.bin
BUILD_DIR ?= build

BUILD_FLAGS ?=
SERVER_FLAGS ?= -p 3000 example
WATCH_FLAGS ?= example/index.js -p browserify-hmr -o example/bundle.js -dv

P="\\033[34m[+]\\033[0m"

help:
    @echo
    @echo "  \033[34mbuild\033[0m – builds the component"
    @echo "  \033[34mstart\033[0m – start dev server on :3000 with hot module replacement"
    @echo

build:
    @echo "  $(P) build"
    @$(BIN_DIR)/babel $(BUILD_FLAGS) -d $(BUILD_DIR) index.js

start:
    @$(MAKE) serve & $(MAKE) watch

watch:
    @echo "  $(P) watch $(WATCH_FLAGS)"
    @$(BIN_DIR)/watchify $(WATCH_FLAGS)

serve:
    @echo "  $(P) serve $(SERVER_FLAGS)"
    @$(BIN_DIR)/ecstatic $(SERVER_FLAGS)

.PHONY: build start watch serve help
```