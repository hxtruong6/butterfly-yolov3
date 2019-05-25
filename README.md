##Project Machine learning
### Detect butterfly
1. Dataset
  In this project, I train 3 kind of butterfly
    - CommonBuckeye
    - MourningCloak
    - ParisPeacock
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