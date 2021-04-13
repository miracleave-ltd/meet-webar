# 【Step1】WebVRを作成しよう
### ⑴初めに・・・
1. 当リポジトリをGitでクローン、またはDownloadZipしローカル上で展開してください。
![image](https://user-images.githubusercontent.com/66664167/114502898-71381f00-9c67-11eb-80a2-f4cd1eeba2bb.png)

### ⑵WebARの作成
1. Web上でARを可能とするには、Google社製model-viwerとMozilla社製A-frameがありますが、今回はA-frameを基に作っていきます。
2. ar.htmlという空のファイルを作成してください。
3. 作成したar.htmlに、以下コードを張り付けましょう。。<br>このプログラムは、A-frameとar.jsのライブラリを読み込むことで、ARを可能とします。
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

2. index.htmlという空のファイルを作成してください。
3. 作成したindex.htmlに、以下コードを張り付けて★ARのHTMLファイル名を指定★の部分作成したWebARのHTMLファイル名に置き換えます。<br>このプログラムとしては公式公開されているQRコードに必要なライブラリをscriptタグで読み込んで、jQueryでWebARのリンクをQRコード化させています。
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
1. 以下にアクセスしてください。<BR>
　https://vercel.com/signup
2. Githubアカウントでログインしてください。
![image](https://user-images.githubusercontent.com/66664167/114530379-d7cc3580-9c85-11eb-9438-4a97b98e69ff.png)

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
![image](https://user-images.githubusercontent.com/66664167/114528562-17921d80-9c84-11eb-8f71-959fcfc9e6df.png)
4. 登録メールアドレスにログイン確認が求められるので、「VERIFY」から確認する。


### ⑷デプロイ
1. 以下コマンドを実行し、デプロイしましょう。<br>※カレントディレクトリにあるファイルがデプロイされますので、今いるディレクトリが正しいか注意してください。

```
now
```

3. 「Sent up and deploy?」と求められるので```Y```を入力し、Enterを押してください。
4.  ```ユーザー名```を入力し、Enterを押してください。
5. 「Link to existing project?」と求められるので```N```を入力し、Enterを押してください。
6. 「Want to override the settings?」と求められるので```N```を入力し、Enterを押してください。
7. コマンド実行結果に、アクセス先が記載されているのでアクセスしてみよう。
![image](https://user-images.githubusercontent.com/66664167/114531193-a2741780-9c86-11eb-9c50-0f0851695952.png)
8. QRコードをスマートフォンのカメラ機能で読み取って、ARを動かしてみよう。


# 【Step3】応用編：WebARに好きな文字を表示してみよう
1. 文字データを作成するために、以下サイトにアクセスしましょう。
https://msdf-bmfont.donmccurdy.com/

2. 好きな文字を入力し、「CREATE MSDF」ボタンを押してください。
![image](https://user-images.githubusercontent.com/66664167/114529479-f2ea7580-9c84-11eb-9fa0-4a070e0339a2.png)

3. Step1で作成したar.htmlをテキストエディタで開き、value値を好きな文字と同じように修正しましょう。
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

4. 以下コマンドを実行し、再デプロイをしてみましょう。

```
now
```

5. コマンド実行結果に、アクセス先が記載されているのでアクセスしてみよう。
![image](https://user-images.githubusercontent.com/66664167/114530887-53c67d80-9c86-11eb-8e17-7dd56d6ce218.png)


# Tips
Vercel（バーセル）のダッシュボードからもデプロイ結果は確認できます。
```
https://vercel.com/dashboard
```
![image](https://user-images.githubusercontent.com/66664167/114531106-8bcdc080-9c86-11eb-9761-0c1ec3e2b292.png)
