# GNB Shipping Document Classifier

A machine learning project using **Gaussian Naive Bayes (GNB)** to classify shipping and logistics documents.  
Originally developed during an internship at **Openturf Technologies**, this version is adapted with public-friendly documentation.

---

## 🚀 Features
- Classifies shipping documents by type using Gaussian Naive Bayes.
- Provides a REST API for uploading and classifying documents.
- Outputs:
  - File name  
  - Page count  
  - Document type(s) with percentage breakdown  

---

## 📦 Installation
Clone the repository and install dependencies:

```bash
git clone https://github.com/your-username/gnb-shipping-doc-classifier.git
cd gnb-shipping-doc-classifier
pip install -r requirements.txt
```

Update paths:
- **`docreader.py`** → set your local path for `pytesseract`.  
- **`config.ini`** → set your `UPLOAD_FOLDER` (location of files to upload).  

---

## ▶️ Running the API
Start the REST API server:

```bash
python restapi.py
```

The API will start locally at:  
```
http://127.0.0.1:5000
```

---

## 🛠 Usage (with Postman)
1. Open [Postman](https://www.postman.com/downloads/).
2. Create a **POST request** to:
   ```
   http://127.0.0.1:5000/upload
   ```
3. Under **Body → form-data**:
   - Add a key called `file` (case-sensitive).
   - Set its type to **File** and upload your document.
4. Hit **Send** to receive the classification result.

---

## 📊 Example Output
```json
{
  "filename": "invoice_sample.pdf",
  "pages": 3,
  "types": {
    "Invoice": 87.5,
    "Packing List": 12.5
  }
}
```

---

## 📚 Model Details
- **Classifier**: Gaussian Naive Bayes (`scikit-learn`)
- **Input**: Shipping document text extracted with Tesseract OCR
- **Output**: Predicted document type with confidence score
- 
- [Model Report](./GNB_Classification_Ramya.pdf) – methodology and evaluation results  
- [Admin Guide](./App%20Admin%20Guide.pdf) – deployment and API usage instructions   
---

## ⚠️ Notes
- Only **one file** can be uploaded at a time.  
- The key name in Postman **must** be `file`.  
- Output format can be JSON or HTML.  
