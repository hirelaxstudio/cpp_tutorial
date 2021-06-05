# Sık Kullanılan Built-in Types
***Boolean (bool):*** True (1) ya da False (0) değerini tutar.

***Character (char):*** 8 bit'lik (1 byte) boyutunda data depolayabilir. Bu data'ların ASCII tablosundaki karakter karşılıklarını verir.

***Integer (int):*** Integer sayıları (decimal hariç) depolar.

***Floating point (float):*** Float sayıları (decimal dahil) tutar. 32 bit (4 byte) veri depolayabilir.

***Double floating point (double):*** Float sayıları (decimal dahil) tutar. 64 bit (8 byte) veri depolayabilir.

***Valueless (void):*** Tipsiz demek. Bir değerin veya değişkenin tipini bilmiyorsan kullanılır.

***Wide character (wchar_t):*** UNICODE karakterleri tutar. her karakteri 16 bit (2 byte) şeklinde depolar.

***String (string):*** String ifadeleri (text'leri) tutar.

**Not:** *Decimal sayı sistemi*, 0'dan 9'a kadar sayıları tutar. Ama programlamada kullanılan *decimal*, decimal sayı sisteminden farklı olarak floating-point sayıları da tutar. (10/3)*3 gibi işlemler float data type kullanılarak yapılmaya çalışıldığında asla doğru sonucu vermez. Buna **float sapması** denir. *Float* **32 bit** data tutabildiği için bu sınırı aşınca işlemler yanlış sonucu verir. Aynı durum *double* için de geçerlidir. double **64 bit** data tutabilir ve bu sınırı aşınca işlemler sapıtır. *decimal* data type'ı C++ desteklemez. *decimal* data type, **128 bit** data tutabildiği için sapma çok azdır. Bu yüzden bankacılık gibi işlerdeki kritik hesaplamalarda *decimal* data type kullanılır.

# Character Type
Character Type tanımlarken tek tırnak kullanılır (`char b = 'f'`) çünkü çift tırnak string data'yı temsil eder. [ASCII karakter kümesi](https://www.w3schools.com/charsets/ref_html_ascii.asp)ndeki karakterlerin decimal karşılıklarını kullanarak da karakter elde edilebilir. Yani:
```cpp
char  ascii_trick_1 = 'A';
char  ascii_trick_2 = 65;
int  ascii_trick_3 = 'A';
int  ascii_trick_4 = 65;

cout << "char: " << ascii_trick_1 << " " << ascii_trick_2 << endl;
cout << "int: " << ascii_trick_3 << " " << ascii_trick_4 << endl;
```
Output:
```
char: A A
char: 65 65
```
**Dikkat:** Buradan sonraki kısımlarda, *(signed) char* örneğindeki gibi parantez içinde bazı kavramlar göreceksiniz. Bu kavramları parantez içinde yazmam, "Bunu yazmasan da olur." anlamına gelmektedir. Ama yine de yazmakta yarar var çünkü compiler kodu yorumlarken yanılabilir. Bu yüzden compiler'ın net bir anlam çıkarması için parantez içindekileri yazmamazlık yapmayın.
| Type | Açıklaması |
|--|--|
| `char` | En fazla 8 bit (1 byte) boyutunda data depolayabilir. Bu data'ların ASCII tablosuna göre [bytecode](https://en.wikipedia.org/wiki/Bytecode) karşılığını verir. |
| `char16_t` | En fazla 16 bit (2 byte) data depolayabilir. Bu dataların UNICODE encoded UTF-16 tablosuna göre [bytecode](https://en.wikipedia.org/wiki/Bytecode) karşılığını verir. |
| `char32_t` | En fazla 32 bit (4 byte) data depolayabilir. Bu dataların UNICODE encoded UTF-32 tablosuna göre [bytecode](https://en.wikipedia.org/wiki/Bytecode) karşılığını verir. |
| `wchar_t` | `wchar_t`, desteklenen en büyük karakter kümesini temsil eder ve UTF-16LE ile kodlanmış UNICODE karakterlerini kullanır. Bu yüzden 1 bit'lik bir karakter bile diğer her karakter gibi 16 ya da 32 bit (bir wide character) yer kaplıyor. Bir programı başka bir dile döndürmek istiyorsan, o programda `wchar_t` kullanmak avantajlıdır. |
| `string` | `#include <string>` komutuyla string kütüphanesini programa ekledikten sonra kullanılabilir. Çift tırnak içinde belirtilmiş text'leri (karakter dizilerini yani character array'ları) tutar. Yani string, `char[]` mantığıyla çalışır *(array'lar kısaca: aynı veri türündeki data'ları tutan bir liste.)*. |

# Integer Type
**Signed (işaretli)** ve **unsigned (işaretsiz)** prefix'leri (ön ekleri), o data type'ın sadece pozitif değerler mi alacağını yoksa hem pozitif hem de negatif değerler mi alacağını belirler. Signed prefix'i, bir bit'i sayının negatif ya da pozitif olduğunu belirtmek için kullanırken unsigned bunu yapmaz. Bu yüzden unsigned prefix'ine sahip bir data type, daha büyük pozitif değerleri ifade edebilir.

| Type | Açıklaması | Boyutu |
|--|--|--|
| (signed) char | 8 bit (1 byte) data depolayabilir. Character data type'a sahip değerleri ifade eder. | -127 to 127 |
| unsigned char | 8 bit (1 byte) data depolayabilir. Character data type'a sahip değerleri ifade eder. | 0 to 255 |
| (signed) short (int) | 16 bit (2 byte) yer kaplar. Integer data type'a sahip değerleri (sayıları) ifade eder. Decimal değerleri ifade etmez. | -(2^15^) to (2^15^)-1 |
| unsigned short (int) | 16 bit (2 byte) data depolayabilir. Integer data type'a sahip değerleri (sayıları) ifade eder. Decimal değerleri ifade etmez. | 0 to (2^16^)-1 |
| (signed) int | 32 bit (4 byte) data depolayabilir. Integer data type'a sahip değerleri (sayıları) ifade eder. Decimal değerleri ifade etmez. | -(2^31^) to (2^31^)-1 |
| unsigned (int) | 32 bit (4 byte) data depolayabilir. Integer data type'a sahip değerleri (sayıları) ifade eder. Decimal değerleri ifade etmez. | 0 to (2^32^)-1 |
| (signed) long (int) | 64 bit (8 byte) data depolayabilir. Integer data type'a sahip değerleri (sayıları) ifade eder. Decimal değerleri ifade etmez. | -(2^63^) to (2^63^)-1 |
| unsigned long (int) | 64 bit (8 byte) data depolayabilir. Integer data type'a sahip değerleri (sayıları) ifade eder. Decimal değerleri ifade etmez. | 0 to (2^64^)-1 |
| (signed) long long (int) | 128 bit (16 byte) data depolayabilir. Integer data type'a sahip değerleri (sayıları) ifade eder. Decimal değerleri ifade etmez. | -(2^127^) to (2^127^)-1 |
| unsigned long long (int) | 128 bit (16 byte) data depolayabilir. Integer data type'a sahip değerleri (sayıları) ifade eder. Decimal değerleri ifade etmez. | 0 to (2^128^)-1 |

**Önemli Not:** Bu data type'ların boyutu farklı işletim sistemi ve farklı compiler'larda farklılık gösterir. Kabaca anlatmak gerekirse, 32 bitlik işletim sistemleri 128 bit'lik `long long int` veya 64 bit'lik `long int` değerlerini desteklemediği için bu değerleri de 32 bitlik kabul eder ve kodları öyle yorumlar. Benzer şey compiler'lar için de geçerlidir. Bu yüzden farklı tutorial kaynaklarında bu data type'ların bit değerleri farklı verilmiştir. Ama teoride yukarıdaki tabloda belirtildiği büyüklüktedirler. Aynı durum aşağıdaki **Floating-point Type** başlığının altındaki `double` ve `long double` data type'ları için de geçerlidir.

# Floating-point Type
Decimal type sayıları ifade eder. Yani 3.14 gibi kesirli sayıları ifade eder. *float* data type'ın range (kapsadığı alan) sıkıntıları yüzünden genellikle *double* data type tercih edilir. Bu sunlardan en bilindiği **float sapması**'dır.
| Type | Açıklaması |
|--|--|
| float | 32 bit (4 byte) data depolayabilir. |
| double | 64 bit (8 byte) data depolayabilir. |
| long double | 96 bit (12 byte) data depolayabilir. |

# Boolean Type
Boolean değerler True (1) ve False (0) olmak üzere iki tanedir. 1 bit ile ifade edilirler. Program yazarken True ya da False keyword'lerini kullansak da, bilgisayar bu değerleri 1 ve 0 olarak işler. Örnek:
```cpp
bool BooleanType1 = true;
bool BooleanType2 = false;
```

# Void Type
void data type, **"untyped (tipsiz)"** veya **"type not specified (tipi belirtilmemiş)"** olarak ifade edebileceğimiz, hiçbir veri türü ile ilişkilendirilmemiş data type anlamına gelir. Bir value'nun veya variable'ın type'ını bilmiyorsanız veya bir variable'ın data type'ını daha sonra belirlemek istiyorsanız veya farklı data type'lar üzerinde çalışmanız gerekiyorsa kullanabileceğiniz bir data type çeşididir.
```cpp
void vrb; // declare vrb
```

# Null Pointer
*NULL*, "Boş, harhangi bir value içermiyor." anlamına gelir. *NULL*, bir değer içermez ama değer alabilecek durumdadır. Bulunduğu bellekteki değeri boşaltmak için kullanılır.
```cpp
int  *ptr = NULL;
```
**Not:** NULL ile void arasındaki fark, void bir type'dır, null bir value'dir.

# typedef Declarations
`typedef` kullanarak mevcut bir tür için yeni bir ad oluşturabilirsiniz. Örnek:
```cpp
typedef int sayi; 
sayi a = 1;
```
Burada `int` data type'ının adı `sayi` olarak değiştirildi ve artık `int a = 1;` şeklinde define işlemi yapmak yerine `sayi a = 1;` define işlemi yapılır.

# Enumerated Types
*Enumerated type (enumeration)*, integral constant'lardan oluşan used-defined (kullanıcı tanımlı) bir data type'dır. `enum` keyword'ü ile ifade define edilir.
```cpp
enum isimler { ali, veli, hakan, yusuf };
```
Default olarak ali 0, veli 1, ... olarak numaralandırır. Bu numaralandırma sırasını gerekirse değiştirebilirsiniz. Örneğin:
```cpp
enum season {
	spring = 0,
	summer = 4,
	autumn = 8,
	winter = 12
};
```
## Enumerated Type Declaration
Bir *enumerated type* oluşturduğunuzda (create), bir variable için sadece blueprint (taslak) oluşturursunuz. Örnek:
```cpp
#include <iostream>
using namespace std;

enum week { Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };

int main() {
	week today;
	today = Wednesday;
	cout << "Day " << today+1;
	return 0;
}
```
Buradaki `today`'ı declare ederken 3 şekilde edebiliriz:
```cpp
enum week { Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday } today;
```

```cpp
enum week { Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };
enum week today;
```

```cpp
enum week { Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };
week today;
```
Başka bir örnek:
```cpp
#include <iostream>
using namespace std;

enum seasons { spring = 34, summer = 4, autumn = 9, winter = 32};

int main() {
	seasons s;
	s = summer;
	cout << "Summer = " << s << endl;
	return 0;
}
```
Bir **enum** variable'ı, birçok olası value'den yalnızca bir value alır. Aynı sonucu structure kullanarak da elde edebilirsiniz ama **enum** kullanmak daha verimlidir.
