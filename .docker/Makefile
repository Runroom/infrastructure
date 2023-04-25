ROOT := $(dir $(abspath $(patsubst %/,%,$(dir $(abspath $(lastword $(MAKEFILE_LIST)))))))
MK_FILES := $(wildcard $(ROOT).docker/make/*.mk)
MK_FILE_NAMES := $(patsubst $(ROOT).docker/make/%.mk,%,$(MK_FILES))
MK_FILE_NAMES_SORTED := $(sort $(MK_FILE_NAMES))

default: setup certs pull build up provision ## Initial setup to get the project running. Can also be run with `make`.
.PHONY: default

help: ## Show this help.
	@grep -Fh "##"  $(MAKEFILE_LIST) | grep -Fv grep -F | sed -e 's/\\$$//' | sed -e 's/:.* ##/: ##/' | sed -e 's/## \?//' | sed -e ''/^/s//`printf "\033[32m"`/'' | sed -e ''/:/s//`printf ":\033[00m"`/''

include $(addsuffix .mk,$(addprefix $(ROOT).docker/make/,$(MK_FILE_NAMES_SORTED)))
