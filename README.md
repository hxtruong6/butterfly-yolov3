##Project Machine learning
### Detect butterfly
1. Dataset
  In this project, I train 3 kind of butterfly
    - CommonBuckeye
    - MourningCloak
    - ParisPeacock
  Total about 1200 images
  Butterfly images was taken from google and many pages.
  I created 3 utils for getting, converting type image, changing name.

  *Script getting image from google image search*
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
  *Script getting image from any page*
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
  I used tool *Yolo-Annotation-Tool-New* to create the bounding box for images
2. Training
  I followed to this link: *https://medium.com/@manivannan_data/how-to-train-yolov3-to-detect-custom-objects-ccbcafeb13d2*
  I trained model on Google Colab follow this link: *https://colab.research.google.com/drive/1lTGZsfMaGUpBG4inDIQwIJVW476ibXk_#scrollTo=wkzMqLZV-rF5*
  I did almost the same, fix some error about the path to file
  Thank you for sharing <3
3. Notes
  Some points I got stuck, I'm not sure with others
  - Because I used *google colab* and got free 12GB GPU to training, So before *make* command after clone yolov3 project. I changed *Makefile* file: **GPU = 1** and **CUDNN=1**
  - In *butterfly-obj.data* file. Backup should be point to your drive. It will save a backup file and weight after 1000 at fist and 10000 times next by default
  - Because I don't want save after 10000 times, so I change *detector.c* in *examples* folder. **Line 138* change to ``` if(i%500==0 || (i < 1000 && i%100 == 0)){ ...} ```. It means it will save weights file after 100 times at first and 500 times for second time.
  
Finally, this is my notebok: *https://colab.research.google.com/drive/1HAc0G3hedpFuJ1XI1fNVZSAYJGiaoCgq?authuser=1#scrollTo=wrI19JfCeyZh*
##### Have a nice day!!!
