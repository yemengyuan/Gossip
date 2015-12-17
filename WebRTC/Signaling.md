# WebRTC Signaling // unfinished

### icecandidate 遇到的問題 // unfinished
現在主要問題是要怎麼取出icecandidate？在web端似乎是有一個叫做onicecandidate的handler然後回傳icecandidate的物件，然後再將其丟給bob，然後bob可以加入自己的pcfactory之中（在pcfactory裡確實有addicecandidate)。現在的問題是，就算我不在意如何用signaling channel來丟這些訊息，我也要瞭解要如何取得。可是我現在無法做到。

突然找到，在**PeerConnectionObserver.onIceCandidate**(interface用以構建PeerConnection)之中有handler用以實作傳遞icecandidate。現在又有問題了，是自己會去找icecandidate嗎？

### Offer(constrain) 的定義
關於offer（constrain）就可以很簡單的設定自己的videoconstrain or audioconstrain，然後在addtrack時再設置加入對方給的offer（constrain) videotrack和audiotrack時加入即可。
