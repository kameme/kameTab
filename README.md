# kameTab
チャットのtabキー候補、コンフィグでどのコマンドにも設定できる

Bukkitのパケットに割り込んでTabComplete機能の独自追加、パケットが送られてくるのがトリガだから、デフォルトのコマンドや、プラグイン側が対応してるものにも割り込める。

設定とかはWiki見て設定するといいかな、それか、config.txtに例のせてる

ソースは頑張ったから直接は見せないかなー、中身欲しい人はデコンパイルするなりどうぞ。
個人で利用する分ならいいけど、配布するとかはしないでほしいかな。


<h5>使い方</h5>

とても簡単、チャットTab補完が使えるようになるだけMOD鯖でも動くよ コマンド以外も多分補完可能

---
- 座標取得<br>
 チャット中にTabを押すことで現在立っている場所の座標に変換される
 
 - 例:@eからスペースを開けずにTab
   + /tp name @
    + /tp name 100 56 23
    
---
- @セレクタ変換<br>
 @pや@a.@eなどのセレクタを現在の座標をつけて変換する
 
 - 例:@eからスペースを開けずにTab
   + /testfor @e 
    + /testfor @e[x=100,y=88,z=23,r=26]
    
---
- アイテムスポイト機能<br>
 手に持ったアイテム、目線の先のブロックのIDを取得できる。

 チャット中に「@i」「@b」をつけてTabキーを押すと___minecraft:id___と___BukkitID___に変換できる
 
 - @i:手に持っているアイテム
 - @b:目線先にあるブロック
 
 
 - 例:@iからスペースを開けずにTab(手に金床を持っていた場合
   + /give @i 
    + /give minecraft:anvil

<h5>config設定</h5>

configにTab補完機能を追加したいコマンドを設定することができる。

<h4>‣例1</h4>
Citizensの/npcコマンドにcreate|remove|select|spawn|respawnを追加したい場合

```yaml
Commands:
  /npc:
    create: ""
    remove: ""
    select: ""
    despawn: ""
    respawn: ""
Groups: ""
```


<h4>‣例2</h4>
Scriptblock/sbコマンドにTab補完を追加したい場合（まとめる系


```yaml
Commands:
  /sbinteract:
    ">sb1":
      ">sb2": ""
  /sbwalk:
    ">sb1":
      ">sb2": ""
Groups:
  ">sb1":
  - create
  - add
  - remove
  - view
  
  ">sb2":
  - "@bypass"
  - "@command"
  - "@player"
  - "@say"
  - "$item:"
  - "$cost:"
```

<h5>permission設定</h5>
| permission | 説明 | 
| ----- | ----- |
|kametab.tab|Tab補完の権限(補完するなら必ず)|
|kametab.custom.(コマンド名)|指定したコマンドのカスタムTab補完の権限|
|kametab.tab.loc|@での座標補完の権限|
|kametab.tab.block|目線先のブロック取得の権限|
|kametab.tab.item|手に持ってるアイテム取得の権限|
|kametab.tab.select|@セレクター補完の権限|
|kametab.tab.tag|NBTタグ取得の権限|
|kametab.tab.text|テキストの補完の権限|
