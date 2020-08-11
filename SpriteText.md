# SpriteText.

A [sprite](https://threejs.org/docs/index.html#api/en/objects/Sprite) based text component. SpriteText is a text that always faces towards the camera.

## Quick start

### SpriteText

The easiest way to use SpriteText in your code is import SpriteText from SpriteText.js file in your JavaScript module. [Example](https://raw.githack.com/anhr/SpriteText/master/Examples/SpriteText.html).

```
import { SpriteText } from 'https://raw.githack.com/anhr/SpriteText/master/SpriteText.js';
```
or

* Create a folder on your localhost named as [folderName].
* Add your web page into [folderName]. See [example](https://raw.githack.com/anhr/SpriteText/master/Examples/SpriteText.html) web page.
* import [three.js](https://github.com/anhr/three.js)
```
import * as THREE from 'https://threejs.org/build/three.module.js';
```
or
```
import { THREE } from 'https://raw.githack.com/anhr/commonNodeJS/master/three.js';
```
or download [three.js](https://github.com/anhr/three.js) repository into your "[folderName]\three.js\dev" folder.
```
import * as THREE from './three.js/dev/build/three.module.js';
```
* Download [SpriteText](https://github.com/anhr/SpriteText) repository into your "[folderName]\SpriteText\master" folder.
```
import { SpriteText } from './SpriteText.js';
```

Now you can use SpriteText in your javascript code. See [SpriteText API](https://raw.githack.com/anhr/SpriteText/master/jsdoc/SpriteText/index.html) for details.

### SpriteTextGui

Add SpriteTextGui into [dat.gui](https://github.com/anhr/dat.gui) for manual change settings of the SpriteText.
[Example](https://raw.githack.com/anhr/SpriteText/master/Examples/SpriteTextGui.html)

Import dat.gui.
```
import { dat } from 'https://raw.githack.com/anhr/commonNodeJS/master/dat/dat.module.js';
```
or download [commonNodeJS](https://github.com/anhr/commonNodeJS) repository into your "[folderName]\commonNodeJS\master" folder.
```
import { dat } from './commonNodeJS/master/dat/dat.module.js';
```
Import SpriteTextGui.
```
import { SpriteTextGui } from 'https://raw.githack.com/anhr/SpriteText/master/SpriteTextGui.js';
```
or

* Use folder on your localhost named as [folderName]. See [SpriteText](https://github.com/anhr/SpriteText#spritetext-1) above.
* Download [SpriteText](https://github.com/anhr/SpriteText) repository into your "[folderName]\SpriteText\master" folder.

```
import { SpriteTextGui } from './SpriteTextGui.js';
```

Now you can use SpriteTextGui in your javascript code.
```
const gui =  new dat.GUI();
const folder = SpriteTextGui( gui, scene, {

	//getLanguageCode: getLanguageCode,
	//cookie: cookie,

} );
```
If you want to localize the gui, please uncomment
```
getLanguageCode: getLanguageCode,
```
line above and import getLanguageCode.
```
import { getLanguageCode } from 'https://raw.githack.com/anhr/commonNodeJS/master/lang.js';
```
or download [commonNodeJS](https://github.com/anhr/commonNodeJS) repository into your "[folderName]\commonNodeJS\master" folder.
```
import { getLanguageCode } from './commonNodeJS/master/lang.js';
```
If you want save a custom StereoEffect settings to the cookie, please uncomment
```
cookie: cookie,
```
line in the SpriteTextGui.gui(...) above and import cookie.
```
import cookie from 'https://raw.githack.com/anhr/cookieNodeJS/master/cookie.js';
```
or download [cookieNodeJS](https://github.com/anhr/cookieNodeJS) repository into your "[folderName]\cookieNodeJS\master" folder.
```
import cookie from './cookieNodeJS/master/cookie.js';
```

### group.userData.optionsSpriteText - common options for the group of the SpriteText
You can set options for all SpriteText from the [Group](https://threejs.org/docs/index.html#api/en/objects/Group) or [Scene](https://threejs.org/docs/index.html#api/en/scenes/Scene) and all child groups.
Options of the child groups is more priority before parent group options.
Example:
```
//options for all SpriteText on the scene
scene.userData.optionsSpriteText = {

	fontColor: 'rgb(0, 255, 0)'//green color

}
var group = new THREE.Group();

//options of the group and all child group
group.userData.optionsSpriteText = {

	fontColor: 'rgba(255, 255, 225, 0.5)'//white semi opacity color

}
scene.add( group );

scene.add( new SpriteText( 'Scene' ) );//green color of the font
group.add( new SpriteText( 'Group' ) );//white semi opacity color of the font
```

### folder.userData.restore() - Restore group.userData.optionsSpriteText to default values.
Example:
```
options = {

	textHeight: 0.1,
	sizeAttenuation: false,

}
const fSpriteTextAll = SpriteTextGui( gui, scene, {

	getLanguageCode: getLanguageCode,
	settings: { zoomMultiplier: 1.5, },
	options: options

} );

//Change of the text height
options.textHeight = 0.2;

//update of the options of all SpriteText, added in to group and all child groups
SpriteText.updateSpriteTextGroup( group );

//To do something...

//Restore options.textHeight to 0.1
fSpriteTextAll.userData.restore();
```