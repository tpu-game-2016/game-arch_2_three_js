
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Three.js sample</title>
  <style>
    body {
      text-align: center;
    }

    canvas { 
      width: 100%; 
      height: 100%;
      border: 1px solid black;
    }
  </style>
</head>

<body>
  <h1>Liquid Three.js Cube</h1>
  <p>Change the browser's window size.</p>
  <script src="https://github.com/mrdoob/three.js/blob/master/build/three.min.js"></script> <!-- 最新の Three.js を取得 -->
  <script>
    var scene = new THREE.Scene(); // Three.js シーンオブジェクトの生成
    var camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000); // カメラの設定

    var renderer = window.WebGLRenderingContext ? new THREE.WebGLRenderer() : new THREE.CanvasRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight); // ビューポートの大きさを設定
    document.body.appendChild(renderer.domElement); // レンダラをbodyに紐づけ

    var geometry = new THREE.CubeGeometry(20, 20, 20); // 四角形の生成
    var material = new THREE.MeshBasicMaterial({ color: 0x0000FF }); // マテリアルの作成（青）
    var cube = new THREE.Mesh(geometry, material); // メッシュとマテリアルからオブジェクトを生成
    scene.add(cube); // シーンに配置

    camera.position.z = 50; // カメラをZ軸上に置く

    var render = function () {
      cube.rotation.x += 0.01; // 少しずつ回転
      cube.rotation.y += 0.01;

      renderer.render(scene, camera); // 物体を描画
      requestAnimationFrame(render); // 60fpsで動かす
    };

    render(); // 描画を起動させる
  </script>
</body>
</html>
