# 🤖 ROBO-ADVISOR 

**Bitget Stock Token Analyzer**

Bot này dùng để:

* Phân tích các **stock token trên Bitget**
* Áp dụng các chỉ báo kỹ thuật: RSI, Bollinger Bands, MACD, ATR
* Đưa ra tín hiệu: **BUY / SELL / HOLD**
* Gửi thông báo qua **Telegram**

---

## 📦 1. Yêu cầu hệ thống

* Python >= 3.8
* Internet ổn định
* Tài khoản Telegram

---

## ⚙️ 2. Cài đặt

Mở terminal / CMD:

```bash
pip install requests
```

---

## 🔑 3. Cấu hình Telegram

### Bước 1: Tạo bot Telegram

* Nhắn tin cho **@BotFather**
* Gõ: `/start`
* Gõ: `/newbot`
* Đặt tên bot → nhận **TOKEN**

### Bước 2: Lấy Chat ID

* Nhắn tin cho bot của bạn
* Truy cập link:

```
https://api.telegram.org/bot<YOUR_TOKEN>/getUpdates
```

* Copy `chat.id`

---

### Bước 3: Cập nhật code

Thay vào đây:

```python
TELEGRAM_BOT_TOKEN = "YOUR_BOT_TOKEN"
TELEGRAM_CHAT_ID   = "YOUR_CHAT_ID"
```

⚠️ Lỗi bạn đang gặp:

```
TELEGRAM_BOT_TOKEN =
```

→ là do chưa gán giá trị → Python báo lỗi syntax

---

## ▶️ 4. Chạy bot

```bash
python bot.py
```

Nếu chạy thành công:

```
BOT STARTED...
```

Bot sẽ:

* Scan danh sách cổ phiếu mỗi 5 phút
* Gửi tín hiệu khi có setup

---

## 📊 5. Logic hoạt động

Bot phân tích theo:

### 🔹 RSI

* < 30 → Oversold → BUY
* > 70 → Overbought → SELL

### 🔹 Bollinger Bands

* Chạm band dưới → BUY
* Chạm band trên → SELL

### 🔹 MACD

* MACD > Signal → BUY
* MACD < Signal → SELL

### 🔹 Tổng hợp tín hiệu

* BUY > SELL → 🔥 BUY
* SELL > BUY → 🧊 SELL
* Cân bằng → ⚖️ HOLD

---

## 💰 6. PnL logic

```python
pnl = price - vcp
pnlp = (pnl / vcp) * 100
```

→ So sánh giá hiện tại với **VCP (giá tham chiếu bạn tự đặt)**

---

## ⚠️ 7. Lưu ý quan trọng (RẤT QUAN TRỌNG)

Bot này:

* ❌ KHÔNG phải financial advice
* ❌ KHÔNG quản lý rủi ro
* ❌ KHÔNG tính liquidation

👉 Bạn cần:

* Giới hạn đòn bẩy (≤ 5x cho người mới)
* Luôn đặt stop-loss
* Không all-in

---

## 🚀 8. Tùy chỉnh nâng cao

Bạn có thể:

* Thêm coin vào `WHITELIST`
* Thay timeframe:

```python
INTERVAL = "1H" → "15m" hoặc "4H"
```

* Tăng tốc scan:

```python
POLL_SECONDS = 300 → 60
```

## 📌 9. Gợi ý cải tiến (Pro level)

* Thêm **risk management**
* Thêm **position sizing**
* Thêm **backtest**
* Thêm **filter volume**
* Thêm **trend filter (EMA200)**


Chỉ cần nói: *“upgrade bot”* là mình build cho bạn bản xịn hơn 👍
