# WebRTC Android範例平台移植
從[官方文件](https://webrtc.org/native-code/android/)和之前寫的開發[環境設定](https://github.com/yemengyuan/Gossip/blob/master/WebRTC/Environment%20Setup.md)中用gclient獲取開發資料，裡面有範例程式碼。根據官方說法必須使用Linux，不過我找到可以使用Android Studio開發的方式。這邊簡單介紹。

1. 先獲取官方資料，在**/src/webrtc/example/androidapp**資料夾（路徑憑藉記憶寫，明天確定），這個資料夾就是我們範例程式碼所在了。複製出來進mac／windows（我用的mac，不知道windows會有什麼問題，不過感覺不會差很多）。
2. 打開android studio選擇import project 選擇剛剛複製的androidapp資料夾。等一會兒～～～發現好像可以了。不不，還有兩個library沒有加入。
3. 第一個是libjingle，我在這裡面用的是版本是**10836**，compile沒有問題（9xxx版會有一些class還沒有做出來，可能10836之後的某些也可以,不過我沒有測試）具體import libjingle操作看這篇[環境設定](https://github.com/yemengyuan/Gossip/blob/master/WebRTC/Environment%20Setup.md)。
4. 最後要加入signaling所使用的third party library，在這邊是用的[autobahn](http://autobahn.ws/)。不過不用麻煩的去找library了，在example/androidapp/third_party中就有自帶autobanh.jar。之後就是將這個library import入android project就好。

完成上面四個步驟就可以啦～接下來就好好看看WebRTC到底是怎麼實作的了。哎，真的是好事多磨呀。終於可以安安心心的看範例程式了，過不了多久就要向公司匯報了。

Have fun.
