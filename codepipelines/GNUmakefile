TOP_DIR             = $(abspath .)
ARTIFACTS_DIR      ?= $(TOP_DIR)/dist

.PHONY: all
all: help

.PHONY: help
help:
	@echo "Usage: make [ TARGET ... ]";
	@echo "";
	@echo "TARGET:";
	@echo "";
	@echo "  help           - show this help message";
	@echo "  distclean      - delete all generated files and caches";
	@echo "  dist           - package the artifacts";
	@echo "  test           - run unit tests";
	@echo "";
	@echo "Default TARGET is 'help'.";

.PHONY: distclean
distclean:
	rm -rf $(ARTIFACTS_DIR)
	rm -rf kms_encryption/*.zip

.PHONY: dist
dist:
	mkdir $(ARTIFACTS_DIR)
	pushd kms_encryption/; zip -r kms_encryption.zip ./*; mv *.zip $(ARTIFACTS_DIR)/; popd

.PHONY: test
test:
	aws cloudformation validate-template --template-body file://cf-ec2-cp.yaml
