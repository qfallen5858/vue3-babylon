<!--
 * @Author: your name
 * @Date: 2021-12-16 15:35:44
 * @LastEditTime: 2021-12-16 17:35:53
 * @LastEditors: your name
 * @Description: 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
 * @FilePath: \hello-vue3\src\components\HelloWorld.vue
-->
<template>
  <canvas id="renderCanvas"></canvas>
  
</template>
<script>
import * as BABYLON from 'babylonjs'

window.addEventListener('DOMContentLoaded', function(){
  let canvas = document.getElementById("renderCanvas");
  let engine = new BABYLON.Engine(canvas, true);

  let createScene = function(){
    let scene = new BABYLON.Scene(engine);
    let camera = new BABYLON.ArcRotateCamera("Camera", Math.PI / 2, Math.PI/2, 2, new BABYLON.Vector3(0,0,5), scene);
    camera.attachControl(true)
    new BABYLON.HemisphericLight("light1", new BABYLON.Vector3(1, 1, 0), scene);
    new BABYLON.PointLight("light2", new BABYLON.Vector3(0, 1, -1), scene);

    BABYLON.MeshBuilder.CreateSphere("sphere", {diameter:2}, scene);
    return scene;
  };

  let scene = createScene();

  engine.runRenderLoop(function(){
    scene.render();
  });

  window.addEventListener("resize", function(){
    engine.resize();
  })
})
</script>
<style scoped>
a {
  color: #42b983;
}

#renderCanvas{
  width: 100%;
  height: 100%;
}
</style>
