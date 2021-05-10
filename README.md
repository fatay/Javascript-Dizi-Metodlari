# Javascript-Dizi-Metodlari
### Javascript Dizi Metodları (Türkçe) ###

Javascriptteki en önemli dizi metodlarını Türkçe açıklamalarıyla beraber aşağıda bulabilirsiniz. data adlı değişken app.js 'de tanımlanmış olup, burada sadelik açısından veriler gösterilmemiştir. Denemek için repositoryi indirip test edebilirsiniz.

### Array.find() ###
Belirli kriteri sağlayan elemanlardan tekil olarak bir tanesini getirir. Örneğin id 'si "5e652aa659a9911f63e6e218" olan veriyi getirmek istersek;

```javascript
let foundById = null;
foundById = data.find(item => item._id = "5e652aa6fb34c68462a97fe9z");
console.log(foundById);
```
Şimdi de yaşı 35ten küçük olan kaydı getirelim. 

```javascript
let foundByAge = data.find(item => item.age < 35);
console.log(foundByAge);
```
find fonksiyonu tekil çalıştığından şartı sağlayan ilk kaydı getirir. Bu nedenlerden dolayı eğer kayıt eşsiz(unique) ise find, değilse ve çoklu getirilmek isteniyorsa ileride göreceğimiz filter metodu kullanışlıdır.

### Array.findIndex() ###
Bu metod, find ile aynı mantıkla çalışır ve bulunan elemanın indeksini getirir.

```javascript
let foundIndex = data.findIndex(item => item._id === "5e652aa6fb34c68462a97fe9")
console.log(foundIndex);
```

### Array.indexOf() ###
Eğer aranan kritere uyan eleman varsa pozitif olarak indeksini, değilse -1 negatif sayısını döndürür. Stringlerde de bulunan bu metod, eşitse 0 döndürmektedir.

```javascript
let newArr = [
    "Fatih",
    "Aydın",
    "Defne",
    "Enis",
    "İsmail",
    "Ferit",
    1,
    2,
    3,
    4,
    5
];

let findIndex  = newArr.indexOf("Fatih");
```

Belirli bir indeksten sonra aramak istersek;

```javascript
let findIndexA = newArr.indexOf("İsmail",3);
```

### Array.filter() ###
Diziyi filtreyerek filtreden geçen elemanlarla yeni bir dizi oluşturur.

```javascript
let filterByAEG = data.filter(item => item.age > 30 && item.eyeColor == "blue" && item.gender == "female");
```

Ayrıca filtreleme işleminden sonra yapılacak işlemler devam edecekse; şu şekilde de kullanılabilir;

```javascript
let filterBy = data.filter(
    item => {
        // işlemler...
    }
);
```

### Array.map() ###
Filter fonksiyonu filtreledikleri elemanların tüm fieldlarını getiriyordu. Array.map() fonksiyonu sayesinde; örneğin sadece maillerden oluşan bir dizi oluşturabiliriz.

```javascript
let mapper  = data.map(item => item.email);
console.log(mapper);
```

Veya sadece mail ve company(şirket) bilgisinin olduğu bir dizi döndürmek istersek;

```javascript
let mapping = data.map(item => {
    return {
        eposta_adresi : item.email,
        sirket_bilgisi : item.company 
    };
});
console.log(mapping);
```

Diziyi şu şekilde manipüle de edebiliriz;
```javascript
let manipulatedString = data.map(item => {
    return "(" + item.name + ")" + " " + item.phone + " " + item.address;
});
console.log(manipulatedString);
```

Veriye daha kolay ulaşmak için map ile kısaltmalar oluşturabiliriz;

```javascript
const coordinates = data.map(item => {
    return {
        lat: item.latitude,
        long: item.longitude
    };
});
console.log(coordinates);
```

### Array.reduce() ###
Tekilleştirici dizi fonksiyonudur. Bir diziyi tek bir değere indirgemek için kullanılır.

```javascript
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// çıktı: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// çıktı: 15
```

### Array.forEach() ###
İteratif olarak dizi elemanlarını döndürmemizi sağlamaktadır.

```javascript
const araba = [
    {marka: "Porsche", fiyat: 100000},
    {marka: "Audi",    fiyat: 80000},
    {marka: "Toyota",  fiyat: 30000}
];

araba.forEach(araba => {
    console.log(`${araba.marka} fiyatı ${arabalar.fiyat} dolardır.`);
  });
```
Çıktı:
    "Porsche fiyatı 100000 dolardır."
    "Audi fiyatı 80000 dolardır."
    "Toyota fiyatı 30000 dolardır."


### Array.every() ###
Bir dizinin tüm elemanlarını irdeleyerek belirtilen conditionu sağlayıp-sağlamadığına bakar.
EĞER Kİ TÜM ELEMANLAR ŞARTI SAĞLARSA TRUE,
DEĞİLSE FALSE döndürür.

```javascript
const kisiler = [
    {isim: "Fatih",  yas: 24},
    {isim: "İsmail", yas: 23},
    {isim: "Refik",  yas: 60}
];
  
const yirmiYasindanBuyukler = kisiler.every(kisi => kisi.yas >= 20);
```
Çıktı: true

### Array.some() ###
Bir dizinin tüm elemanlarını irdeleyerek belirtilen conditionu sağlayıp-sağlamadığına bakar.
EĞER Kİ ELEMANLARDAN BİR TANESİ BİLE ŞARTI SAĞLARSA TRUE,
DEĞİLSE FALSE döndürür.

```javascript
const calisanlar = [
    {isim: "Fatih",  yas: 24},
    {isim: "İsmail", yas: 23},
    {isim: "Refik",  yas: 60}
];
const altmisYasindanBuyukler = calisanlar.every(calisan => calisan.yas >= 60);
```

Kısacası ;
*   every() =>  condition1 && condition2 && ... conditionN  (AND)
*   some()  =>  condition1 || condition2 || ... conditionN  (OR)

şeklinde ilerlemektedir.

Fatih Aydin, 2021
