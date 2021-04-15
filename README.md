# meet-webar
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [【Step1】WebARを作成しよう](#step1webar%E3%82%92%E4%BD%9C%E6%88%90%E3%81%97%E3%82%88%E3%81%86)
    - [⑴初めに](#%E2%91%B4%E5%88%9D%E3%82%81%E3%81%AB)
    - [⑵WebARの作成](#%E2%91%B5webar%E3%81%AE%E4%BD%9C%E6%88%90)
    - [⑶スマートフォンから簡単にアクセスするために、WebARのページをQRコード化しよう](#%E2%91%B6%E3%82%B9%E3%83%9E%E3%83%BC%E3%83%88%E3%83%95%E3%82%A9%E3%83%B3%E3%81%8B%E3%82%89%E7%B0%A1%E5%8D%98%E3%81%AB%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B9%E3%81%99%E3%82%8B%E3%81%9F%E3%82%81%E3%81%ABwebar%E3%81%AE%E3%83%9A%E3%83%BC%E3%82%B8%E3%82%92qr%E3%82%B3%E3%83%BC%E3%83%89%E5%8C%96%E3%81%97%E3%82%88%E3%81%86)
- [【Step2】Vercel（バーセル）を使ったサーバーレスデプロイをやってみよう](#step2vercel%E3%83%90%E3%83%BC%E3%82%BB%E3%83%AB%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%9F%E3%82%B5%E3%83%BC%E3%83%90%E3%83%BC%E3%83%AC%E3%82%B9%E3%83%87%E3%83%97%E3%83%AD%E3%82%A4%E3%82%92%E3%82%84%E3%81%A3%E3%81%A6%E3%81%BF%E3%82%88%E3%81%86)
    - [⑴Vercel（バーセル）とは・・・](#%E2%91%B4vercel%E3%83%90%E3%83%BC%E3%82%BB%E3%83%AB%E3%81%A8%E3%81%AF%E3%83%BB%E3%83%BB%E3%83%BB)
    - [⑵Vercel（バーセル）のアカウント登録](#%E2%91%B5vercel%E3%83%90%E3%83%BC%E3%82%BB%E3%83%AB%E3%81%AE%E3%82%A2%E3%82%AB%E3%82%A6%E3%83%B3%E3%83%88%E7%99%BB%E9%8C%B2)
    - [⑶ローカル環境からVercel（バーセル）へのログイン](#%E2%91%B6%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E7%92%B0%E5%A2%83%E3%81%8B%E3%82%89vercel%E3%83%90%E3%83%BC%E3%82%BB%E3%83%AB%E3%81%B8%E3%81%AE%E3%83%AD%E3%82%B0%E3%82%A4%E3%83%B3)
    - [⑷デプロイの実施](#%E2%91%B7%E3%83%87%E3%83%97%E3%83%AD%E3%82%A4%E3%81%AE%E5%AE%9F%E6%96%BD)
- [【Step3】マーカーベースのWebARを作ってみよう](#step3%E3%83%9E%E3%83%BC%E3%82%AB%E3%83%BC%E3%83%99%E3%83%BC%E3%82%B9%E3%81%AEwebar%E3%82%92%E4%BD%9C%E3%81%A3%E3%81%A6%E3%81%BF%E3%82%88%E3%81%86)
- [Tips](#tips)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

***
# 【Step1】WebARを作成しよう
### ⑴初めに
1. 当ページの上部から当リポジトリをGitでクローン、またはDownloadZipしローカル上の任意フォルダで展開してください。<br/>
![image](https://user-images.githubusercontent.com/66664167/114502898-71381f00-9c67-11eb-80a2-f4cd1eeba2bb.png)
<br/><br/>

### ⑵WebARの作成
Web上でARを可能とするには、Google社製model-viewerとMozilla社製A-frameがありますが、今回はA-frameを基に作っていきます。<br/>
1. 【Step1】の⑴でクローンしたパスを開きます。<br/>（例：C:\workspace\miracleave\meetup\meet-webar）
2. 開いたフォルダ直下に、WebARのコードを記述するために、ar.htmlという名前の空ファイルを作成してください。
3. 作成したar.htmlに、以下コードを張り付けましょう。<BR>WebARには、画像や3D、そしてアニメーションの表示が可能ですが、今回はテキストを表示してみます。
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
    <script src="https://jeromeetienne.github.io/AR.js/aframe/build/aframe-ar.js"></script>
    <title>mirameetvol15</title>
  </head>
  <body>
    <a-scene embedded arjs="debugUIEnabled:false; sourceType: webcam;">
        <a-text position="0 1 -2"
         rotation="0 0 0"
         value="meet up!!"
         color="red"
         scale="1 1 1"></a-text>
    </a-scene>
  </body>
</html>
```
4. 上記コードは、A-frameとar.jsのライブラリを5-6行目で読み込むことで、body部にARの実現を可能する各タグが使用できます。
今回は以下のタグを使用しています。
* a-scene・・・シーンと呼ばれる部分です。ARを表現するものは全てこのタグ内に記載する必要があります。
* a-text・・・ARでtext文字を表示するタグです。
<br/><br/>

### ⑶スマートフォンから簡単にアクセスするために、WebARのページをQRコード化しよう
手順⑵で作成した、WebARのHTMLファイルを読み込ませてQRコード化させるために、以下のような構造を作成します。<br/>
![image](https://user-images.githubusercontent.com/66664167/114813727-a8d0d380-9ded-11eb-9f83-a1e5ea6dbbde.png)

1. 先ほどと同様に【Step1】の⑴でクローンしたパス直下に、QRコード化のコードを記述するために、index.htmlという名前の空ファイルを作成してください。
3. 作成したindex.htmlをテキストエディタで開きましょう。
4. 開いたindex.html、以下コードを張り付けます。
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
			jQuery('#output').qrcode(location.href + '/ar.html');
		})
	</script>
</body>
</html>
```
4. このコードは、必要なライブラリをscriptタグ（8-9行目）で読み込み、jQueryで12行目に指定したURLをQRコード化させています。あらかじめ、クローン（またはDownloadZip）したフォルダにはQRコードのライブラリが入ってますので、今回はscriptタグの記述のみでQRコード化が可能となります。
<br/><br/>

***
# 【Step2】Vercel（バーセル）を使ったサーバーレスデプロイをやってみよう
### ⑴Vercel（バーセル）とは・・・
Vercelはフロントエンド向けのホスティングサービスで、無料プランでも利用可能です（100回/日までデプロイ可）<br/>
Git（GitHub, GitLab, Bitbucket に対応）とVercel（バーセル）を連携させることができます。連携するとGit にプッシュされる度にデプロイすることも可能です。<br/>
また、```now```というコマンドで簡単にデプロイできる点も魅力です。
<br/><br/>

### ⑵Vercel（バーセル）のアカウント登録
1. サーバーレスデプロイを使うには、Vercel（バーセル）のアカウント登録が必要ですので、以下からアクセスしてください。<BR>
https://vercel.com/signup
2. 「Continue with GitHub」から、Githubアカウントでログインしてください。<br/>
![image](https://user-images.githubusercontent.com/66664167/114530379-d7cc3580-9c85-11eb-9438-4a97b98e69ff.png)
<br/><br/>

### ⑶ローカル環境からVercel（バーセル）へのログイン
1. CUI（コマンドプロンプト/ターミナル）を起動してください。
2. 以下コマンドを実行し、【Step1】の⑴でクローンしたパスに移動してください。

```
cd 【Step1】の⑴でクローンしたパス
```

4. 以下コマンドを実行し、npmでVercel（バーセル）のデプロイを行うコマンド「now」をインストールします。

```
npm i -g now
```

2. 以下コマンドを実行し、CUI上からVercel（バーセル）にログインします。

```
now login
```

3. githubに登録しているメールアドレスにログイン確認が求めるメールが送信されますので、登録しているメールの受信ボックスを確認してください。（以下、受信例）<br/>
![image](https://user-images.githubusercontent.com/66664167/114812872-db79cc80-9deb-11eb-9147-1afc8a165403.png)

4. 登録メールアドレスにログイン確認が求められるので、「VERIFY」を押してください。<br/>
![image](https://user-images.githubusercontent.com/66664167/114528562-17921d80-9c84-11eb-8f71-959fcfc9e6df.png)

5. CUI上でも待機状態から進み、ログインが出来ていることを確認します。
<br/><br/>

### ⑷デプロイの実施
1. 以下コマンドを実行し、デプロイしましょう。カレントディレクトリにあるファイルがデプロイされますので、今いるディレクトリが正しいか注意してください。

```
now
```

3. 初回デプロイのため、いくつかCUI上での確認が必要となりますので、以下の通り入力してください。<r>※2回目以降のデプロイでは求められません。
* 「Sent up and deploy?」（デプロイ元の確認）<BR>　　→　```Y```を入力し、Enterを押下。
* 「Which scope do you want to deploy to?」（デプロイ先の確認）<BR>　　→　Enterを押下。
* 「Link to existing project?」（既存プロジェクトとの連携の確認）<BR>　　→　```N```を入力し、Enterを押下。
* 「What’s your project’s name?」（プロジェクト名の確認）<BR>　　→　Enterを押下。
* 「In which directory is your code located?」（コードのディレクトリ確認）<BR>　　→　Enterを押下。
* 「Want to override the settings?」（設定情報の引き継ぎ）<BR>　　→　```N```を入力しEnterを押してください。

4. 以下、コマンド実行結果の例ですが、コマンド実行結果の「Production: https～」から始まる行に、デプロイしたアクセス先が記載されているのでアクセスしてみましょう。<br/>
![image](https://user-images.githubusercontent.com/66664167/114531193-a2741780-9c86-11eb-9c50-0f0851695952.png)

5. PC上に表示されたQRコードを、スマートフォンのカメラ機能で読み取って、WebARページの表示とARを表示させてみましょう。<br/>
![image](https://user-images.githubusercontent.com/66664167/114810914-02ce9a80-9de8-11eb-870e-894ff1175198.png)
<br/><br/>
	
***
# 【Step3】マーカーベースのWebARを作ってみよう
マーカーベースは、特定のテキストや画像を認識設定し、カメラがそれを認識するとARの内容が表示される仕組みです。先ほど作成したテキストを表示するWebARをマーカーベース化してみましょう。
<br/>
1. 以下にアクセスし、マーカーベースで認識させるデータを作成します。<br/>
https://jeromeetienne.github.io/AR.js/three.js/examples/marker-training/examples/generator.html

2. 「UPLOAD」ボタンを押し、認識させたい好きな画像をアップロードしてください。<br/>
![image](https://user-images.githubusercontent.com/66664167/114809489-3e1b9a00-9de5-11eb-9541-399055d79b53.png)

3. 「DOWNLOAD MARKER」ボタンを押し、アップロードした画像の.pptファイルをダウンロードしてください。
4. ダウンロードした.pptファイルの名前を<font color="Red">pattern.patt</font>に変更し、【Step1】の⑴でクローンしたパスに直下に配置してください。
5. ar.htmlのマーカーベースを実現するには、a-textタグをa-makerタグで囲みましょう。<br>文字の確度調整が必要なのでrotationを-90に指定します。<BR>文字色（color）や、テキスト（value）、表示位置（pattern）を自由に変更しても良いです。

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
      <a-marker type="pattern" url="pattern.patt">
        <a-text position="0 1 -2"
         rotation="-90 0 0"
         value="my,dogs!!^^"
         color="blue"
         scale="1 1 1"></a-text>
       </a-marker>
    </a-scene>
  </body>
</html>
```
	
5. 以下コマンドを実行し、再デプロイをしてみましょう。<BR>初回以降のデプロイはコマンド一つで簡単に実施出来ます。

```
now
```

6. コマンド実行結果の「Production: https～」から始まる行に、デプロイしたアクセス先が記載されているのでアクセスしてみましょう。<br/>
![image](https://user-images.githubusercontent.com/66664167/114530887-53c67d80-9c86-11eb-8e17-7dd56d6ce218.png)

7. PC上に表示されたQRコードを、スマートフォンのカメラ機能で読み取って、WebARページの表示とARを動かしてみましょう。<BR>【Step3】の手順2.で読み込ませた画像をカメラで合わせてみてください。<br/>
![image](https://user-images.githubusercontent.com/66664167/114810999-35789300-9de8-11eb-8487-d3c4f88e1b9d.png)
<br/><br/>
	
***
# Tips
* a-seene内で使用できるタグは様々あります。動画・音声、画像等、表示したい内容によってタグは違うので注意してください。使用出来るタグは以下公式ページよりご確認ください。<br/>
https://aframe.io/docs/1.2.0/primitives/a-box.html
* Vercel（バーセル）のダッシュボードからもデプロイ結果は確認できます。
```
https://vercel.com/dashboard
```
![image](https://user-images.githubusercontent.com/66664167/114531106-8bcdc080-9c86-11eb-9761-0c1ec3e2b292.png)

* ダッシュボードのNew Projectから、GitHubリポジトリとの連携も可能です。<br/>
![image](https://user-images.githubusercontent.com/66664167/114799076-cabc5d00-9dd1-11eb-9fe9-35f4801188c7.png)
![image](https://user-images.githubusercontent.com/66664167/114799098-d576f200-9dd1-11eb-92d6-1309dc70a01b.png)

* デプロイしたプロジェクトは、プロジェクトのSettings > Advanced > Delete Projectより削除可能です。<br/>
![image](https://user-images.githubusercontent.com/66664167/114799309-50d8a380-9dd2-11eb-8c71-5ad5a5097503.png)
