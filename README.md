電話番号からFreePBXのContactManagerグループ名を取得するAGIスクリプトです。<br/>
Dynamic Routesと組み合わせることで、特定グループの着信を自由にルーティングすることができます。<br/>
例えば、迷惑電話を掛けてくるグループを一括で拒否したり、FAX専用ダイヤルの着信をFAX受信先に送ったり、<br/>
相手が分かっている着信を最初から特定部署のキューに回したりといった使い方が出来ます。<br/>
<br/>
直接SQLを実行しているため、ContactManagerのDB構造が変わった場合は使えないと思います。<br/>
ContactManagerのAPIを使用したかったのですが、GroupNameを取得する方法が見つかりませんでした。<br/>
インストールはagi-binディレクトリにコピーし、パーミッションを設定するだけです。<br/>
/var/lib/asterisk/agi-binなどですが、各環境に合わせて配置してください。<br/>

使い方の一例として、まず下記画像のようにFreePBXのコンタクトマネージャー、Externalにテストというグループを作成し番号を登録します。

![cm](https://github.com/accept/getGroupByNumber-FreePBX/assets/421679/46d7b7b3-ce22-48e7-9819-e8b6db09cf9c)
<br/>
<br/>

次に、Dynamic Routesを下記画像のように構成します。<br/>
AGI Lookupはggbn.agiまでのパスと引数です。<br/>
引数は番号からグループ名を取得するため[NUMBER]となっています。<br/>
AGI Result Variableはggbn.agiに記述されている結果を格納する変数名です。<br/>
スクリプトをそのまま使用する場合はgnとなります。

![後内](https://github.com/accept/getGroupByNumber-FreePBX/assets/421679/9329fc1b-ae88-44f9-8257-aa7ba6102549)

Matchにグループ名を記述することで、そのグループからの着信をルーティングできます。<br/>
参考画像では作成したグループ、テストに登録された番号からの着信はすべてTerminate Callに飛ばされるようになります。<br/>

こちらのコードを書くにあたって、下記のお二方のコードを多大に参考にさせていただきました。<br/>
この場を借りて感謝申し上げます。

sorvani様
https://github.com/sorvani/freepbx-helper-scripts/blob/master/Aastra_Button_Functions/show_ring_group_membership.php

lgaetz様
https://gist.github.com/lgaetz/7cab1bc6b6266ba658d5dd90d2e919eb
https://community.freepbx.org/t/using-dynamic-routes-with-an-agi-file/77968
