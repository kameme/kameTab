# kameTab
チャットのtabキー候補、コンフィグでどのコマンドにも設定できる

Bukkitのパケットに割り込んでTabComplete機能の独自追加、パケットが送られてくるのがトリガだから、デフォルトのコマンドや、プラグイン側が対応してるものにも割り込める。

設定とかはWiki見て設定するといいかな、それか、config.txtに例のせてる

ソースは頑張ったから直接は見せないかなー、中身欲しい人はデコンパイルするなりどうぞ。
個人で利用する分ならいいけど、配布するとかはしないでほしいかな。


<h5>使い方</5>

とても簡単、チャットTab補完が使えるようになるだけMOD鯖でも動くよ


<h5>config設定</5>

configにTab補完機能を追加したいコマンドを設定することができる。

<h4>‣例1：</4>Citizensの/npcコマンドにcreate|remove|select|spawn|respawnを追加したい場合

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


<h4>‣例1：</4>Scriptblock/sbコマンドにTab補完を追加したい場合（まとめる系


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


