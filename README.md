電話番号からContactManagerのグループ名を取得するAGIスクリプトです。<br/>
Dynamic Routesモジュールと組み合わせることで、特定グループの着信を自由にルーティングすることができます。<br/>
例えば、迷惑電話を掛けてくるグループを一括で拒否したり、FAX専用ダイヤルの着信をFAX受信先に送ったり、<br/>
相手が分かっている着信を最初から特定部署のキューに回したりといった使い方が出来ます。<br/>
直接SQLを実行しているため、DB構造が変わった場合は使えないと思います。<br/>

こちらのコードを書くにあたって、下記のお二方のコードを多大に参考にさせていただきました。
この場を借りて感謝申し上げます。

sorvani様
https://github.com/sorvani/freepbx-helper-scripts/blob/master/Aastra_Button_Functions/show_ring_group_membership.php

lgaetz様
https://gist.github.com/lgaetz/7cab1bc6b6266ba658d5dd90d2e919eb
https://community.freepbx.org/t/using-dynamic-routes-with-an-agi-file/77968
