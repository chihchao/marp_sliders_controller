# Marp Slide Controller



## 事前準備

1. 先將 Marp Markdown 簡報轉成 html 檔案。
2. 開啟 html 檔案，在檔案最後的 `</body></html>` 前，插入以下程式：

```
<!-- 引入必要依賴 -->
<script src="https://unpkg.com/mqtt/dist/mqtt.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<!-- 設定控制器網址並載入腳本 -->
<script>
  // 這行可以讓你隨時更換控制器的位置，而不必動到 GitHub 上的腳本
  // window.MARP_REMOTE_CONTROLLER = "https://yourname.github.io/controller.html";
  // 如果想要固定使用某個 ID，不要每次重新載入簡報時都變動，可以在這裡設定
  // window.MARP_REMOTE_ROOM_ID = "DEMOHELLOMARP2025"; // 這裡填入您想要的固定 ID
</script>
<script src="https://chihchao.github.io/marp_sliders_controller/marp-remote.js"></script>
```


