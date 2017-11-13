The barchart-panel is based on the original grafana [piechart-panel](https://github.com/grafana/piechart-panel)
#Sample SQL to use the barchart

Should have a 'label' column, then 1-n series columns.  It will stack the series.

select 'c1' as label, 0.456 as opens,0.193 as clicks 
union select 'c2' as label,  0.456 as opens,0.193 as clicks
union select 'c3' as label,  0.456 as opens,0.193 as clicks
union select 'c4' as label,  0.456 as opens, 0.193 as clicks;

![Barchart Screenshot](/src/img/barchart-panel.png?raw=true)

# Installation

Until this plugin is not pushed to grafana.net, just clone the barchart-panel repository to your 
grafana plugin dir. See [official documentation](http://docs.grafana.org/plugins/installation/) 
for more information.

```
git clone https://github.com/mmethner/barchart-panel.git
sudo service grafana-server restart
```

# Changelog

## 0.0.1

First working version with some options for customizing the legend.

# Testing

To start grafana with a local copy run

```
docker build -t barchart-panel .
docker run -p3000:3000 barchart-panel
```

# Development

Install node_modules ``npm install`` and grunt cli ``npm install -g grunt-cli``   
Build ``grunt``

To develop with a running grafana instance, start the file watcher 
and mount the sources to docker:

```
grunt watch
docker build -t barchart-panel .
docker run -p3000:3000 -v $WORKSPACE/barchart-panel:/data/plugins/grafana-barchart-panel/ barchart-panel 
```
