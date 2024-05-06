# Instagram 3D 旋转照片墙

```template
<div class="instagram-box">
  <div class="instagram" :style="setImageInstagram(roX, roY)">
    <img 
      v-for="(image, i) in props.images"  
      :src="image.src" 
      class="image"
      draggable="false"
      :style="setImageTransform(i)" 
    >
  </div>
</div>
```
```js
  import { ref, defineProps, computed, onMounted } from 'vue'
  const props = defineProps({ 
    images: Array,
    imageHeight: Number | String
  })
  // 计算旋转角度
  const deg = 360/props.images.length
  // 点击时、移动时坐标
  const mouseDownX = ref(0)  
  const mouseDownY = ref(0)   
  const mouseMoveX = ref(0)
  const mouseMoveY = ref(0)
  // 旋转量 = 移动时 - 点击时
  const roX = computed(() => { return  -10 - (mouseMoveY.value - mouseDownY.value) * 0.2 })
  const roY = computed(() => { return (mouseMoveX.value - mouseDownX.value) * 0.2 })

  // 遍历变形 IMG
  function setImageTransform(i){ 
    return { transform: 'rotateY(' + i*deg + 'deg) translateZ(300px) translateY(-50%)' } 
  }
  // 绑定 height/width, 绑定 computed 偏移量到容器
  function setImageInstagram(roX, roY){
    var height = props.imageHeight + 'px'
    var width = 2/3 * props.imageHeight + 'px'
    return { 
        transform: 'perspective(800px) rotateX(' + roX + 'deg) rotateY(' + roY + 'deg)',
        height: height,
        width: width
      } 
  }

  // 移动时，获取坐标
  function onMousemove(ev){
    mouseMoveX.value = ev.clientX;
    mouseMoveY.value = ev.clientY;    
  }
  // 点击时，获取坐标，挂载移动时处理函数
  function onMousedown(ev){
    mouseDownY.value = ev.clientY;
    mouseDownX.value = ev.clientX;
    mouseMoveX.value = mouseDownX.value
    mouseMoveY.value = mouseDownY.value
    document.addEventListener('mousemove', onMousemove)
  }

  // 松开时，注销移动时处理函数
  function onMouseup(){
    document.removeEventListener('mousemove', onMousemove)
      mouseMoveX.value=0
      mouseMoveY.value=0
      mouseDownX.value=0
      mouseDownY.value=0
  }
  // 挂载事件
  onMounted(()=>{
    document.addEventListener('mousedown', onMousedown)
    document.addEventListener('mouseup', onMouseup)
  })
```
```sass
.box
  display: block
  height: 500px
  width: 3400px
  .instagram
    display: block   
    position: relative
    // transform 旋转元素
    transform-style: preserve-3d
    // 居中
    top: 50%
    left: 40%
    img
      position: absolute
      width: 100%
      height: 100%
      border-radius: 5px
      box-shadow: 0px 0px 10px #fff
      /*倒影的设置*/
      -webkit-box-reflect: below 10px -webkit-linear-gradient(top,rgba(0,0,0,0) 50%,rgba(0,0,0,.5) 100%)
```