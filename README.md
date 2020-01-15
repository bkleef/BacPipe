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

Not all _species_ fit in the drop down, it is not scrollable, which means that the lower items cannot be selected.

The default value is _ecoli_ and is set in [`configure.yaml`](https://github.com/bkleef/BacPipe/blob/master/configure.yaml#L17):

```yaml
mlst_typing:
  organism: ecolis
```

The order of items in the drop down is determined in: [`Pipeline.py`](https://github.com/bkleef/BacPipe/blob/master/Pipeline.py#L1953):

```python
app.addLabelOptionBox("Species", ["ecoli","ecoli_2","kpneumoniae","paeruginosa","pfluorescens","abaumannii","abaumannii_2","senterica","saureus","spneumoniae","spyogenes","efaecalis","efaecium","----------------------------","achromobacter","aeromonas","afumigatus","aphagocytophilum","arcobacter","bcc","bcereus","bhampsonii","bhenselae","bhyodysenteriae","bintermedia","blicheniformis","bordetella","borrelia","bpilosicoli","bpseudomallei","brachyspira","bsubtilis","calbicans","campylobacter","cbotulinum","cconcisus","cdifficile","cdiphtheriae","cfetus","cfreundii","cglabrata","chelveticus","chlamydiales","chyointestinalis","cinsulaenigrae","ckrusei","clanienae","clari","cmaltaromaticum","cronobacter","csepticum","csinensis","csputorum","ctropicalis","cupsaliensis","ecloacae","fpsychrophilum","hcinaedi","hinfluenzae","hparasuis","hpylori","hsuis","kkingae","koxytoca","kseptempunctata","leptospira","leptospira_2","leptospira_3","llactis","lmonocytogenes","lsalivarius","mabscessus","magalactiae","mbovis","mcatarrhalis","mhaemolytica","mhyopneumoniae","mhyorhinis","mmassiliense","mplutonius","mpneumoniae","neisseria","orhinotracheale","otsutsugamushi","pacnes","pgingivalis","plarvae","pmultocida_multihost","pmultocida_rirdc","ppentosaceus","ranatipestifer","sagalactiae","sbsec","scanis","sdysgalactiae","sepidermidis","sgallolyticus","shaemolyticus","shominis","sinorhizobium","slugdunensis","smaltophilia","soralis","spseudintermedius","ssuis","sthermophilus","sthermophilus_2","streptomyces","suberis","szooepidemicus","taylorella","tenacibaculum","tvaginalis","vcholerae","vibrio","vparahaemolyticus","vtapetis","vvulnificus","wolbachia","xfastidiosa","yersinia","ypseudotuberculosis","yruckeri"], raw,3,2)
```

To use a value that cannot be selected, I recommend defining it in `configure.yaml` before starting the program. For example:

```yaml
mlst_typing:
  # organism: ecolis
  organism: szooepidemicus
```
