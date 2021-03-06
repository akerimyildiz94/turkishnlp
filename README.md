
Not : Türkçe dökümantasyon aşağıdadır.

See [Change Log](Changelog.md)

Note that version 0.0.4 is not published on Pypi so that syllabication is not available on current pip release yet. You can still download it manually and use syllabication

Versiyon 0.0.4 henüz Pypi da yayınlanmadığından, heceleme şu anki pip versiyonunda kullanılabilir değil. Yine de kendiniz GitHub üzerinden projeyi indirip hecelemeyi kullanabilirsiniz



# Turkish NLP with Python

## Performance 

|  Method    | Execution Time (ms) | Words Count|
|------------|----------|----------|
| auto_correct                     | 135 ms                  | 1000 words |
| is_turkish                       | 1 ms                    | 1000 words |
| syllabicate_sentence             | 94 ms                   | 1000 words |


Very early version of the TurkishNLP. For now it has basically 3 main functions; Detecting Turkish Language, correcting typos and syllabication in Turkish words.

## Dataset
Dataset was created by parsing and filtering a Turkish wikipedia dump. 

## Getting Started
To get started first you need to install the package. With using pip;
```
pip install turkishnlp
```
After installing the package succesfully try and import the package.

```
import turkishnlp
```
### Downloading the data
To download the data first we need to create an instance of TurkishNLP class. So we need to ;
```
from turkishnlp import detector
obj = detector.TurkishNLP()
```
After creating the instance we can simply call the download function like this;

```
obj.download()
```
It will take shortly and after the download it will print out "Download succesful". You won't have to download the data again.

### Creating the wordset
To create the wordset from data you need to ;
```
obj.create_word_set()
```
And it will create the wordset and necesary dictionaries.

### Example Usage
So there are 3 main functions, detecting if the language is Turkish, Turkish typo correction and syllabication.

### Language Detection
```
print(obj.is_turkish("Ben bugün ankaraya gideceğim belki birşeyler alırım"))
```
Will return us "True" along with the accuracy point which is 0.85

### Typo Correction

```
lwords = obj.list_words("vri kümsi idrae edre ancaka daha güezl oalbilir")
print(obj.auto_correct(lwords))
```
Which will print out ['veri', 'kümesi', 'idare', 'eder', 'ancak', 'daha', 'güzel', 'olabilir']. "List_words" method simply splits the text by words with the help of regex. You can simply use "join" to make it a sentence again like this;

```
lwords = obj.list_words("vri kümsi idrae edre ancaka daha güezl oalbilir")
corrected_words = obj.auto_correct(lwords)
corrected_string = " ".join(corrected_words)
```
Which will print out 'veri kümesi idare eder ancak daha güzel olabilir'. 

### Syllabication

```
obj.syllabicate_sentence("Hiç unutmadım, doğudan esen hafif bir yel saçlarını dalgalandırıyordu")
```
And it will give you ;

"[['hiç'], ['u', 'nut', 'ma', 'dım,'], ['do', 'ğu', 'dan'], ['e', 'sen'], ['ha', 'fif'], ['bir'], ['yel'], ['saç', 'la', 'rı', 'nı'], ['dal', 'ga', 'lan', 'dı', 'rı', 'yor', 'du']]"

# Python ile Türkçe Dil İşleme

TurkishNLP kütüphanesinin alfa versiyonu. Şimdilik Türkçe dilini tespit etme, Türkçe yazım hatalarını düzeltme ve kelimeleri hecelere ayrıma olmak üzere 3 ana fonksiyonu var

## Veri
Veri kümesi wikipedia'nın Türkçe dump'ı parselanıp temizlenerek oluşturuldu.

## Başlarken
Öncelikle başlamadan, pip ile kütüphaneyi yüklemeniz gerekiyor. Şu şekilde;
```
pip install turkishnlp
```
Yükledikten sonra kütüphaneyi şu şekilde import etmeyi deneyin;

```
import turkishnlp
```
### Veriyi indirmek
Veriyi indirmek için önce TurkishNLP sınıfından türetilmiş bir obje oluşturmamız lazım;
```
from turkishnlp import detector
obj = detector.TurkishNLP()
```
Objeyi oluşturduktan sonra indirme metodunu şu şekilde çağırarak indirme işlemini başlatabiliriz ;

```
obj.download()
```
İndirme işlemi çok uzun sürmeden bitecek ve ardından "Download Succesful" yani indirme başarılı manasına gelen bir yazı ekrana basılacak

### Verisetini oluşturmak
İndirdiğimiz veriden kodun içinde kullanacağımız verisetlerini oluşturmak için basitce;
```
obj.create_word_set()
```
Yapıyoruz ve işlem tamamlanmış oluyor

### Örnek Kullanım
Başlıkta da belirttiğim gibi temel olarak 3 metod var.

### Türkçe Dil Tespiti

```
print(obj.is_turkish("Ben bugün ankaraya gideceğim belki birşeyler alırım"))
```
Yaptığında göreceğiz ki, ekrana "True" bastırıyor ve doğruluk oranı olarak 0.85 döndürüyor.

### Yazım Hatası Düzeltme

```
lwords = obj.list_words("vri kümsi idrae edre ancaka daha güezl oalbilir")
print(obj.auto_correct(lwords))
```
Yapıyoruz ve sonuç olarak bize ['veri', 'kümesi', 'idare', 'eder', 'ancak', 'daha', 'güzel', 'olabilir'] listesi veriliyor. Burada "list_words" metodunun yaptığı string olarak gelen texti regex yardımıyla kelimelerine ayırmaktır Kelimeleri birleştirmek için Python'ın "join" metodu kullanılabilir. Örneğin;

```
lwords = obj.list_words("vri kümsi idrae edre ancaka daha güezl oalbilir")
corrected_words = obj.auto_correct(lwords)
corrected_string = " ".join(corrected_words)
```
Yazdıracağı sonuç : 'veri kümesi idare eder ancak daha güzel olabilir'. 

### Hecelere Ayırmak 
```
obj.syllabicate_sentence("Hiç unutmadım, doğudan esen hafif bir yel saçlarını dalgalandırıyordu")
```
Yapıyoruz. Ve dönen sonuç;

"[['hiç'], ['u', 'nut', 'ma', 'dım,'], ['do', 'ğu', 'dan'], ['e', 'sen'], ['ha', 'fif'], ['bir'], ['yel'], ['saç', 'la', 'rı', 'nı'], ['dal', 'ga', 'lan', 'dı', 'rı', 'yor', 'du']]"
