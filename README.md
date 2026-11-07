# Veri Notları — Medium Makaleleri

Medium’da yazdığım veri analizi, istatistik ve makine öğrenmesi yazılarının kodları.
Her klasörde ilgili makalenin tüm grafiklerini ve rakamlarını baştan üreten, çalıştırılmış bir Jupyter notebook bulunur.

**Yazar:** Uğur Avşar · [Medium](https://medium.com/@uguravsar10) · [LinkedIn](https://www.linkedin.com/in/uguravsarr)

---

## Makaleler

| # | Makale | Konular | Kod |
|---|--------|---------|-----|
| 01 | [Ortalama Yalan Söyler: Grafiğe Bakmadan Karar Vermeyin](https://medium.com/@uguravsar10/ortalama-yalan-s%C3%B6yler-grafi%C4%9Fe-bakmadan-karar-vermeyin-84ab115d802a) | Tanımlayıcı istatistik · EDA · Veri görselleştirme · Veri kalitesi | [`01_ortalama_yalan_soyler`](01_ortalama_yalan_soyler/) |
| 02 | [Accuracy %99,9, Peki Model İşe Yarıyor mu? Dengesiz Veride Doğru Metrik Seçimi](https://medium.com/@uguravsar10/accuracy-99-9-peki-model-i%CC%87%C5%9Fe-yar%C4%B1yor-mu-dengesiz-veride-do%C4%9Fru-metrik-se%C3%A7imi-1583749e6dc8) | Dengesiz veri · Precision/Recall · ROC vs PR · Karar eşiği | [`02_accuracy_yaniltir`](02_accuracy_yaniltir/) |

---

## 01 · Ortalama Yalan Söyler

![Kapak](01_ortalama_yalan_soyler/gorseller/00_kapak.png)

📖 **[Makaleyi Medium’da oku](https://medium.com/@uguravsar10/ortalama-yalan-s%C3%B6yler-grafi%C4%9Fe-bakmadan-karar-vermeyin-84ab115d802a)**

Tek bir özet istatistiğin (ortalama, korelasyon) neden yanıltıcı olabileceğini üç örnekle gösterir:

1. **Taksi ücretleri:** Sağa çarpık dağılımda ortalama (13,09 $) ile medyan (9,50 $) arasındaki fark; yolculukların %70’inde ücret ortalamanın altında.
2. **Anscombe Dörtlüsü:** Özet istatistikleri aynı, grafikleri bambaşka dört veri seti.
3. **Bahşişler:** Yolculukların %36’sında bahşiş sıfır görünüyor; ödeme yöntemine göre ayırınca bunun nakit bahşişlerin kayda girmemesinden kaynaklandığı ortaya çıkıyor.

**Veri**
- NYC Taxi & Limousine Commission (TLC) kayıtlarından alınmış, Mart 2019’a ait 6.433 taksi yolculuğu — [seaborn `taxis` örnek veri seti](https://github.com/mwaskom/seaborn-data)
- Anscombe, F. J. (1973). *Graphs in Statistical Analysis.* The American Statistician, 27(1), 17–21.

---

## 02 · Accuracy %99,9, Peki Model İşe Yarıyor mu?

![Kapak](02_accuracy_yaniltir/gorseller/00_kapak.png)

📖 **[Makaleyi Medium’da oku](https://medium.com/@uguravsar10/accuracy-99-9-peki-model-i%CC%87%C5%9Fe-yar%C4%B1yor-mu-dengesiz-veride-do%C4%9Fru-metrik-se%C3%A7imi-1583749e6dc8)**

Dengesiz veride accuracy’nin neden yanıltıcı olabileceğini ve bir sınıflandırma modelini hangi ölçütlerle değerlendirebileceğimizi gösterir:

1. **Tembel model:** Her işleme “normal” diyen model test setinde %99,87 doğruluk alıyor, ama hiçbir dolandırıcılığı yakalamıyor.
2. **Üç model karşılaştırması:** Lojistik regresyon dolandırıcılıkların %49’unu, dengeli (class_weight="balanced") model %88’ini yakalıyor; accuracy ise üçünde birbirine çok yakın.
3. **ROC vs Precision–Recall:** Aynı model için ROC-AUC 0,97, average precision 0,71.
4. **Karar eşiği:** Eşik, eğitim verisinde zaman sıralı çapraz doğrulamayla maliyete göre seçildiğinde, varsayımlarla test setindeki toplam maliyet yaklaşık %60 azalıyor.

**Veri**
- Kredi kartı dolandırıcılığı veri seti — Eylül 2013, Avrupalı kart sahiplerinin iki günlük 284.807 işlemi (492 dolandırıcılık). ULB Machine Learning Group & Worldline; Kaggle’da “Credit Card Fraud Detection”. Notebook, verinin herkese açık bir GitHub kopyasını kullanır (~100 MB).
- Dal Pozzolo, A., Caelen, O., Johnson, R. A. & Bontempi, G. (2015). *Calibrating Probability with Undersampling for Unbalanced Classification.* IEEE SSCI, 159–166.

---

## Çalıştırma

```bash
git clone https://github.com/Uguravsar75/medium-makaleler.git
cd medium-makaleler
pip install -r requirements.txt
jupyter notebook   # klasörlerden istediğiniz notebook’u açın
```

Veriler notebook’ların içinde doğrudan internetten okunur; ayrıca indirme gerekmez.
