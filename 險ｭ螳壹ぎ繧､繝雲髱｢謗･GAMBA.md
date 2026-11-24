# 競輪養成所 面接GAMBA 設定ガイド（先生用）

作文GAMBAと同じ方法で公開・接続します。

## 1. ファイル
| ファイル | 中身 |
|---|---|
| index.html | アプリ本体 |
| config.js | AIの接続先（作文GAMBAと同じ。gamba-api のURL入り） |
| questions.js | 想定質問22問・本人の語句・模範例・深掘り質問・面接の心得 |
| knowledge.js | 基礎知識9項目・確認クイズ12問・要点カード（2026年11月24日時点） |
| gamba-api_mensetsu_addon.js | gamba-api に貼る追加コード（面接用の採点・ヒント） |

## 2. GitHub Pages に置く
作文GAMBAと同じリポジトリに `keirin-mensetsu` などのフォルダを作り、上の index.html・config.js・questions.js・knowledge.js の4つを入れます。
gamba-api は realizefield.github.io からしか使えないので、ダブルクリックで開いた場合はAI採点が動きません（その場合は「採点用の文章をコピー」になります）。

## 3. gamba-api に追加コードを貼る（くわしい採点にする）
1. Cloudflare で gamba-api の「コードを編集」を開く。
2. gamba-api_mensetsu_addon.js の中身を、`/* ---------------- 入口 ---------------- */` のすぐ上に貼る（作文用の追加コードを貼ってある場合は、その下でよい）。
3. 入口の switch の `case 'ai_chat':` の行の下に、次の1行を足す。
   `case 'mensetsu_grade': case 'mensetsu_hint': return await mensetsu(body, request, env, origin);`
4. 「デプロイ」。
5. アプリの「⚙ 先生用」→「つながるか試す」で「面接用の機能も追加ずみ」と出れば完了。

貼る前でも、アプリはこれまでの ai_chat を使って「簡易採点」で動きます。

## 4. 生徒に伝えること
- Chrome（パソコン・Android）か iPhone の Safari で開く。最初にマイクの許可を求められたら「許可」。
- 📘 基礎知識 → 💡 面接の心得 → 📋 質問一覧（★の多い順）→ 🎯 本番モード の順で。
- 模範例の【　】は自分のことで埋める（タイムの伸び、今の生活、師匠から教わった言葉など）。作り話はしない。
- 結果は画面を閉じると消えるので、印刷・テキスト保存で先生に見せる。
