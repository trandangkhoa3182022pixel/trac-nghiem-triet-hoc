# Trắc nghiệm Triết học 214 câu — Rust + WebAssembly

Ứng dụng web tĩnh. Logic, điều hướng, chấm điểm, lịch sử, lưu câu, mở khóa kết quả đều viết trong `src/lib.rs` (Rust). HTML/CSS dùng cho hiển thị; đoạn JS trong `index.html` chỉ nạp WASM.

## Build (máy tính có Rust + wasm-pack)

```bash
rustup target add wasm32-unknown-unknown
cargo install wasm-pack
wasm-pack build --target web --release --out-dir pkg
```

Dùng web server tĩnh (`python -m http.server 8000`) rồi truy cập `http://localhost:8000/`. Không mở `index.html` bằng `file://` vì module WASM cần HTTP.

## GitHub Pages

Repository → Settings → Pages → Source **GitHub Actions**. Commit toàn bộ mã nguồn trong ZIP. Workflow `.github/workflows/pages.yml` sẽ build Rust và triển khai. Nếu GitHub Pages đang đặt **Deploy from a branch**, phải đổi sang **GitHub Actions**.

## Lưu ý về thanh toán

Đây là ứng dụng tĩnh. QR và mã mở khóa thủ công **không xác thực được giao dịch**. Mã đặt trong WASM không bảo mật; cần backend và webhook ngân hàng/cổng thanh toán nếu muốn xác minh thật.

Bộ 214 câu và đáp án được trích nguyên trạng từ file V4. Chưa biên dịch thử trong môi trường tạo file vì không có Rust toolchain.
