# 001.london
3d model spinner


First of all, watch this video to understand a bit of whats going to happen:
https://www.youtube.com/watch?v=1TeMXIWRrqE

I did almost everything the same except that I exported my model from blender as a .glb instead of a .gltf. For blender, when you export it, make sure to click the box that says export as glTF 2.0 and then select glb in the dropdown on the next screen

Next go to shopify and most importantly I want you to backup your website. Go to Theme> Download theme file and export it to your email. Once that is done, go to Theme > Edit code

First of all, you want to create a new home page as you will actually replace the page that shopify sees as your "index". Simply click "add a new template" under the Templates folder and make it a new tamplate for "page" called "home". It should open a blank file(if its not blank then delete all of the auto generated code). You want it to have only the following line of code(copy and paste it exactly):
{{ content_for_index }}

Then on your actual shopify admin dashboard, under sales channels go to online store>pages> and click Add Page. Title it "Home" and under the Template option in the right side of your screen, select the template suffix to be "page.home"and save it. If you want to see if it worked properly, click the preview button and it should take you to your website's index but the url should be "yourdomain.com/home"

The actual process of rendering the 3d model is done by using the ThreeJS library.(https://threejs.org)
Download the library from their website and upload the following three files to your Assets folder by clicking Add a new asset and selecting the files:
three.js
three.min.js
three.module.js
Upload your 3d model "glb" file to this section aswell.

Next, Under the Assets Folder, click Add new Asset. You will want to create a page called GLTFLoader.js and copy the code from this link: https://github.com/mrdoob/three.js/blob/master/examples/js/loaders/GLTFLoader.js

You will want to do the same process again but make the new file called OrbitControls.js and copy this code: https://github.com/mrdoob/three.js/blob/master/examples/js/controls/OrbitControls.js

Create another file in the assets folder named "spinner.js". Here is my personal spinner.js class customized to fit my website, theres comments on it to clarify what stuff means: https://pastebin.com/y9pQRLgi
You are going to want to change stuff up in this one especially on line 56, this is where you are going to put your 3d file you exported as a glb. But you can't simply reference it, you have to actually find the root location of the file on your shopify site and set that as the source.

-------- UPDATED --------

To finally get the changes to show up, theres two more steps to follow.
First, create a new file under the Layout folder by clicking "Add a new layout". When prompted, select "Create a new layout from 'Theme' called 'landing'" and click 'Create Layout'. In this file you will add the code that is included in this github repository under "theme.landing.liquid".  (https://github.com/PatricioBunt/001.london/blob/master/theme.landing.liquid)

Next and finally, you have to replace the code in your "index.liquid" file under the Templates folder. It should just say "{{ content_for_index }}", so erase that and replace it with the code I included in this github for "index.liquid". (https://github.com/PatricioBunt/001.london/blob/master/index.liquid)
Thats it! Save your changes and you should see it work once you refresh your page!
