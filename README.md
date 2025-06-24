**🧠📸Xây dựng mô hình sử dụng Mạng nơ ron để tạo chú thích cho hình ảnh.**
Đây là một dự án học máy sử dụng trí tuệ nhân tạo để **tự động tạo chú thích (caption)** cho ảnh. Mô hình kết hợp giữa **thị giác máy tính (Computer Vision)** và **xử lý ngôn ngữ tự nhiên (NLP)** nhằm hiểu nội dung ảnh và mô tả bằng câu văn tiếng Anh.

---
## 🧰 Công nghệ và mô hình sử dụng
- **InceptionV3**: mô hình CNN đã huấn luyện trước, dùng để trích xuất đặc trưng ảnh.
- **LSTM (Long Short-Term Memory)**: để sinh văn bản (caption) từ vector đặc trưng ảnh.
- **Word Embedding**: sử dụng GloVe (Global Vectors) để ánh xạ từ sang vector.
- **Transfer Learning**: tái sử dụng mô hình đã học từ ImageNet.
- **Gradio**: giao diện người dùng cho phép tải ảnh và hiển thị caption.
---
## 🗃️ Bộ dữ liệu
- **Flickr8K** (8.091 ảnh) và **Flickr30K** (31.783 ảnh).
- Link data: https://www.kaggle.com/datasets/phamhuynhbaophuong/flick8k-flick30k
- Mỗi ảnh đi kèm với nhiều câu mô tả (captions) mô tả hoạt động đời sống thường ngày.
- Dữ liệu được chia thành:  
  - Train: ~31.000 ảnh  
  - Test: ~7.000 ảnh
---
## ⚙️ Pipeline hệ thống
1. **Tiền xử lý ảnh**: Resize, chuẩn hóa ảnh cho phù hợp với InceptionV3.
2. **Trích xuất đặc trưng**: Dùng InceptionV3 để mã hóa ảnh thành vector 2048 chiều.
3. **Tiền xử lý caption**: Loại bỏ ký tự không cần thiết, chuẩn hóa, thêm token `startseq` và `endseq`.
4. **Tạo tập từ vựng**: Lọc từ xuất hiện > 10 lần, ánh xạ `word <-> index`.
5. **Tạo embedding matrix** từ GloVe.
6. **Huấn luyện mô hình**: Kết hợp ảnh + chuỗi để dự đoán từ tiếp theo.
7. **Đánh giá mô hình**: Dùng BLEU score.
8. **Tạo giao diện người dùng** bằng Gradio.
---
## 📈 Kết quả
- **BLEU-1**: ~44.26% – mô hình chọn được từ phù hợp.
- **BLEU-2**: ~25.4% – khả năng tạo cụm từ chưa tối ưu.
- Có thể cải thiện thêm bằng cách:
  - Tăng dữ liệu huấn luyện.
  - Dùng thêm chỉ số đánh giá khác như METEOR, ROUGE, TER.
  - Mở rộng sang nhận diện ảnh real-time.
---
## 🌍 Ứng dụng thực tế
- Hỗ trợ người khiếm thị.
- Tìm kiếm hình ảnh thông minh.
- Mô tả nội dung ảnh tự động cho mạng xã hội hoặc thương mại điện tử.
---
