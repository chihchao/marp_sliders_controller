[中文說明](#中文說明)

# Marp Slides Controller

Remote control your Marp-generated HTML slides using a mobile browser, with synchronized speaker notes.

## Demo
<https://chihchao.github.io/marp_slides_controller/slide_template.html>
- Open the link, press `K` to show the QRCode, and scan it with your phone to access the controller.
- Supports Previous / Next / Restart / Jump to page.

## Quick Start

1. Convert your Marp Markdown to HTML (`marp slide.md -o slide.html`).
2. Insert the following code before `</body></html>` in your output `slide.html`:
   ```html
   <!-- Include necessary dependencies -->
   <script src="https://unpkg.com/mqtt/dist/mqtt.min.js"></script>
   <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
   <!-- Configure controller URL and static Room ID (Optional) -->
   <script>
     // Controller URL: Change this only if you deploy your own controller
     // window.MARP_REMOTE_CONTROLLER = "https://yourname.github.io/controller.html";
     // Static Room ID: Prevent changing rooms on reload
     // window.MARP_REMOTE_ROOM_ID = "DEMOHELLOMARP2025";
   </script>
   <script src="https://chihchao.github.io/marp_slides_controller/marp-remote.js"></script>
   ```
3. Reload the slide, press `K` to pop up the QRCode. Scan it with your phone to open the controller.

## How it works

- **Slide Side** (`marp-remote.js`) connects to a public MQTT Broker (`broker.hivemq.com`). After obtaining a "Room ID":
  - Publishes current page number and speaker notes to `marp/remote/{roomId}/status` (using retain, so the phone gets the latest status upon reconnection).
  - Subscribes to `marp/remote/{roomId}/cmd` to receive `next`, `prev`, `restart`, `jump` commands and change pages accordingly.
- **Controller Side** (`controller.html`) connects to the same room via the `room` parameter in the URL, displaying page numbers and notes while sending control commands.

## Key Files

- `marp-remote.js`: The core remote control script injected into the Marp HTML. Handles MQTT connection, page state synchronization, and QRCode display.
- `controller.html`: The mobile controller UI, accessed by scanning the QRCode generated on the slide.
- `slide_template.html` / `slide_template.md`: Example slides and reference output with the script already injected.

## Common Configurations

- **Custom Controller URL**: If you deploy your own controller, update `window.MARP_REMOTE_CONTROLLER` to your URL.
- **Static Room ID**: Set `window.MARP_REMOTE_ROOM_ID` so that the room remains the same after the slide reloads (useful for multiple people connecting simultaneously).
- **Getting Speaker Notes**:
  - Prioritizes reading Marp-generated presenter notes.
  - If no notes are present, falls back to reading HTML comments within each `<section>`.

## Security and Limitations

- Uses a public MQTT Broker. Do not include sensitive information in commands or notes.
- No built-in authentication. If stricter control is needed, please use your own Broker and controller deployment.

---


<a id="中文說明"></a>
[English Version](#marp-slide-controller)

# Marp Slides Controller

用手機瀏覽器遠端控制 Marp 產出的 HTML 簡報，並同步顯示講者備忘錄。

## Demo
<https://chihchao.github.io/marp_slides_controller/slide_template.html>
- 開啟連結後，按 `K` 顯示 QRCode，用手機掃 QRCode 就會出現控制器。
- 可 上一頁/下一頁/重新開始/跳轉頁面

## 快速開始

1. 把 Marp Markdown 轉成 HTML（`marp slide.md -o slide.html`）。  
2. 在輸出的 `slide.html` 裡，於 `</body></html>` 之前加入下列程式碼：
   ```html
   <!-- 引入必要依賴 -->
   <script src="https://unpkg.com/mqtt/dist/mqtt.min.js"></script>
   <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
   <!-- 設定控制器網址與固定房間 ID（皆為選填） -->
   <script>
     // 控制器頁面 URL：要換部署位置只改這裡
     // window.MARP_REMOTE_CONTROLLER = "https://yourname.github.io/controller.html";
     // 固定房間 ID：避免每次重新載入都換房間
     // window.MARP_REMOTE_ROOM_ID = "DEMOHELLOMARP2025";
   </script>
   <script src="https://chihchao.github.io/marp_slides_controller/marp-remote.js"></script>
   ```
3. 重新載入簡報，按鍵盤 `K` 會彈出 QRCode。用手機掃描即可打開控制器。

## 運作方式

- 簡報端 (`marp-remote.js`) 連上公開的 MQTT Broker (`broker.hivemq.com`)，取得「房間 ID」後：
  - 把目前頁碼與講者備忘錄發送到 `marp/remote/{roomId}/status`（使用 retain，手機重新連也拿得到最新狀態）。
  - 監聽 `marp/remote/{roomId}/cmd`，接受 `next`、`prev`、`restart`、`jump` 指令並換頁。
- 控制器端 (`controller.html`) 透過 URL 參數中的 `room` 連到同一房間，顯示頁碼與備忘錄並送出控制指令。

## 主要檔案

- `marp-remote.js`：插入到 Marp HTML 後的遠端控制核心腳本，負責 MQTT 連線、同步頁面狀態、顯示 QRCode。
- `controller.html`：手機端控制器 UI，掃描簡報產生的 QRCode 後進入。
- `slide_template.html` / `slide_template.md`：範例簡報與已插好腳本的參考輸出。

## 常見設定

- **自訂控制器位置**：若自行部署控制器，把 `window.MARP_REMOTE_CONTROLLER` 改成你的 URL。
- **固定房間 ID**：設定 `window.MARP_REMOTE_ROOM_ID`，讓同一場簡報重新整理仍沿用同一房間（方便多人同時連線）。
- **取得講者備忘錄**：
  - 優先讀取 Marp 產生的 presenter notes。
  - 若沒有 notes，會回退讀取每張投影片 `<section>` 中的 HTML 註解。

## 安全與限制

- 使用公開 MQTT Broker，請勿在指令或備忘錄中放入敏感資訊。
- 未內建身份驗證，若需要更嚴謹的控制，請改用自有 Broker 與控制器部署。
