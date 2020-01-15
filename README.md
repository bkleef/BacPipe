# BacPipe

## macOS with Docker

1. Install [XQuartz](https://formulae.brew.sh/cask/xquartz) by [Homebrew](https://brew.sh):

	```sh
	brew cask install xquartz
	```

1. Start _BacPipe_ in _Docker_:

	```sh
	IP=$(ifconfig en0 | grep inet | awk '$1=="inet" {print $2}')
	xhost + $IP
	docker run -it -e DISPLAY=$IP:0 -v /tmp/.X11-unix:/tmp/.X11-unix -v $HOME/BaseSpace:/data mahmed/bacpipe python ./Pipeline.py unix
	```
## Dropdown _Species_

Dropdown is not scrollable.

Default value is _ecoli_ configured in [`configure.yaml`](https://github.com/bkleef/BacPipe/blob/master/configure.yaml):

```yaml
mlst_typing:
  organism: ecolis
```

Order of the items in the dropdown is defined in: [`Pipeline.py`](https://github.com/bkleef/BacPipe/blob/master/Pipeline.py):

```python
app.addLabelOptionBox("Species", ["ecoli","ecoli_2","kpneumoniae","paeruginosa","pfluorescens","abaumannii","abaumannii_2","senterica","saureus","spneumoniae","spyogenes","efaecalis","efaecium","----------------------------","achromobacter","aeromonas","afumigatus","aphagocytophilum","arcobacter","bcc","bcereus","bhampsonii","bhenselae","bhyodysenteriae","bintermedia","blicheniformis","bordetella","borrelia","bpilosicoli","bpseudomallei","brachyspira","bsubtilis","calbicans","campylobacter","cbotulinum","cconcisus","cdifficile","cdiphtheriae","cfetus","cfreundii","cglabrata","chelveticus","chlamydiales","chyointestinalis","cinsulaenigrae","ckrusei","clanienae","clari","cmaltaromaticum","cronobacter","csepticum","csinensis","csputorum","ctropicalis","cupsaliensis","ecloacae","fpsychrophilum","hcinaedi","hinfluenzae","hparasuis","hpylori","hsuis","kkingae","koxytoca","kseptempunctata","leptospira","leptospira_2","leptospira_3","llactis","lmonocytogenes","lsalivarius","mabscessus","magalactiae","mbovis","mcatarrhalis","mhaemolytica","mhyopneumoniae","mhyorhinis","mmassiliense","mplutonius","mpneumoniae","neisseria","orhinotracheale","otsutsugamushi","pacnes","pgingivalis","plarvae","pmultocida_multihost","pmultocida_rirdc","ppentosaceus","ranatipestifer","sagalactiae","sbsec","scanis","sdysgalactiae","sepidermidis","sgallolyticus","shaemolyticus","shominis","sinorhizobium","slugdunensis","smaltophilia","soralis","spseudintermedius","ssuis","sthermophilus","sthermophilus_2","streptomyces","suberis","szooepidemicus","taylorella","tenacibaculum","tvaginalis","vcholerae","vibrio","vparahaemolyticus","vtapetis","vvulnificus","wolbachia","xfastidiosa","yersinia","ypseudotuberculosis","yruckeri"], raw,3,2)
```
