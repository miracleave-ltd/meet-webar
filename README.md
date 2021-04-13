# 【Step1】WebVRを作成しよう
### ⑴初めに
1. 当リポジトリをGitでクローン、またはDownloadZipし、ローカルで展開してください。
![image](https://user-images.githubusercontent.com/66664167/114502898-71381f00-9c67-11eb-80a2-f4cd1eeba2bb.png)

### ⑵WebARの作成
1. Web上でARを可能とするには、Google社製model-viwerとMozilla社製A-frameがありますが、今回はA-frameを基に作っていきます。
2. 
```
<!DOCTYPE html>
<html>
  <head>
  <head>
    <meta charset="utf-8" />
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
    <script src="https://jeromeetienne.github.io/AR.js/aframe/build/aframe-ar.js"></script>
    <title>WebAR</title>
  </head>
  <body>
    <a-scene embedded arjs="debugUIEnabled:false; sourceType: webcam;">
      <a-text
        value="ようこそ！mira meetへ！！"
        font="custom-msdf.json"
        font-image="custom.png"
        negate="false"
        scale="2 2 1"
        position="0 1 -4"
        color="red">
      </a-text>
    </a-scene>
  </body>
</html>
```

### ⑵スマートフォン上から簡単にアクセスするために、QRコード化しよう
1. 作成したWebARをQRコード化させて読み込むために、以下のような構造を作成します。
![image](https://user-images.githubusercontent.com/66664167/114505643-a9416100-9c6b-11eb-8e49-bd0f125e0497.png)


2. 最初に読み込ませたいのでindex.htmlを作成し、以下コードを張り付けて★ARのHTMLファイル名を指定★の部分作成したWebARのHTMLファイル名に置き換えます。<br>このプログラムとしては公式公開されているQRコードに必要なライブラリをscriptタグで読み込んで、jQueryでWebARのリンクをQRコード化させています。
```
<!DOCTYPE html>
<html>
<head>
	<title>meet up vol.15</title>
</head>
<body>
	<div id="output"></div>

	<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.5.2/jquery.min.js"></script>
	<script type="text/javascript" src="jquery-qrcode-master/jquery.qrcode.min.js"></script>
	<script>
		jQuery(function(){
			jQuery('#output').qrcode(location.href + '/★ARのHTMLファイル名を指定★');
		})
	</script>
</body>
</html>
```

# 【Step2】Vercel（バーセル）を使ったサーバーレスデプロイをやってみよう
### ⑴Vercel（バーセル）とは・・・
VercelはZEIT社が提供する、フロントエンド向けのホスティングサービスで、無料プランでも利用可能です（100回/日までデプロイ可）<BR>
Git（GitHub, GitLab, Bitbucket に対応）とVercelを連携させることができます。連携するとGit にプッシュされる度にデプロイすることも可能です。<BR>
また、```now```というコマンドで簡単にデプロイできる点も魅力です。

### ⑵Vercel（バーセル）のアカウント登録
1. 以下にアクセスしてください。
　https://vercel.com/signup
2. Githubアカウントでログインしてください。

### ⑶ローカル環境からVercel（バーセル）へのログイン
1. 以下コマンドを実行

```
npm i -g now
```

2. CUIからVercel（バーセル）にログインするために、以下コマンドを実行しましょう。

```
now login
```

3. githubに登録しているメールアドレスにログイン確認が求められるので入力。
4. 登録メールアドレスにログイン確認が求められるので、「VERIFY」から確認する。


### ⑷デプロイ
1. 以下コマンドを実行し、デプロイする。<br>※カレントディレクトリにあるファイルがデプロイされますので、今いるディレクトリが正しいか注意してください。

```
now
```

3. Y→N入力
4. ZEITのダッシュボードにアクセスすると、デプロイした「webvr-main」フォルダが配置されていることを確認すしましょう。

```
https://vercel.com/dashboard
```

5. ダッシュボードにアクセスし、「VISIT」からデプロイした内容にアクセスし、QRコードが表示されることを確認しましょう。
6. QRコードをスマートフォンのカメラ機能で読み取って、ARを動かしてみよう。


# 【Step3】応用編：WebARを色々修正してみよう
1. 以下より、フォントを作成する。
https://msdf-bmfont.donmccurdy.com/
