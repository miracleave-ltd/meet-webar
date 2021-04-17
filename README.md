# meet-webar
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**目次**

- [【Step1】WebARを作成しよう](#step1webar%E3%82%92%E4%BD%9C%E6%88%90%E3%81%97%E3%82%88%E3%81%86)
- [【Step2】準備が出来ましたので、Vercel（バーセル）を使ってデプロイをしてみましょう](#step2%E6%BA%96%E5%82%99%E3%81%8C%E5%87%BA%E6%9D%A5%E3%81%BE%E3%81%97%E3%81%9F%E3%81%AE%E3%81%A7vercel%E3%83%90%E3%83%BC%E3%82%BB%E3%83%AB%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%A6%E3%83%87%E3%83%97%E3%83%AD%E3%82%A4%E3%82%92%E3%81%97%E3%81%A6%E3%81%BF%E3%81%BE%E3%81%97%E3%82%87%E3%81%86)
- [【Step3】画像を360°回転させるWebARを作ってみよう](#step3%E7%94%BB%E5%83%8F%E3%82%92360%C2%B0%E5%9B%9E%E8%BB%A2%E3%81%95%E3%81%9B%E3%82%8Bwebar%E3%82%92%E4%BD%9C%E3%81%A3%E3%81%A6%E3%81%BF%E3%82%88%E3%81%86)
- [Tips](#tips)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

***
# 【Step1】WebARを作成しよう
マーカーベースのWebARを作成していきましょう。マーカーベースとはカメラで特定の画像を設定し、カメラがそれを認識するとARの内容が表示される仕組みです。今回のハンズオンでは、好きな画像を設定し、その画像をカメラで認識した時にテキストを表示するコードを作成します。

### ⑴初めに
1. 当ページの上部から当リポジトリをGitでクローン、またはDownloadZipしローカル上の任意フォルダで展開してください。<br/>
![image](https://user-images.githubusercontent.com/66664167/114502898-71381f00-9c67-11eb-80a2-f4cd1eeba2bb.png)
<br/>※展開後のディレクトリ例<br/>
　・クローンした場合：C:\workspace\miracleave\meetup\meet-webar<br/>
　・DownloadZIPした場合：C:\workspace\miracleave\meetup\meet-webar-main<br/>
![image](https://user-images.githubusercontent.com/66664167/115102750-f2552600-9f87-11eb-82c1-1f19312882c8.png)
<br/><br/>

### ⑵WebARの作成
Web上でARを可能とするには、Google社製model-viewerとMozilla社製A-frameがありますが、今回はA-frameを基に作っていきます。<br/>
1. 【Step1】の⑴でクローン、またはDownloadZIPで展開したパスを、WindowsのエクスプローラーまたはMacのFinderで開きます。

2. WebARのコードを記述するために、開いたフォルダ直下に以下のar-marker.htmlをテキストエディタで開いてください。

3. WebARには、テキストや画像そして3Dアニメーションの表示が可能ですが、今回はテキストを表示してみます。開いたar-marker.htmlに以下コードを張り付けましょう。※貼り付け後必ず保存してください。

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
    <script src="https://jeromeetienne.github.io/AR.js/aframe/build/aframe-ar.js"></script>
    <title>meet up vol.15</title>
  </head>
  <body>
    <a-scene embedded arjs="debugUIEnabled:false; sourceType: webcam;">
      <a-marker type="pattern" url="pattern.patt">
        <a-text
           position="0 1 -2"
           rotation="-90 0 0"
           value="meet up!vol.15!"
           color="red"
           scale="1 1 1"
	></a-text>
       </a-marker>
    </a-scene>
  </body>
</html>
```

4. 上記コードは、A-frameとar.jsのライブラリを5-6行目で読み込むことで、body部にARの実現を可能する各タグが使用できます。
今回は以下のタグを使用しています。
* a-scene・・・シーンと呼ばれる部分です。ARを表現するものは全てこのタグ内に記載する必要があります。
* a-text・・・ARでtext文字を表示するタグです。


5. 上記3.の手順貼り付けたコードから、a-textタグ内の以下オプションを変えてみましょう。※変更後は必ず保存してください。
* position ・・・表示するテキストが画面上のどの位置に配置するか指定できます。x y zの形式で指定します。
* rotation ・・・表示するテキストを回転させます。x y zの形式で指定します。
* value    ・・・表示するテキストを指定します。
* color    ・・・表示するテキストの色を指定します。
* scale    ・・・表示するテキストのサイズを指定します。x y zの形式で指定します。

5. 次に、マーカーベースで認識させる画像データを作成しますので、以下にアクセスしてください。<br/>
https://jeromeetienne.github.io/AR.js/three.js/examples/marker-training/examples/generator.html

6. 左上にある「UPLOAD」ボタンを押し、認識させたい好きな画像をアップロードしてください。<br/>
![image](https://user-images.githubusercontent.com/66664167/114809489-3e1b9a00-9de5-11eb-9541-399055d79b53.png)

7. アップロードが出来たら、中央部上にある「DOWNLOAD MARKER」ボタンを押し、アップロードした画像の.pptファイルをダウンロードしてください。

8. ダウンロードした.pptファイルの名前を<font color="Red">pattern.patt</font>に変更し、【Step1】の⑴でクローンしたパスに直下に配置してください。
<br/><br/>

***
# 【Step2】準備が出来ましたので、Vercel（バーセル）を使ってデプロイをしてみましょう
### ⑴そもそも、Vercel（バーセル）とは・・・
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

3. 以下コマンドを実行し、npmでVercel（バーセル）のデプロイを行うコマンド「now」をインストールします。

```
npm i -g now
```

4. 以下コマンドを実行し、CUI上からVercel（バーセル）にログインします。

```
now login
```

5. githubに登録しているメールアドレスにログイン確認が求めるメールが送信されますので、登録しているメールの受信ボックスを確認してください。（以下、受信例）<br/>
![image](https://user-images.githubusercontent.com/66664167/114812872-db79cc80-9deb-11eb-9147-1afc8a165403.png)

6. 登録メールアドレスにログイン確認が求められるので、「VERIFY」を押してください。<br/>
![image](https://user-images.githubusercontent.com/66664167/114528562-17921d80-9c84-11eb-8f71-959fcfc9e6df.png)

7. CUI上でも待機状態から進み、ログインが出来ていることを確認します。
<br/><br/>

### ⑷デプロイの実施
1. 以下コマンドを実行し、デプロイしましょう。カレントディレクトリにあるファイルがデプロイされますので、今いるディレクトリが正しいか注意してください。

```
now
```

2. 初回デプロイのため、いくつかCUI上での確認が必要となりますので、以下の通り入力してください。<r>※2回目以降のデプロイでは求められません。
* 「Sent up and deploy?」（デプロイ元の確認）<BR>　　→　```Y```を入力し、Enterを押下。
* 「Which scope do you want to deploy to?」（デプロイ先の確認）<BR>　　→　Enterを押下。
* 「Link to existing project?」（既存プロジェクトとの連携の確認）<BR>　　→　```N```を入力し、Enterを押下。
* 「What’s your project’s name?」（プロジェクト名の確認）<BR>　　→　Enterを押下。
* 「In which directory is your code located?」（コードのディレクトリ確認）<BR>　　→　Enterを押下。
* 「Want to override the settings?」（設定情報の引き継ぎ）<BR>　　→　```N```を入力しEnterを押してください。

3. 以下、コマンド実行結果の例ですが、コマンド実行結果の「Production: https～」から始まる行に、デプロイしたアクセス先が記載されているのでアクセスしてみましょう。<br/>
![image](https://user-images.githubusercontent.com/66664167/114531193-a2741780-9c86-11eb-9c50-0f0851695952.png)

4. PC上に表示されたQRコードをスマートフォンのカメラ機能で読み取って、WebARページの表示とARを表示させてみましょう。<br/>
<br/><br/>
	
***
# 【Step3】画像を360°回転させるWebARを作ってみよう
Step2ではa-textを使ったテキストの文字表示を行いましたが、A-Frameではa-text以外にも様々なタグが用意されています。次は、画像を360°回転が出来るWebARを作成してみます。
<br/>

1. 【Step1】の⑴でクローン、またはDownloadZIPで展開したパスを、WindowsのエクスプローラーまたはMacのFinderで開きます。

2. 360°回転させたい画像を用意し、PC上にダウンロードしてください。

3. 用意した画像名を<font color="Red">texture.png</font>に変更し、【Step1】の⑴でクローンしたパスに直下に配置してください。

4. 360°回転のWebARのコードを記述するために、開いたフォルダ直下に以下のar-panorama.htmlをテキストエディタで開いてください。

5. 画像を360°回転させるには、a-skyというタグを使用します。開いたar-panorama.htmlに以下コードを張り付けましょう。※貼り付け後必ず保存してください。

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
      <a-assets>
        <img id="sky" src="texture.png" />
      </a-assets>
      <a-sky
        id="ar-panorama"
	radius="10"
	src="#sky"> </a-sky>
    </a-scene>
  </body>
</html>
```


4. 上記コードは、です。上記3.の手順貼り付けたコードから、a-skyタグ内の以下オプションを変えてみましょう。※変更後は必ず保存してください。
* radius ・・・表示するテキストが画面上のどの位置に配置するか指定できます。x y zの形式で指定します。

5. 以下コマンドを実行し、再デプロイをしてみましょう。<BR>初回以降のデプロイはコマンド一つで簡単に実施出来ます。

```
now
```

6. コマンド実行結果の「Preview: https～」から始まる行に、デプロイしたアクセス先が記載されているのでアクセスしてみましょう。<br/>
![image](https://user-images.githubusercontent.com/66664167/114530887-53c67d80-9c86-11eb-8e17-7dd56d6ce218.png)

7. PC上に表示されたQRコードを、スマートフォンのカメラ機能で読み取って、WebARページの表示とARを動かしてみましょう。<BR>【Step3】の手順2.で読み込ませた画像をカメラで合わせてみてください。<br/>
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
***
* ダッシュボードのNew Projectから、GitHubリポジトリとの連携も可能です。<br/>
![image](https://user-images.githubusercontent.com/66664167/114799098-d576f200-9dd1-11eb-92d6-1309dc70a01b.png)
***
* デプロイしたプロジェクトは、プロジェクトのSettings > Advanced > Delete Projectより削除可能です。<br/>
![image](https://user-images.githubusercontent.com/66664167/114799309-50d8a380-9dd2-11eb-8c71-5ad5a5097503.png)
