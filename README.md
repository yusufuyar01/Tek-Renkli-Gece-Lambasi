# Tek Renkli Gece Lambasi

Bu proje, bir fotosel (ışığa duyarlı direnç) kullanarak bir LED'in parlaklığını kontrol etmeyi amaçlar. Ortamdaki ışık seviyesi değiştikçe LED'in parlaklığı da buna göre ayarlanır.

## İçindekiler

- [Açıklama](#açıklama)
- [Gereksinimler](#gereksinimler)
- [Kurulum](#kurulum)
- [Kullanım](#kullanım)
- [Kod Açıklaması](#kod-açıklaması)
- [Devre Şeması](#devre-şeması)
- [Katkıda Bulunma](#katkıda-bulunma)
- [Lisans](#lisans)

## Açıklama

Bu proje, Arduino platformu kullanılarak geliştirilmiştir. Fotosel, ortamdaki ışık seviyesini ölçer ve bu değeri Arduino'ya analog olarak iletir. Arduino, bu değeri kullanarak LED'in parlaklığını ayarlar. Işık seviyesi arttıkça LED'in parlaklığı da artar, azaldıkça ise azalır.

## Gereksinimler

- Arduino Uno veya benzeri bir geliştirme kartı
- 1 adet fotosel (ışığa duyarlı direnç)
- 1 adet LED
- 2 adet direnç (biri fotosel için, diğeri LED için uygun değerlerde)
- Jumper kabloları
- Arduino IDE yazılımı

## Kurulum

1. Arduino IDE yazılımını indirin ve kurun.
2. Gerekli kütüphaneleri yükleyin (varsa).
3. Devre şemasını takip ederek komponentleri bağlayın.
4. Kodu Arduino IDE'ye kopyalayın.
5. Arduino kartınızı bilgisayara bağlayın.
6. Doğru portu seçin ve kodu yükleyin.
  
  ![Image](https://github.com/user-attachments/assets/1c728dea-bef5-4fda-bb31-78986352d757)

## Kullanım

Kod yüklendikten sonra, fotoselin üzerine düşen ışık miktarı değiştikçe LED'in parlaklığı da buna göre değişecektir.

## Kod Açıklaması

```c++
int led = 8; // LED'in bağlı olduğu pin
int parlaklik; // LED'in parlaklık değeri

void setup() {
  pinMode(led, OUTPUT); // LED pinini çıkış olarak ayarla
  pinMode(A0, INPUT); // Fotosel pinini giriş olarak ayarla
}

void loop() {
  parlaklik = analogRead(A0); // Fotoselden gelen değeri oku (0-1023)
  analogWrite(led, parlaklik); // LED'in parlaklığını ayarla (0-255)
}