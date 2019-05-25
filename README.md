## Project Machine learning

### Detect butterfly

1. Dataset
   In this project, I train 3 kind of butterfly

   - CommonBuckeye
   - MourningCloak
   - ParisPeacock
     Total about 1200 images
     Butterfly images was taken from google and many pages.
     I created 3 utils for getting, converting type image, changing name.

   _Script getting image from google image search_

```
var cont=document.getElementsByTagName("body")[0];
var imgs=document.getElementsByTagName("a");
var i=0;var divv= document.createElement("div");
var aray=new Array();var j=-1;
while(++i<imgs.length){
  if(imgs[i].href.indexOf("/imgres?imgurl=http")>0){
    divv.appendChild(document.createElement("br"));
    aray[++j]=decodeURIComponent(imgs[i].href).split(/=|%|&/)[1].split("?imgref")[0];
    divv.appendChild(document.createTextNode(aray[j]));
  }
}
cont.insertBefore(divv,cont.childNodes[0]);
```

_Script getting image from any page_

```
function getAllImgageSrc() {
  let count = 0;
  let imgs = "";
  document.querySelectorAll("img").forEach(img=>{
    imgs+=img.src+'\n'
    count++;
  })
  console.log("Image length: ", count);
  console.log(imgs);
}
```

   I used tool _Yolo-Annotation-Tool-New_ to create the bounding box for images

2. Training
   - I followed to this link: _https://medium.com/@manivannan_data/how-to-train-yolov3-to-detect-custom-objects-ccbcafeb13d2_
   - I trained model on Google Colab follow this link: _https://colab.research.google.com/drive/1lTGZsfMaGUpBG4inDIQwIJVW476ibXk_#scrollTo=wkzMqLZV-rF5_
   - I did almost the same, fix some error about the path to file
##### Thank you for sharing <3

3. Notes
   Some points I got stuck, I'm not sure with others
   - Because I used _google colab_ and got free 12GB GPU to training, So before _make_ command after clone yolov3 project. I changed _Makefile_ file: **GPU = 1** and **CUDNN=1**
   - In _butterfly-obj.data_ file. It will save a backup file and weight after 1000 at fist and 10000 times next by default
   - Because I don't want save after 10000 times, so I change _detector.c_ in _examples_ folder. \*_Line 138_ change to `if(i%500==0 || (i < 1000 && i%100 == 0)){ ...}`. It means it will save weights file after 100 times at first and 500 times for second time.
   - I saved _backup file_ and _wieghts_ in backup folder of google colab. So I need to download files before google reset
Finally, this is my notebok: _https://colab.research.google.com/drive/1HAc0G3hedpFuJ1XI1fNVZSAYJGiaoCgq?authuser=1#scrollTo=wrI19JfCeyZh_

#### Have a nice day!!!
