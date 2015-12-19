# 開發紀錄

## PeerConnection
* **iceCandidate要如何取得？**
* **在開始建立PeerConnection時有一個constrain，那個和我們的creatoffer,setLocalDescription有衝突嗎？之間的關係是什麼？**

  * 猜測：從A丟constrain給B，B就知道A需要什麼樣的constrain，然後在獲取mediastream的時候特別利用A的constrain再傳送。所以只是要有兩個sdp就可以完成。但是，還是沒有明白為什麼要在peerconnection創建的時候要給constrain。
* **creatOffer和creatAnswer有什麼用處？**
* google io 特地提到有pc.creatOffer,然後用signaling channel send offer
* 在google io中只是簡單的在obvserver中的onAddStream中讓另一端的顯示出來即可。（利用renderer）
* 2015/12/20 1:40 AM 耗了一個晚上，終於可以將WebRTC官方範例燒錄到手機中，具體過程我會紀錄下來。
哎，開發真的好艱辛，資源少又沒人可以問。接下來去認真看範例吧。
