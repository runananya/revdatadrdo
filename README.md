


# **Reversible Data Hiding (RDH) using Difference Image Histogram Modification**  

🔍 **A Python-based implementation of Reversible Data Hiding (RDH) that enables lossless embedding and extraction of hidden data in grayscale images while ensuring perfect image recovery.**  


## **📌 Features**  
✅ Implements **Difference Image Histogram Modification** for **high-capacity** and **lossless** data embedding.  
✅ Uses **index mapping algorithms** to optimize pixel arrangement, increasing **embedding capacity by 50%**.  
✅ **Histogram shifting & peak bin modification** for minimal distortion (**PSNR > 50 dB**).  
✅ **Pixel Difference Histogram (PDH) analysis** to ensure **undetectability**.  
✅ Supports **custom data embedding** with **reversible extraction**.  

---

## **📂 Project Structure**
```
📦 RDH-Image-Embedding
 ┣ 📂 examples
 ┃ ┣ 📜 sample_image.jpg
 ┣ 📜 rdh_embedding.py
 ┣ 📜 rdh_extraction.py
 ┣ 📜 utils.py
 ┣ 📜 README.md
 ┗ 📜 requirements.txt
```

---

## **🚀 Installation**  
1. Clone the repository  
   ```bash
   git clone https://github.com/yourusername/RDH-Image-Embedding.git
   cd RDH-Image-Embedding
   ```

2. Install dependencies  
   ```bash
   pip install -r requirements.txt
   ```

---

## **📸 Usage**  

### **🔹 Embedding Data into an Image**
Run the script to embed binary data into an image:  
```python
from PIL import Image
import numpy as np
from rdh_embedding import embed_data

# Load grayscale image
image = np.array(Image.open("sample_image.jpg").convert('L'))

# Define binary data to hide
data = "10101001010"

# Embed data
marked_img, delta, index_map, peak_diff, location_map = embed_data(image, data, axis="columns")

# Save output
Image.fromarray(marked_img).save("marked_image.jpg")
print("✅ Data embedded successfully!")
```

---

### **🔹 Extracting Data from an Image**
```python
from rdh_extraction import extract_data

# Extract hidden data
extracted_data, recovered_img = extract_data(marked_img, delta, index_map, peak_diff, location_map, len(data), axis="columns")

# Save recovered image
Image.fromarray(recovered_img).save("recovered_image.jpg")
print("Extracted Data:", extracted_data)

if extracted_data == data:
    print("✅ Success: Data matches the original!")
else:
    print("❌ Mismatch: Extracted data differs from original.")
```

---

## **📊 Performance Analysis**
- **Peak Signal-to-Noise Ratio (PSNR)**: Measures distortion between original and marked images.
- **Pixel Difference Histogram (PDH) Analysis**: Evaluates the detectability of embedded data.  
  ```python
  from utils import pdh_analysis
  pdh_analysis(original_img, marked_img)
  ```

---

## **🔬 Experimental Results**
| Image Type      | Capacity Increase | PSNR (dB) |
|----------------|------------------|-----------|
| Checkerboard   | **+100%**        | 54.14     |
| Textures       | **+50%**         | 51.41     |
| Pattern Images | **+50%**         | 52.77     |
| House Image    | **+30%**         | 51.54     |

---

## **📜 References**
- [Reversible Data Hiding Techniques with High Message Embedding Capacity in Images](https://doi.org/10.1371/journal.pone.0231602)  
- Histogram-based and Difference Expansion Methods  
- Image Steganography & Secure Communication  

---

## **👨‍💻 Author**
👤 **Ananya Tomar**  
📧 ananyatomar2308@gmail.com  
 

---

## **⭐ Contributing**
If you'd like to contribute, **open an issue** or **submit a pull request**. Let's improve **secure reversible data hiding together!**  

---

### **📜 License**
This project is licensed under the **MIT License**.
```

