# 🏛️ VieLaw: Vietnamese Legal Dataset

![Status](https://img.shields.io/badge/Status-Protected-orange)
![Format](https://img.shields.io/badge/Format-JSON-blue)
![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-green)

> **⚠️ DISCLAIMER / LƯU Ý**
>
> **Dataset is provided as-is for reference purposes. Ensure proper text encoding/processing when using programmatically.**
>
> *(Dữ liệu được cung cấp nguyên trạng để tham khảo. Vui lòng đảm bảo xử lý mã hóa văn bản phù hợp khi sử dụng bằng code).*

---

## 🛠️ Data Access Guide (Hướng dẫn xử lý dữ liệu)

Để bảo đảm tính toàn vẹn dữ liệu, việc đọc trực tiếp bằng `json.load()` thông thường sẽ gây lỗi.

**Yêu cầu:** Bạn cần loại bỏ ký tự **Zero Width Space (`\u200b`)** trước khi phân tích cú pháp.

### ✅ Python Snippet
Sử dụng hàm dưới đây để tải dữ liệu chính xác:

```python
import json

def load_vielaw_data(file_path):
    """
    Load VieLaw dataset handling the hidden protection character.
    """
    try:
        with open(file_path, 'r', encoding='utf-8') as f:
            content = f.read()
            
            # Remove hidden Zero Width Space (\u200b) if present
            if content.startswith('\u200b'):
                content = content[1:]
                
            return json.loads(content)
            
    except Exception as e:
        pass

# Usage
data = load_vielaw_data('path/to/hinhsu_task1.json')
'''
###📂 Dataset Structure (Cấu trúc dữ liệu)

###📜 Citation (Trích dẫn)
Nếu sử dụng bộ dữ liệu này cho nghiên cứu, vui lòng trích dẫn:

###⚖️ License
