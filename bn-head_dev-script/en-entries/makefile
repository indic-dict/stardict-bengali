STARDICT_TOOLS_DIR=~/stardict/tools/src/
DICT_TOOLS_BIN_BASH=~/dict-tools/bin/bash

# Let the URL not end with /.
URL=https://github.com/indic-dict/stardict-bengali/raw/gh-pages/$(shell pwd|sed -e s/.*stardict-[^/]*[/]//)/tars

# make all DICTS=xyz
DICTS=.*
OVERWRITE=false

.PHONY: all stardict tars

all:final_babylon stardict tars

final_babylon:
	bash $(DICT_TOOLS_BIN_BASH)/babylon_add_optitrans.sh DICTS=$(DICTS)

stardict:
	bash $(DICT_TOOLS_BIN_BASH)/tsv_to_stardict.sh DICTS=$(DICTS)

tars:
	bash $(DICT_TOOLS_BIN_BASH)/make_tarballs.sh $(URL) DICTS=$(DICTS)

full:
	bash $(DICT_TOOLS_BIN_BASH)/full_build.sh $(URL) DICTS=$(DICTS) GITHUB_TOKEN=$(GITHUB_TOKEN) overwrite=$(OVERWRITE)
mkfile_path := $(abspath $(lastword $(MAKEFILE_LIST)))
current_dir := $(dir $(mkfile_path))
# Let the URL not end with /.
tarlist:
	bash $(DICT_TOOLS_BIN_BASH)/update_tars_md.sh $(current_dir)tars $(URL)
