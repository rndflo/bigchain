# bigchain



## Steps

~~~
==> mkdir bigchain
~~~



~~~
==> cd bigchain
~~~

~~~
==> touch bigGenesis.json
~~~


Instantiate data directory

~~~
==> geth --datadir ./bigDataDir init ./bigGenesis.json
~~~

Start Ethereum small node

~~~
==> geth --datadir ./bigDataDir --networkid 1114 console 2>> bigEth.log
~~~

In another terminal 

~~~
==> tail -f bigEth.log
~~~


In the geth Javascript console 
personal.newAccount("apple123")


Add another peer

~~~
==> geth --datadir ./smallDataDir init ./bigGenesis.json
~~~


Launch the 2nd small on a different port 

~~~
==> geth --datadir ./smallDataDir --networkid 1114 --port 30304 console 2>> smallEth.log
~~~

~~~
==> tail -f smallEth.log 
~~~

In the 1st console

~~~
> admin.nodeInfo.enode
"enode://ae96f0115ebb17cbdb4494f04382233357c95a9fa5d293b75c2d24909f23dad5f9da03993deaed699cd9e69114e9a29fcf8a8a5c8fa49fb55085b91419b8e8b8@192.168.2.14:30303"
~~~

In the 2nd console

~~~
> admin.addPeer("enode://ae96f0115ebb17cbdb4494f04382233357c95a9fa5d293b75c2d24909f23dad5f9da03993deaed699cd9e69114e9a29fcf8a8a5c8fa49fb55085b91419b8e8b8@192.168.2.14:30303")
true
~~~

