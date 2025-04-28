<img width="659" alt="image" src="https://github.com/user-attachments/assets/7b2c48c7-95d6-4f4c-9b52-f7a8f4994dac" /># Nesne Tanımada Derin Öğrenme Mimarilerinin Performans Karşılaştırması
Bu çalışma, nesne tanıma için yaygın olarak kullanılan farklı derin öğrenme modellerinin performansını, veri augmentasyonu eklemeyi içeren bir yöntemle karşılaştırmaktadır. Kullanılan modeller arasında YOLO (You Only Look Once), Faster R-CNN (Region-based Convolutional Neural Networks), SSD (Single Shot Multibox Detector), ResNet50 ve RetinaNet yer almaktadır. 

Çalışma, COCO veri seti üzerinde bu modellerin nesne tespiti başarılarını, orijinal ve augmentasyona tabi tutulmuş veri setlerinde test ederek karşılaştırmaktadır. Veri augmentasyonu ile model doğruluğunda gözle görülür iyileşmeler sağlanmıştır. Bu çalışma, nesne tespiti alanında en verimli derin öğrenme mimarisinin tespit edilmesini amaçlamaktadır.

# Çözüm Dizaynı

Hazırladığımız çözümün akışını adım adım açıklamak gerekirse, süreç aşağıdaki gibi olacaktır.

## 1. Verinin Hazırlanması
- COCO’dan rastgele görsel seçimi
- COCO’dan görsele ait nesne etiketlerinin yüklenmesi

## 2. Verinin Normalizasyonu
- Görselin normalizasyonu
  - RGB renk kodları ile encode etme
  - Standart boyutlara göre yeniden boyutlandırma

## 3. Nesne Tespiti
- YOLO v3 modeli ile görselde nesne tespiti

## 4. Çıktıların Normalizasyonu
- COCO ve YOLO nesne etiketlerinin aynı hale getirilmesi (standardizasyon)

## 5. Tespit Başarımı Ölçümü
- Jaccard’s Index (accuracy), Precision, Recall ölçümlerinin yapılması
- Intersection over Union başarı ölçümü
- Raporlama

# Projenin Dosya ve Dizin Yapısı

**Projenin linki:** 🔗 [Yapay Zeka Final Projesi (500).pynb](https://colab.research.google.com/drive/1m8h1GcXX9mkB17m9Rhf6sKHBAP9kyoOq#scrollTo=2j3RA_nqN6oi)

Aşağıdaki ekran görüntüsünde projenin dosya ağacı yer alıyor.

- Kırmızı ile işaretli “Goruntu Isleme Deneme 2.ipynb” ödevin kendisi olan notebook dosyası.
- Turuncu ile işaretli “annotations” dizini ve altında yer alan dosyalar, COCO veri setinin import edilebilmesi için gerekli annotations dosyalarını içeriyor.
- Son olarak açık mor rengi ile işaretli dosyalar, önceden eğitilmiş YOLO v3 modelini kullanabilmemizi sağlayacak yardımcı dosyaları içeriyor. 
  - Bu dosyalardan `yolov3.weights`, pre-trained yapay sinir ağı modelinin ağırlık konfigürasyonunu içermekte.
  - `darknet.py` ve `utils.py` dosyaları ise bizim kendi notebook’umuza import edeceğimiz yardımcı Python modülleri.
