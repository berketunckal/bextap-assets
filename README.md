# Unity Strateji Haritası Oluşturucu (Map Generator)

Bu araç, **GeoJSON** verilerini kullanarak Unity içinde yüksek performanslı, etkileşimli ve özelleştirilebilir **2D Strateji Haritaları** (Grand Strategy / Risk benzeri) oluşturmanızı sağlar.

![Map Generator Demo](Screenshots/demo.png)
*(Buraya oyun içi veya editörden güzel bir görsel ekleyin)*

## 🌟 Özellikler

*   **🚀 Tek Tıkla Kurulum:** `ne_10m_admin_1_states_provinces` gibi standart GeoJSON dosyalarını otomatik tanır ve işler.
*   **📐 Mesh Üretimi & Optimizasyon:** 
    *   **Ear Clipping** algoritması ile karmaşık poligonları düzgün mesh'lere çevirir.
    *   **Douglas-Peucker** algoritması ile gereksiz köşe noktalarını temizleyerek performansı artırır (Ayarlanabilir Tolerans).
*   **🏷️ Akıllı Etiketleme:**
    *   Ülke sınırlarını hesaplar ve ismi en uygun merkeze yerleştirir.
    *   Ülke yüz ölçümüne göre yazı boyutunu (Font Size) otomatik ölçekler.
    *   Şehirler ve bölgeler için otomatik alt etiketler oluşturur.
*   **🎨 Dinamik Stil (Runtime Styling):**
    *   Oyun çalışırken sınır renklerini, kalınlıklarını ve yazı tiplerini değiştirebilirsiniz.
    *   **LineRenderer** tabanlı sınır çizimi ile pürüzsüz görünüm.
*   **📦 Bağımlılıksız (Standalone):**
    *   `Newtonsoft.Json` veya `LibTessDotNet` gibi harici DLL'lere ihtiyaç duymaz (Gerekli kütüphaneler optimize edilerek içine gömülmüştür).

## 📸 Ekran Görüntüleri

### Editör Arayüzü (Map Baker)
Kullanıcı dostu arayüz ile saniyeler içinde bake işlemi yapın.
![Map Baker Window](Screenshots/baker_ui.png)

### Oyun İçi Görünüm
Renk paletleri ve yazı tipleri tamamen özelleştirilebilir.
![Ingame Map](Screenshots/ingame_map.png)

## 🛠️ Kurulum

1.  Bu projeyi indirin ve `Assets/MapGenerator` klasörünü kendi Unity projenize sürükleyin.
2.  (Opsiyonel) Eğer TextMeshPro yüklü değilse, Unity size soracaktır veya "Window > TextMeshPro > Import TMP Essentials" yolunu izleyin.

## 📖 Kullanım

1.  Unity Editör'de **Tools > Map Baker** menüsünü açın.
2.  **GeoJSON File** kısmına harita veri dosyanızı sürükleyin (Proje içinde varsayılan olarak `SampleData` klasöründe gelir).
3.  **Map Font** kısmına istediğiniz bir `TMP_FontAsset` atayın.
4.  **Simplify Level** çubuğunu kaydırarak detay/performans dengesini ayarlayın (Önerilen: 0.001 - 0.005).
5.  **BAKE WORLD MAP** butonuna basın.
6.  Oluşturulan harita `Assets/GeneratedMap` klasörüne prefab olarak kaydedilecektir.

## 🧩 Teknik Detaylar

*   **Veri Yapısı:** GeoJSON verisi `MiniJSON` (optimize edilmiş) ile okunur.
*   **Üçgenleme:** Özel olarak uyarlanmış `LibTessDotNet` (Ear Clipping) kullanılır.
*   **Görünüm:** Materyaller `Sprites/Default` shader'ı kullanır, böylece ışıklandırmadan bağımsız net renkler elde edilir.

---
*Geliştirici Notu: Bu proje açık kaynaklıdır ve strateji oyunu prototipleri için tasarlanmıştır.*
