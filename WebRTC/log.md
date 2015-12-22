# 開發紀錄

## 2015/12/20 PeerConnection
* **iceCandidate要如何取得？**
* **在開始建立PeerConnection時有一個constrain，那個和我們的creatoffer,setLocalDescription有衝突嗎？之間的關係是什麼？**

  * 猜測：從A丟constrain給B，B就知道A需要什麼樣的constrain，然後在獲取mediastream的時候特別利用A的constrain再傳送。所以只是要有兩個sdp就可以完成。但是，還是沒有明白為什麼要在peerconnection創建的時候要給constrain。
* **creatOffer和creatAnswer有什麼用處？**
* google io 特地提到有pc.creatOffer,然後用signaling channel send offer
* 在google io中只是簡單的在obvserver中的onAddStream中讓另一端的顯示出來即可。（利用renderer）
*  1:40 AM 耗了一個晚上，終於可以將WebRTC官方範例燒錄到手機中，具體過程我會紀錄下來。
哎，開發真的好艱辛，資源少又沒人可以問。接下來去認真看範例吧。

## 2015/12/21 
* ice 是 stun和turn的整合技術。在實作的時候會先利用stun，如果失敗，再借用turn來relay。
* ice之所以叫做整合技術，其實ice裡面有stun server和 turn server
* Stun sever是用來找到device所處在的ip和port，然後再用signaling將這個資料給另外一端，這樣就可以做到p2p。
* 一開始利用udp做p2p，如果沒有成功在turn中利用的是tcp。**TURN是否可以用udp?**('url': 'turn:192.158.29.39:3478?transport=udp','url': 'turn:192.158.29.39:3478?transport=tcp'兩個都有是什麼情況？）
* google的共用stun server： stun.l.google.com:19302
* 發現有4個constrain，分別是pcConstrains, videoConstrains, audioConstrains, sdpMediaConstrains. 現在感覺pcConstrains，給pc用，用來限制傳輸的一些限制。videoConstrains,audioConstrains用來做creatTrack的限制，sdpMediaConstrains用來做creatAnswer和creatOffer用。現在主要問題是，sdpConstrain用來給對方，那為什麼還要videoConstrain和audioConstrains，不是直接按照對方的要求給就好嗎？還是說，videoConstrains audioConstrains的意義在於顯示自己的localMediaStream？好混亂。
* NAT Type:
	1. inner ip;port 對應 nat ip;port 並且任何都可以聯通
	2. inner ip;port 對應 nat ip;port 只有發送過資料的outter ip 中的所有port才可以連通
	3. inner ip;portA 對應 nat ip;portA 只有發送過資料的outter 對應ip;port 才可以連通
	4. inner ip;portA 對應 nat ip;portA 與outter ip;portA連接；inner ip;portA 對應nat ip;portB與outter ip;portB連結，相互不能傳送。
* 之所以會出現nat阻擋p2p的問題是：nat會禁止外部不受識別的ip;port直接和內部連結。

## 12/22 開始參考實作
* 突然發現竟然有一個叫做room server的url, 範例程式用的是https://apprtc.appspot.com。這個url有什麼用嘛？不管先用default
* 在call裡面發現有好多的設定呀，而且一個也不懂。有空來研究一下。現在能做出來就好了。
