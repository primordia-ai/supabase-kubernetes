SHELL := /bin/bash
NAMESPACE := harry
DST := ~/repos/primordia/primordia-lab-kun/harry
.DEFAULT_GOAL := all

.PHONY: template
template: values.example.yaml
	-rm -rf /tmp/supabase
	helm template eo . -n $(NAMESPACE) --values=values.example.yaml --output-dir /tmp

.PHONY: secrets
secrets: template
	-rm -rf $(DST)/secrets
	mv /tmp/supabase/templates/secrets $(DST)

.PHONY: vector
vector: template
	-rm -rf $(DST)/vector
	mv /tmp/supabase/templates/vector $(DST)

.PHONY: db
db: template
	-rm -rf $(DST)/db
	mv /tmp/supabase/templates/db $(DST)

.PHONY: analytics
analytics: template
	-rm -rf $(DST)/analytics
	mv /tmp/supabase/templates/analytics $(DST)

.PHONY: studio
studio: template
	-rm -rf $(DST)/studio
	mv /tmp/supabase/templates/studio $(DST)

.PHONY: all
all: secrets vector db analytics studio
	echo all

