# Yapay Öğrenme ile Yetenek Avcılığı Sınıflandırması

## Proje Özeti

Scoutlar tarafından maçlarda izlenen futbolcuların maç içi performanslarına ve özelliklerine verilen puanlara dayanarak, oyuncuların potansiyel sınıflarını (**average**, **highlighted**) tahmin etmeye yönelik makine öğrenmesi projesi.

Bu projede, Scoutium veri setinden alınan oyuncu değerlendirme verileri kullanılarak çeşitli sınıflandırma algoritmaları ile modelleme yapılmış, oyuncuların yetenek seviyeleri tahmin edilmiştir.

---

## Veri Seti

- Scoutium’dan maçlarda gözlemlenen futbolcuların özelliklerine göre scoutların verdiği puanlar.
- 9 değişken, 10.730 gözlem.
- Önemli sütunlar:
  - `player_id`: Oyuncu ID'si
  - `position_id`: Oyuncunun maçtaki pozisyonu (1: Kaleci, 2: Stoper, ..., 10: Forvet)
  - `attribute_id`: Değerlendirilen oyuncu özelliğinin ID'si
  - `attribute_value`: Oyuncunun ilgili özelliğine verilen puan
  - `potential_label`: Oyuncunun yetenek sınıfı (average, highlighted, below_average - below_average çıkarıldı)

---

## Kullanılan Teknolojiler

- Python 3
- Pandas, NumPy (Veri işleme)
- Scikit-learn (Modelleme, Ölçeklendirme, Model Değerlendirme)
- LightGBM, XGBoost, CatBoost (Gelişmiş sınıflandırma algoritmaları)
- Matplotlib, Seaborn (Veri görselleştirme)

---

## Proje Adımları

1. **Veri Okuma ve Birleştirme:** İki CSV dosyası (`attributes` ve `potential_labels`) uygun anahtarlarla birleştirildi.
2. **Ön İşleme:** Kaleci pozisyonu (1) ve az sayıda bulunan `below_average` sınıfı çıkarıldı.
3. **Pivot Table Oluşturma:** Her satır bir oyuncuyu temsil edecek şekilde `attribute_id` değerleri sütun olarak pivotlandı.
4. **Eksik Veri ve İstatistiksel Analiz:** Verinin genel durumu, dağılımı ve korelasyonları incelendi.
5. **Feature Extraction:** Ek özellikler üretildi (min, max, sum, mean, median gibi).
6. **Label Encoding:** Kategorik değişkenler sayısallaştırıldı.
7. **Ölçeklendirme:** Tüm sayısal özellikler StandardScaler ile ölçeklendirildi.
8. **Modelleme:** Birden fazla sınıflandırma modeli (Logistic Regression, Random Forest, XGBoost, LightGBM vb.) kullanılarak tahmin modelleri oluşturuldu.
9. **Model Değerlendirme:** 10 katlı çapraz doğrulama ile modeller ROC AUC, F1, precision, recall ve accuracy skorlarına göre karşılaştırıldı.

---

## Kullanım

Projeyi kendi ortamınızda çalıştırmak için:

```bash
git clone https://github.com/kullaniciadi/yetenek-avciligi-siniflandirma.git
cd yetenek-avciligi-siniflandirma
pip install -r requirements.txt
python main.py
