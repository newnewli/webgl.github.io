﻿#### 环境贴图高级
<p><iframe style="width: 100%; height: 520px; text-align:center;" src="/nehe_webgl/lessons/NeHeWebGL16.html" frameborder="0" width="500" height="500"></iframe></p>

#### 源码笔记
```
<html>

<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>WebGL实现多个物体运动的效果</title>


    <script type="text/javascript" src="../lib/Oak3D_v_0_5.js"></script>
    <script src="../js/MultiStarsMove.js"></script>

    <script id="shader-fs" type="x-shader/x-fragment">

    precision mediump float;


    varying vec2 vTextureCoord;
    uniform sampler2D uSampler;

    uniform vec3 uColor;

    void main(void) {
        vec4 textureColor = texture2D(uSampler, vec2(vTextureCoord.s, vTextureCoord.t));
        gl_FragColor = textureColor * vec4(uColor, 1.0);
    }

    </script>

    <script id="shader-vs" type="x-shader/x-vertex">
    attribute vec3 aVertexPosition;
    attribute vec2 aTextureCoord;

    uniform mat4 uMVMatrix;
    uniform mat4 uPMatrix;

    varying vec2 vTextureCoord;

    void main(void) {
        gl_Position = uPMatrix * uMVMatrix * vec4(aVertexPosition, 1.0);
        vTextureCoord = aTextureCoord;
    }

    </script>


</head>


<body onload="webGLStart();">

<canvas id="lesson09-canvas" style="border: none;" width="500" height="500"></canvas>

<br/>
<input type="checkbox" id="twinkle"/> 闪光<br/>
（使用上/下方向键进行旋转，使用 <code>Page Up</code>键和<code>Page Down</code>键进行缩放）

<br/>
</body>

</html>

```