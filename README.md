# Engineering Books Recommendation System (Content-Based)

Bu proje, mühendislik kitaplarına ait bir veri seti üzerinde **veri ön işleme (data preprocessing)**, **keşifsel veri analizi (EDA)** ve **content-based (içerik tabanlı) kitap öneri sistemi** geliştirmeyi amaçlar.

Proje Jupyter Notebook ortamında, uçtan uca bir akış olacak şekilde tasarlanmıştır:
1. Ham verinin temizlenmesi ve analiz edilmesi  
2. Metin ön işleme (text preprocessing)  
3. TF-IDF ve Cosine Similarity kullanarak kitap önerisi yapılması  
4. Öneri sistemleri için farklı değerlendirme metriklerinin uygulanması  

---

## Proje Yapısı

├── Data-Pre-processing.ipynb
├── Recommendation.ipynb
├── Engineering_books_data.csv
├── Cleaned_Engineering_books_data.csv
├── README.md
└── LICENSE


---

## Veri Setleri

### `Engineering_books_data.csv`
Ham mühendislik kitapları veri setidir.  
Kitaplara ait şu alanları içerir:
- Title
- Author
- Description
- Publisher
- Year
- Language
- Pages
- Download link
- Image

Bu veri seti, ön işleme ve analiz adımları için kullanılır.

---

### `Cleaned_Engineering_books_data.csv`
Ön işleme adımlarından sonra elde edilen temizlenmiş veri setidir.  
Bu dosya, öneri sisteminde doğrudan kullanılır.

---

## Notebook Açıklamaları

### 1️⃣ Data-Pre-processing.ipynb

Bu notebook’ta aşağıdaki işlemler gerçekleştirilir:

#### Veri Temizleme
- Eksik (NaN) verilerin kaldırılması
- “Unknown” değerlerinin kontrol edilmesi
- Kitap başlıkları üzerinden tekrar eden kayıtların silinmesi

#### Özellik Çıkarımı
- Başlık uzunluğu (`title length`)
- Açıklama uzunluğu (`desc_length`)
- Öneri için kullanılan birleşik metin alanı (`recommend char`)

#### Metin Ön İşleme
- Noktalama işaretlerinin kaldırılması
- Stopword temizleme
- Lemmatization (WordNetLemmatizer)
- Küçük harfe dönüştürme

#### Görselleştirme
- Başlık ve açıklama uzunlukları için histogram ve boxplot
- WordCloud görselleştirmeleri

Bu adımlar sonucunda `Cleaned_Engineering_books_data.csv` dosyası üretilir.

---

### 2️⃣ Recommendation.ipynb

Bu notebook’ta **content-based kitap öneri sistemi** geliştirilmiştir.

#### Kullanılan Yöntemler
- **TF-IDF Vectorization**
- **Cosine Similarity**

#### Öneri Mekanizması
- Kitap açıklama ve başlıklarından oluşan metinler TF-IDF ile vektörleştirilir
- Cosine similarity matrisi hesaplanır
- Seçilen bir kitap başlığına göre en benzer kitaplar önerilir

#### Değerlendirme Metrikleri
Notebook içinde öneri sistemlerini değerlendirmek için çeşitli metrik fonksiyonları yer alır:

**Rating prediction metrikleri**
- MAE
- RMSE

**Ranking metrikleri**
- nDCG
- ARHR
- RHR

**Classification tabanlı metrikler**
- Precision
- Recall
- F1-score

**Beyond-accuracy metrikleri**
- Coverage
- Diversity
- Novelty
- Serendipity
- Freshness
- CHR

> Bazı metrikler örnek/simülasyon verileriyle gösterilmiştir. Amaç, metriklerin nasıl hesaplandığını ve yorumlandığını göstermektir.

---


## Kurulum

Python 3.9+ önerilir.

```bash
pip install pandas numpy scikit-learn matplotlib seaborn nltk wordcloud
```

NLTK için gerekli paketler:

nltk.download('stopwords')
nltk.download('wordnet')

Önerilen sıra:

-Data-Pre-processing.ipynb
-Recommendation.ipynb

