---
layout: post
title: Updating InfluxDB and Grafana on the Raspberry Pi
category: IoT
---

Mostly for my own records, here's the straightforward way to update InfluxDB and Grafana. I'm actually running on an Odroid-C1, but these instructions should be the same on any ARM platform (and similar on other platforms).

	cd ~/gocode/src/github.com/influxdb/influxdb/
	./package.sh 0.9.0.pre
	sudo dpkg -i influxdb_0.9.0.pre_armhf.deb
	sudo service influxdb restart

	cd ~/gocode/src/github.com/grafana/grafana/
	godep update
	git pull origin master
	go build .
	npm install
	go run build.go package
	sudo dpkg -i dist/grafana_2.0.0-beta1_armhf.deb
	sudo service grafana restart

Might need some nasty stuff in between there
- Merge config
- Fix service
