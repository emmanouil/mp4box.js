Log of X3DOMsupport
======

#####TODO:
* Add timing when adding XML content to DOM
* Introduce remove <x3d> from DOM
* Handle multiple XML files

#####CHECK:
* parseFromString function ( https://dvcs.w3.org/hg/innerhtml/raw-file/tip/index.html#namespaces )

#####Roadmap:
* Check X3D scene add
* Customize MovieTexture

#####HowTo:
* Create:
  MP4Box -add descriptor_file.nhml media_file.mp4
* Check:
  MP4Box -info media_file.mp4
* Extract Raw:
  MP4Box -raws $trackID$ media_file.mp4
*Extract NHML:
  MP4Box -nhml $trackID$ media_file.mp4


#####Known issues:

***
Currently testing:

Sample Descriptor
```XML
	<?xml version="1.0" encoding="UTF-8" ?>
	<NHNTStream version="1.0" timeScale="25000" trackID="3" mediaType="meta" mediaSubType="metx" text_encoding="utf-8" xml_namespace="http://www.web3d.org/specifications/x3d-namespace" xml_schema_location="http://www.web3d.org/specifications/x3d-3.0.xsd">
		<NHNTSample DTS="0"     isRAP="yes" mediaFile="first.x3d"/>
		<NHNTSample DTS="2500000" isRAP="yes" mediaFile="second.x3d" duration="100000"/>
	</NHNTStream>

```
***
XML with MovieTexture
```XML
<x3d width='854px' height='480px'>
	<scene>
		<shape>
			<appearance>
				<MovieTexture url='"./files/bunny480p.mp4"'></MovieTexture>
			</appearance>
			<box></box>
		</shape>
	</scene>
</x3d>
```

***
XML with Texture

first.x3d
```XML
<x3d xmlns="http://www.x3dom.org/x3dom" showStat="true" showLog="false" x="0px" y="0px" width='854px' height='480px'>
	<scene>
		<shape>
			<appearance>
				<Texture repeatS="false" repeatT="false" scale="true">
					<video id="x3d_vid" src='"./files/bunny[original].mp4"'>
					</video>
				</Texture>
			</appearance>
			<box size="4 4 4"></box>
		</shape>
	</scene>
</x3d>
```
second.x3d
```XML
<x3d xmlns="http://www.x3dom.org/x3dom" showStat="true" showLog="false" x="0px" y="0px" width='854px' height='480px'>
	<scene>
		<shape>
			<appearance>
				<Texture repeatS="false" repeatT="false" scale="true">
					<video id="x3d_vid" src="./files/bunny.mp4">
					</video>
				</Texture>
			</appearance>
			<box size="4 4 4"></box>
		</shape>
	</scene>
</x3d>
```
