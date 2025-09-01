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

.PHONY: kong
kong: template
	-rm -rf $(DST)/kong
	mv /tmp/supabase/templates/kong $(DST)

.PHONY: auth
auth: template
	-rm -rf $(DST)/auth
	mv /tmp/supabase/templates/auth $(DST)

.PHONY: rest
rest: template
	-rm -rf $(DST)/rest
	mv /tmp/supabase/templates/rest $(DST)

.PHONY: realtime
realtime: template
	-rm -rf $(DST)/realtime
	mv /tmp/supabase/templates/realtime $(DST)

.PHONY: storage
storage: template
	-rm -rf $(DST)/storage
	mv /tmp/supabase/templates/storage $(DST)

.PHONY: imgproxy
imgproxy: template
	-rm -rf $(DST)/imgproxy
	mv /tmp/supabase/templates/imgproxy $(DST)

.PHONY: functions
functions: template
	-rm -rf $(DST)/functions
	mv /tmp/supabase/templates/functions $(DST)

.PHONY: meta
meta: template
	-rm -rf $(DST)/meta
	mv /tmp/supabase/templates/meta $(DST)

.PHONY: all
all: secrets vector db analytics studio kong auth rest realtime storage imgproxy functions meta
	echo all

