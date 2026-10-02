ハワイ島ツアー2027 LP / Netlify 公開手順
====================================================
公開URL（目標）: https://tour.wds.world/hawaii202702

■ フォルダ構成（この site フォルダの中身をそのまま公開します）
  hawaii202702/index.html        ... サイト本体（スマホ / PC 自動切替）
  hawaii202702/assets/           ... PC用パーツ画像（768px以上で表示）
  hawaii202702/assets-mobile/    ... モバイル用パーツ画像（767px以下で表示）
  netlify.toml                   ... キャッシュ設定
  _redirects                     ... ルートアクセスをツアーページへ転送

  ※「hawaii202702」というフォルダ名が、そのままURLの末尾になります。
    次のツアーを追加するときは、隣に hawaii202803/ のように
    フォルダを増やすだけでURLが増えます。

■ 表示の出し分け
  画面幅 767px以下 ... モバイル版デザイン
  画面幅 768px以上 ... PC版デザイン（950px幅。950px未満の画面では自動で縮小表示）


====================================================
STEP 1. Netlifyにアップロードする
====================================================
  1. https://app.netlify.com/drop を開く
  2. この「site」フォルダを、ブラウザの画面にドラッグ＆ドロップ
  3. 数十秒で仮URLが発行されます（例: https://sunny-taffy-1a2b3c.netlify.app）
  4. この時点で https://（仮URL）/hawaii202702 が見られます

  ※更新するときは、サイトの「Deploys」タブを開いて
    修正した site フォルダをまた同じようにドラッグ＆ドロップするだけです。


====================================================
STEP 2. 独自ドメイン tour.wds.world をつなぐ
====================================================
  ● Netlify側の操作
  1. 作成したサイトの「Site configuration」→「Domain management」を開く
  2. 「Add a domain」をクリック
  3. tour.wds.world と入力して「Verify」→「Add domain」
  4. 画面に「Set up DNS」などの案内と、つなぎ先のホスト名
     （例: sunny-taffy-1a2b3c.netlify.app）が表示されます。
     このホスト名をメモしてください。

  ● wds.world のDNS管理画面での操作
     （お名前.com / Cloudflare / Route53 など、
      wds.world を管理している会社の管理画面で行います）

  5. DNSレコードを1件追加します。

       タイプ  : CNAME
       ホスト名 : tour            （※ tour.wds.world と入力する画面もあります）
       値      : sunny-taffy-1a2b3c.netlify.app   ← STEP2-4でメモしたもの
       TTL     : 3600（または自動/デフォルト）

     ※「値」の末尾にドットが必要な管理画面もあります（例: 〜.netlify.app.）
     ※ wds.world 本体（ルートドメイン）のレコードは触らないでください。
       tour というサブドメインを1つ足すだけなので、
       既存のサイトやメールには影響しません。

  6. 保存後、反映に数分〜最大48時間かかります（通常は10〜30分）。
     Netlifyの Domain management 画面が「Netlify DNS」や
     チェックマーク表示になれば完了です。

  7. 同じ画面の「HTTPS」欄で証明書が自動発行されます
     （"Verify DNS configuration" → "Provision certificate"）。
     完了すると https:// でアクセスできるようになります。

  → https://tour.wds.world/hawaii202702 で公開完了です。


====================================================
補足
====================================================
■ 申し込みボタンのリンク先
  https://forms.gle/5wx1i4nUj1m9krQP7
  （変更する場合は hawaii202702/index.html 内のこのURLを2か所置き換え）

■ お問い合わせメール
  usher55taka@gmail.com
  （PC版はテキストリンク、モバイル版は画像上の透明リンク）

■ 画像の重さについて
  PC用 約6MB / モバイル用 約4MB です。
  表示されない側は読み込まない作りですが、
  さらに速くしたい場合はWebP化で2〜3割まで圧縮できます。
