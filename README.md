<html lang="ja">
    <head>
        <meta charset="utf-8" />
    </head>
    <body>
        <h1><center>RgbPly</center></h1>
        <h2>なにものか？</h2>
        <p>
            RGB画像とテクスチャ座標付き3Dデータ(.ply)を指定してテクスチャーマップされた3Dオブジェクトを表示します。
<br>
            <img src="images/RgbPly.png">
        </p>
        <h2>環境構築方法</h2>
        <p>
            pip install opencv-python PyOpenGL glfw
        </p>
        <h2>使い方</h2>
        <p>
            python  RgbPly.py  (RGB画像ファイル)  (テクスチャー座標付きPLYファイル)  [(zスケール)]<br>
            ※ ピクセルとz値の比率が不明のため、zスケール引数で調整します。<br>
            <img src="images/usage.svg">
            <table border="1">
                <tr><th>操作</th><th>機能</th></tr>
                <tr><td>左ボタン押下＋ドラッグ</td><td>3Dモデルの回転(yaw,pitch)</td></tr>
                <tr><td>rキー押下＋ホイール回転</td><td>3Dモデルの回転(roll)</td></tr>
                <tr><td>右ボタン押下＋ドラッグ</td><td>3Dモデルの移動</td></tr>
                <tr><td>ホイール回転</td><td>3Dモデルの拡大・縮小</td></tr>
                <tr><td>ホイールボタン押下</td><td>慣性モードのトグル(on⇔off)</td></tr>
                <tr><td>iキー押下</td><td>(同上)</td></tr>
                <tr><td>sキー押下</td><td>スクリーンショット保存</td></tr>
                <tr><td>ウィンドウ閉じるボタン押下　</td><td>プログラム終了</td></tr>
            </table>
        </p>
        <h2>テクスチャー座標付きPLYファイルの作成例</h2>
        <h3>ステップ１. depth推定ソフトウェアで画像からdepth画像を作成する。</h3>
        <p>
            Depth Anything V2 などを使って画像からdepth画像を作成する。<br>
            <a href="https://huggingface.co/spaces/depth-anything/Depth-Anything-V2">https://huggingface.co/spaces/depth-anything/Depth-Anything-V2</a><br>
            <br>
            <img src="images/step1_1.svg">
         </p>
        <h3>ステップ２. depth画像を三角形分割して密なPLYファイルを作成する。</h3>
        <p>
            python depth2ply.py (depth画像ファイル名)<br>
            ⇒ (depth画像ファイル名).ply が作成される。<br>
            <img src="images/step2_1.svg">
        </p>
        <h3>ステップ３. 密なPLYファイルを間引いて疎なPLYファイルを作成する。</h3>
        <h4>Blender 3.6 を使って間引く例</h4>
        <p>
            ①Blender 3.6を起動し、スプラッシュ画像以外をクリックする。<br>
            <img src="images/step3_1.svg"><br>
            ②立方体をクリックし、DELキーを押下して削除する。<br>
            <img src="images/step3_2.svg"><br>
            ③ファイル → インポート → スタンフォード(.ply) → ステップ２で作成したPLYファイルを開く。<br>
            <img src="images/step3_3.svg"><br>
            ④レンチの形をしたアイコン(モディファイアーアイコン)をクリックする。<br>
            <img src="images/step3_4.svg"><br>
            ⑤モディファイアーを追加をクリックする。<br>
            <img src="images/step3_5.svg"><br>
            ⑥デシメートをクリックする。<br>
            <img src="images/step3_6.svg"><br>
            ⑦比率を指定し、面数が減るのを待つ<br>
            例) 1/100に間引きたい場合は 0.01 を指定する。<br>
            <img src="images/step3_7.svg"><br>
            ⑧ファイル → エクスポート → スタンフォード(.ply) → 間引かれたPLYファイルを保存する。<br>
            <img src="images/step3_8.svg"><br>
        </p>
    </body>
</html>
