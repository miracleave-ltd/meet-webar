# 【Step1】WebVRを作成しよう
### ⑴初めに・・・
1. 当リポジトリをGitでクローン、またはDownloadZipしローカル上の任意フォルダで展開してください。
![image](https://user-images.githubusercontent.com/66664167/114502898-71381f00-9c67-11eb-80a2-f4cd1eeba2bb.png)

### ⑵WebARの作成
#### Web上でARを可能とするには、Google社製model-viewerとMozilla社製A-frameがありますが、今回はA-frameを基に作っていきます。
1. WebARのコードを記述するために、ar.htmlという名前の空ファイルを作成してください。
2. 作成したar.htmlに、以下コードを張り付けましょう。<br>このプログラムは、A-frameとar.jsのライブラリを読み込むことで、ARの実現を可能とします。
```
<!DOCTYPE html>
<html>
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
#### 手順⑴で作成した、WebARのHTMLファイルを読み込ませてQRコード化させるために、以下図の構造を作成します。
![image](https://user-images.githubusercontent.com/66664167/114794979-8c6e7000-9dc8-11eb-9b01-77a8402ff3b2.png)


1. QRコード化のコードを記述するために、index.htmlという名前の空ファイルを作成してください。
2. 作成したindex.htmlをテキストエディタで開きましょう。
3. 開いたindex.html、以下コードを張り付けます。
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
			jQuery('#output').qrcode(location.href + '/★★★');
		})
	</script>
</body>
</html>
```
4. 張り付けたコードの★★★の部分を⑴手順で作成したWebARのHTMLファイル名（ar.html）に置き換えます。<br>このコードは、必要なライブラリをscriptタグ（51-52行目）で読み込んで、jQueryで55行目に指定したURLをQRコード化させています。<br>

# 【Step2】Vercel（バーセル）を使ったサーバーレスデプロイをやってみよう
### ⑴Vercel（バーセル）とは・・・
Vercelはフロントエンド向けのホスティングサービスで、無料プランでも利用可能です（100回/日までデプロイ可）<BR>
Git（GitHub, GitLab, Bitbucket に対応）とVercel（バーセル）を連携させることができます。連携するとGit にプッシュされる度にデプロイすることも可能です。<BR>
また、```now```というコマンドで簡単にデプロイできる点も魅力です。

### ⑵Vercel（バーセル）のアカウント登録
1. サーバーレスデプロイを使うには、Vercel（バーセル）のアカウント登録が必要ですので、以下からアクセスしてください。<BR>
　https://vercel.com/signup
2. 「Continue with GitHub」から、Githubアカウントでログインしてください。
![image](https://user-images.githubusercontent.com/66664167/114530379-d7cc3580-9c85-11eb-9438-4a97b98e69ff.png)

### ⑶ローカル環境からVercel（バーセル）へのログイン
1. CUI（コマンドプロンプト/ターミナル）を起動してください。
2. 以下コマンドを実行し、【Step1】の⑴でクローンしたパスに移動してください。

```
cd 【Step1】の⑴でクローンしたパス
```

4. 以下コマンドを実行し、npmでVercel（バーセル）のデプロイコマンドとなる「now」インストールします。

```
npm i -g now
```

2. 以下コマンドを実行し、CUI上からVercel（バーセル）にログインします。

```
now login
```

3. githubに登録しているメールアドレスにログイン確認が求めるメールが送信されますので、登録しているメールの受信ボックスを確認してください。
![image](https://user-images.githubusercontent.com/66664167/114795909-aa3cd480-9dca-11eb-9c58-927de04a24db.png)

4. 登録メールアドレスにログイン確認が求められるので、「VERIFY」を押してください。
![image](https://user-images.githubusercontent.com/66664167/114528562-17921d80-9c84-11eb-8f71-959fcfc9e6df.png)


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
#### 好きな文字をWebAR上に表示されるには、文字データを作成しその文字データをコードに埋め込みます。
1. 文字データを作成する、以下サイトにアクセスしましょう。
https://msdf-bmfont.donmccurdy.com/

2. 「2. Select character set」の欄に表示させたい文字を入力し、「CREATE MSDF」ボタンを押してください。
![image](https://user-images.githubusercontent.com/66664167/114529479-f2ea7580-9c84-11eb-9fa0-4a070e0339a2.png)

3. custom-msdf.zipがダウンロードされますので、zipファイルを展開してください。
4. 展開した中に、以下2ファイルがあると思いますので、【Step1】の⑴でクローンしたパスに２つのファイルを移動してください。<BR>※【Step1】の⑴でクローンしたパスに、既に同じファイルが存在するかと思いますが上書きで大丈夫です。
* custom.png
* custom-msdf.json
6. Step1で作成したar.htmlをテキストエディタで開き、以下を修正しましょう。
* value（144行目）
* scale（150行目）
* position（151行目）
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

4. 以下コマンドを実行し、再デプロイをしてみましょう。<BR>初回以降のデプロイはコマンド一つで簡単に実施出来ます。

```
now
```

5. コマンド実行結果に、アクセス先が記載されているのでアクセスしてみよう。
![image](https://user-images.githubusercontent.com/66664167/114530887-53c67d80-9c86-11eb-8e17-7dd56d6ce218.png)


# Tips
* Vercel（バーセル）のダッシュボードからもデプロイ結果は確認できます。
```
https://vercel.com/dashboard
```
![image](https://user-images.githubusercontent.com/66664167/114531106-8bcdc080-9c86-11eb-9761-0c1ec3e2b292.png)

* Vercel（バーセル）とGitHubリポジトリとの連携も可能です。
