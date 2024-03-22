
<template>
  <h1>旅行伙伴加入表情包生成器</h1>
  <h2>生成属于你的旅行伙伴</h2>
  <h3>现在,上传一张图片吧:</h3>
  <input type="file" @change="handleFileChange">
  <input type="number" v-model="scaleValue" @input="handleScaleChange" step="0.1" min="0.1" max="2" placeholder="缩放比(测试中)"><br><br>
  <p>旅行伙伴的名称为:</p>
  <n-input v-model:value="partname" type="text" placeholder="旅行伙伴名称" />
  <button @click="exportCanvas">导出图片</button>
  <br><br>
  <canvas id="myCanvas" ref="canvasRef" width="507" height="512"> </canvas>
  <p>晚江右海作品 2024.3</p>
</template>
<script>
import { defineComponent, ref, onMounted } from 'vue';
import avatarFrame from './assets/original.png';

export default defineComponent({
  setup() {
    const canvasRef = ref(null);
    let userImg = new Image();
    let scaleValue = 1;
    let partname = ref(null);

    const handleFileChange = (event) => {
      const file = event.target.files[0];
      const reader = new FileReader();

      reader.onload = () => {
        userImg.onload = () => {
          redrawCanvas();
        };

        userImg.src = reader.result;
      };

      if (file) {
        reader.readAsDataURL(file);
      }
    };

    const handleScaleChange = () => {
      redrawCanvas();
    };

    const redrawCanvas = () => {
      const canvas = canvasRef.value;
      const ctx = canvas.getContext('2d');

      canvas.width = userImg.width * scaleValue;
      canvas.height = userImg.height * scaleValue;

      ctx.drawImage(userImg, 0, 0, canvas.width, canvas.height);

      const frameImg = new Image();
      frameImg.onload = () => {
        ctx.drawImage(frameImg, 0, 0, canvas.width, canvas.height);
      };
      frameImg.src = avatarFrame; // 加载头像框图片
    };
    const exportCanvas = () => {
      const canvas = canvasRef.value;
      const dataURL = canvas.toDataURL('image/png');
      const a = document.createElement('a');
      a.href = dataURL;
      a.download = '旅行伙伴'+partname.value+'加入了哦.png'; // 设置下载文件名
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    };

    return {
      canvasRef,
      handleFileChange,
      handleScaleChange,
      scaleValue,
      exportCanvas,
      partname: partname,
    };
  }
});


</script>
<style scoped>

</style>
