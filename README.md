# Aygaz_veribilimi
# Online Sales Dataset Analizi

Bu proje, çevrimiçi satış işlemlerini analiz ederek, indirimlerin, kargo sağlayıcılarının ve satış trendlerinin satış performansı üzerindeki etkilerini anlamayı amaçlamaktadır. Veri seti, müşteri satın alma davranışları, sipariş yönetimi ve satış trendlerini incelemek için kullanılmıştır. Ayrıca, satış tahminleri yapmak amacıyla makine öğrenimi modeli de uygulanmıştır.

## Proje Amacı
Bu proje ile aşağıdaki sorulara yanıtlar aranmaktadır:
- İndirim oranlarının satışlar üzerindeki etkisi nedir?
- Kargo sağlayıcılarının performansı nasıl ölçülür ve iade oranları nasıl etkilenir?
- Satış trendlerinde sezonluk değişiklikler nelerdir?
- Toplam satışları tahmin edebilecek bir makine öğrenimi modeli nasıl oluşturulabilir?

## Kullanılan Kütüphaneler
Bu projede veri analizi ve makine öğrenimi süreçlerinde kullanılan ana Python kütüphaneleri:
- **pandas**: Veri işleme ve manipülasyon için.
- **numpy**: Matematiksel işlemler için.
- **matplotlib** ve **seaborn**: Veri görselleştirme için.
- **scikit-learn**: Makine öğrenimi algoritmaları ve metrikler için.
- **xgboost**: Alternatif modelleme algoritması olarak kullanılabilir (isteğe bağlı).

## Veri Seti
Bu projede, Kaggle'dan alınan "Online Sales Dataset" adlı veri seti kullanılmıştır. Veri seti, çevrimiçi satışları ve müşteri davranışlarını analiz etmek için çeşitli özellikler içermektedir. Öne çıkan bazı sütunlar:
- `InvoiceDate`: Satışın yapıldığı tarih.
- `Quantity`: Satın alınan ürün miktarı.
- `UnitPrice`: Ürün başına fiyat.
- `Discount`: Uygulanan indirim oranı.
- `ShippingCost`: Kargo maliyeti.
- `CustomerID`: Müşteri kimlik bilgisi.
- `ReturnStatus`: İade durumu.
- `ShipmentProvider`: Kargo sağlayıcısı.

## Yapılan Çalışmalar

### 1. **Keşifsel Veri Analizi (EDA)**
- **Satış Trendlerini İnceleme**: Satışların zamanla nasıl değiştiğini incelemek için `InvoiceDate` sütunu kullanılarak zaman bazlı satış analizi yapılmıştır. Aylık satış trendleri görselleştirilmiştir.
- **İndirimlerin Satışlara Etkisi**: İndirimlerin satış miktarları üzerindeki etkisi görselleştirilerek analiz edilmiştir. İndirimli ve indirimsiz satışlar karşılaştırılmıştır.
- **Ürün Kategorilerine Göre Satışlar**: Farklı ürün kategorilerinin toplam satışlar üzerindeki etkisi değerlendirilmiştir.
- **Kargo Sağlayıcılarının Performansı**: Kargo sağlayıcılarının iade oranlarına göre performansları incelenmiştir. Hangi sağlayıcıların daha yüksek iade oranlarına sahip olduğu belirlenmiştir.

### 2. **Veri Temizleme ve Ön İşleme**
- **Eksik Veri İşleme**: `CustomerID`, `ShippingCost` ve `WarehouseLocation` gibi sütunlarda eksik veriler tespit edilip uygun şekilde doldurulmuştur (örneğin, "Unknown" etiketi ile).
- **Negatif Değerler**: `Quantity` ve `UnitPrice` gibi sütunlarda negatif değerler kontrol edilip görselleştirilmiştir.
- **Yeni Özelliklerin Oluşturulması**: `TotalSales` (Toplam Satış) gibi yeni özellikler türetilmiştir. `TotalSales`, `Quantity * UnitPrice * (1 - Discount)` şeklinde hesaplanmıştır.

### 3. **Makine Öğrenimi Modeli - Satış Tahminleri**
- **Model Seçimi**:Satışları tahmin etmek için Random Forest Regressor modeli kullanılmıştır.
- **Eğitim ve Test Verilerine Bölme**: Veri seti, eğitim (%80) ve test (%20) verilerine bölünerek modelin genel başarımı değerlendirilmiştir.
- **Model Değerlendirmesi: **:Modelin başarımı Mean Squared Error (MSE) kullanılarak değerlendirilmiştir.

### 4. Sonuçlar ve Öneriler

#### İndirimlerin Satışlara Etkisi
İndirimlerin satış miktarlarını artırdığı ancak kar marjını düşürdüğü gözlemlenmiştir. Bu durum, fiyatlandırma stratejilerinin optimize edilmesi gerektiğini göstermektedir.

#### Kargo Sağlayıcılarının Performansı
İade oranları yüksek olan kargo sağlayıcıları ile ilgili iyileştirmeler önerilmiştir. Bu sağlayıcılar için süreç analizi yapılmalı ve müşteri memnuniyetini artırmak için gerekli iyileştirmeler yapılmalıdır.

#### Satış Tahminleri
`Random Forest` modeli ile `TotalSales` tahmin edilmiştir. Modelin başarımı **MSE = 362,695.19** olarak hesaplanmıştır. Bu hata oranı, modelin iyileştirilmesi gerektiğini ve daha doğru tahminler için ek çalışmalar yapılması gerektiğini göstermektedir.

### Öneriler:
1. **Fiyatlandırma Stratejileri**: İndirim oranlarının optimize edilmesi ve kar marjı üzerinde daha fazla kontrol sağlanması gerekmektedir. Bu sayede, satışlar artarken kar marjı korunabilir.
  
2. **Kargo Sağlayıcıları İyileştirmesi**: Yüksek iade oranları görülen kargo sağlayıcılarıyla süreç analizi yapılarak iyileştirmeler yapılabilir. Ayrıca, müşteri memnuniyetini artırmak amacıyla alternatif kargo sağlayıcıları araştırılabilir.

3. **Makine Öğrenimi Modeli İyileştirmeleri**: Modelin doğruluğunu artırmak için hiperparametre optimizasyonu yapılabilir ve farklı algoritmalar (örneğin, XGBoost veya Gradient Boosting) deneyerek daha iyi sonuçlar elde edilebilir. Ayrıca, modelin genel performansını artırmak için yeni özellikler eklenebilir.


# Kaggle Linki
Bu projeyi Kaggle üzerinde çalıştığım notebook'tan görüntüleyebilirsiniz:  
[Kaggle - Aygaz Veri Bilimi](https://www.kaggle.com/code/demetasgaroglu/aygaz-ver-b-l-m)
