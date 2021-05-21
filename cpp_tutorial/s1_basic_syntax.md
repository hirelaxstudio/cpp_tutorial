# Comment (Yorum) Satırları
***One Line Comment:***
```
// First Comment
// Second_1 Comment \
   Second_2 Comment
   Second_2 Comment (Çalışmaz çünkü \ yok)
```

***Multi Line Comment:***
```
/*
	Multi Line Comment
	Multi Line Comment
	Multi Line Comment
*/
```

# Kavramlar
***Object:*** Objects (objelerin) states (durumları) ve behaviors (davranışları) vardır. Örneğin bir köpeğin renk, isim, cins vb. states; koşma, havlama, yeme vb. ise behaviors’dur. Her class bir object’tir.

***Class:*** Bir objenin states (durumlarının) ve behaviors (davranışlarının) tutulduğu template'e (şablona) denir.

***Method:*** Temelde bir behavior’dur (davranıştır). Bir class birçok method içerebilir.

***Keyword:*** Compiler tarafından önceden tanımlanmış kelimelerdir. Bu kelimeleri kullanarak identifier (isimlendirme) işlemi yapılamaz.

***Variables:*** Bir programdaki temel depolama birimidir. Variable denilen şey, bir bellek konumuna verilmiş isimdir. Değişken üzerinde yapılan tüm işlemler o bellek konumunu etkiler. Variable declaration (değişken bildirimi), bir değişkenin ilk kullanımından önce bildirildiği veya tanıtıldığı kısmı ifade eder (Yani int a; tarzı bir kullanımla bir değişkeni bildirmek). Variable definition (değişken tanımı), değişkene bir bellek konumu ve bir değer atandığı kısımdır (Yani bildirilmiş değişkene a = 1; şeklinde değer atamak).
 - ***Local Variables:*** Bir block, method veya constructor içinde tanımlanan bir değişken, yerel değişken olarak adlandırılır. Bu değişken, bloğun içindeki algoritma çalışmaya başladığında ya da fonksiyon çağırıldığında yaratılır, blocktan çıkıldığında ya da fonksiyondan return edildiğinde yok olur. Bir local variable, sadece bulunduğu blocktan veya bulunduğu buloğun alt bloğundan erişilebilir. Local Variable'ları initialization yapmak zorunludur.
 
 - ***Instance Variables:*** Statik olmayan değişkenlerdir. block, constructor ve herhangi bir methodun dışındaki class’da bildirilir. Bir class’da bildirildiği için, bu variable’lar, class’ın bir object’i oluşturulduğunda oluşturulur ve nesne yok edildiğinde yok edilir. Local variable’ların aksine access specifiers kullanılabilir. Kullanılmazsa default access specifier kullanılır (access specifiers: Bir class’ın class member’larının erişilebilirliğini ayarlamak için kullanılan private, protected ve public gibi keyword’lerdir). Instance Variable'ları initialization yapmak zorunlu değildir. Bu variable’a sadece object oluşturarak erişebilirsin.

 - ***Static Variables:*** Class Variables olarak da bilinir. Instance variables ile benzer şekilde bildirilirler. Aralarındaki fark, static keyword kullanılarak bildirilmesidir (örnek: static int a;). Instance variables aksine, kaç tane object oluşturduğumuza bakılmaksızın her class için bir tane static variable kopyasına sahip olursunuz. Yani static variables, bir class’ın tüm objects’de ortaktır. Birinde yaptığınız değişiklik diğer objects yansır. Program yürütmenin başlangıcında oluşturulur ve yürütme sona erdiğinde otomatik olarak yok edilir. Static Variable'ları initialization yapmak zorunlu değildir çünkü default değeri sıfırdır. Eğer static variable'a Instance variable gibi erişirsen (bir object sayesinde), compiler warning message gönderecek ve programı durdurmayacaktır. Compiler, object name'i class name ile değiştirecektir. Static variable’a class adı olmadan erişirsek, compiler otomatik olarak class adını ekleyecektir. Static variables’e doğrudan class adı kullanılarak erişilebilir.

**Identifiers:** Tanımlayıcı anlamına gelir. Variable, function, class, module veya herhangi bir user-defined item tanımlamak için kullanılan bir addır. Bir identifier tanımlarken A-Z, a-z, _(alt çizgi), rakam (0-9) kullanımına izin verir. Özel noktalama karakterlerine izin vermez ve keyword'ler identifiers olamaz. C++, büyük - küçük harflere duyarlı bir dildir. Bu yüzden `int VRB` ile `int vrb` farklı iki variable'dır. 
 
***Stringizing operator (#):*** Stringizing operator, programın derlenmesi başlamadan önce önişlemciye bu satırların okumasını ve yorumlamasını söyler. Bir kütüphane include etmek (`#include <iostream>`) veya bir fonksiyon define etmek (`#define print(x) ...`) gibi '#' ile başlayan şeylere **preprocessor directives** denir. `#define`'dan sonra yazılan ifadeye **makro** denir. `#define`, C++ standartlarında olamayan herhangi bir şeyi define etmek (tanımlamak) için kullanılır. Örneğin `printf_s()` yazmaktan sıkılıp bu yapıyı `print()` şeklinde kullanmak istiyorsanız, aşağıdaki örnek koddaki gibi bir yola başvurabilirsiniz. '#' işareti tek başına kullanıldığında, kendinden sonra gelen ifadeyi string'e çevirir. Yani kendinden sonraki ifadeleri çift tırnak içine almış gibi davranır. Örneğin:
```cpp
#include <stdio.h>
#define print(x) printf_s(#x "\n")
int main() {
	print(Ekrana direkt basar \n ve string literals işler); // Print Output 1
	print("Ekrana direkt basar \n ama string literals işlemez"); // Print Output 2
}
```

Print Output 1:
```
Ekrana direkt basar
ve string literal'leri işler
```

Print Output 2:
```
"Ekrana direkt basar \n ama string literal'leri işlemez"
```

# C++ Basic (Temel) Syntax
```cpp
#include <iostream>
using  namespace  std;

int main() {
	cout << "Hello World!!!" << endl;
	return 0;
}
```

## 1) iostream Kütüphanesi
```cpp
#include <iostream> // standard input-output stream
```
C++'ın ana kütüphanelerindendir. `#include <iostream>` yönergesi, önişlemciye standart C++ kodunun **'header iostream'** olarak bilinen bir bölümünü eklemesini bildirir. Bu bölüm, standart input ve output işlemlerini içerir. Bu işlemler kısaca `cin` ve `cout` komutlarını içerisinde barındıran input ve output komutlarıdır.

## 1.1) Bazı iostream Objeleri
```cpp
std::cout << "Line 1\nLine End";
/* Output: (Sonraki satıra geçer)
line 1
Line End
*/
```

```cpp
std::cout << "Line 2\n\nLine End";
/* Output: (Bir satır boşluk bırakıp sonraki satıra geçer)
line 2

Line End
*/
```
```cpp
std::cout << "Line 3" << std::endl << "Line End";
/* Output: (endl, '\n' ile aynı işleve sahip)
line 1
Line End
*/
```
Satır atlama olayını anlamak için yukarıdaki örneklere bakabilirsiniz.
```cpp
int vrb;
std::cin >> vrb;
std::cout << vrb;
```
`vrb` adında ve integer data type'ında bir variable (değişken) declare ediyoruz. `std::cin` kullanarak `vrb` içine extraction operator (>>) ile bir değer define ediyoruz. Sonra da o değeri `std::cout` kullanarak insertion operator (<<) ile output olarak veriyor.

***Insertion Operator (<<)***
Tüm standart C ++ data type’ları için önceden programlanmış insertion operatörü, byte’ları bir output stream object’e (cout) gönderir.

***Extraction Operator (>>)***
Tüm standart C ++ data type’ları için önceden programlanmış extraction operatörü, bir input stream object’ten (cin) byte alır.

## 2) std Namespace
```cpp
using  namespace  std; // STandarD Character OUTput
```
Namespace'ler, include ettiğiniz header (.hh) dosyalarının içine tanımlanmıştır ve o header dosyalarının içine tanımlanan objeleri kullanabilmeniz için varlar. Örneğin bütün standart kütüphaneler *std* namespace'sini kullanır. *std* namespace'si, kod yazarken, `cout`, `cin`, `endl` etc. başına `std::` yazmaktan kurtarır. `cout` tek başına **unqualified name**'dir (nitelenmemiş isimdir). Standart C++ kütüphanesi yüklendiğine *std* adında bir namespace (ad alanı) ile gelir. Yani, *std* adını verdiğimiz bir namespace var, standart kütüphanelerin hepsi *std* adlı namespace'in icinde bulunurlar. İnsanlar genelde okunabilirliği daha fazla olduğu için std:: kullanmak yerine "using namespace std" kullanırlar. Ama isim çakışmalarını önlemenin en garanti yolu std:: kullanmaktır. Sürekli kullandığınız ifadelerin namespace'lerini teker teker yazmak sıkarsa, onları teker teker en başta tanımlayabilirsiniz. Örneğin:
```cpp
using std::cout;
using std::endl;
using std::cin;
```
yaparak sürekli `std::` yazma zahmetinden kurtulurken, namespace karışıklığının önüne geçmiş olursunuz.

**Not:** ':' kolon, '::' double kolon olarak isimlendirilir.

## 2.1) namespace
namespace dediğimiz şeyin amacı, kodları organize etmektir. Örneğin:
```cpp
#include <iostream>
namespace ornek {
	void deneme1() {
		std::cout << "selam 1" << std::endl;
	}
}

void deneme1() {
	std::cout << "selam 2" << std::endl;
}

int main() {
	ornek::deneme1(); // Output: selam 1
	deneme1(); // Output: selam 2
	return 0;
}
```
Yukarıdaki örnekte **ornek** adından bir namespace tanımladık ve içine tanımladığımız fonksiyonu **ornek namespace**'i, yani `ornek::` ile çağırdık. Böylece bu iki fonksiyon aynı isimli olmalarına rağmen farklı outputlar verdi.
## 3) main() Fonksiyonu
```cpp
int main() {
	// Kodlar...
}
```
`int main() { ... }` bir fonksiyondur.  Fonksiyonların syntax'ı aşağıdaki gibidir:
```
return_type function_name(parameter list) {
	body of the function
}
```
Fonksiyonlar, output'unun data type'ının belirtildiği `return_type`, adının belirtildiği `function_name`, parametrelerinin belirtildiği parantez içinde `(parameter list)` ve kullanılacağı işi yapması için ihtiyacı olan kodların bulunduğu süslü parantez içindeki body `{ ... }` kısımlarından oluşur. Bütün programların yürütülmesi (Run), nerede olduğuna bakılmaksızın `main()` fonksiyonu ile başlar ve biter. Fonksiyon ve namespace define ve hesaplama işlemleri `main()` dışında yapılır çünkü `main()` genellikle input ve output işlemlerinin yapıldığı (böyle tercih ediliyor) blocktur.

## 3.1) Return değerleri
```cpp
int main() {
	// Kodlar...
	return 0;
}
```
`main()` fonksiyonu integer data type'ında bir `return` değeri ile bitmek zorundadır. Bu `return` değerleri, hata kodları anlamına gelir. Bu hata kodları sadece `main()` fonksiyonunda geçerlidir. Bu hata kodları şunlardır:

***return 0:*** *"No Error"* demektir. *"EXIT_SUCCESS"* yani "Başarılı hata kodu. Program başarıyla sona erdi hata kodu." anlamına gelir.

***return 1:*** *"Error"* demektir. "Program hata ile sona erdi." anlamına gelir.

***return 2:*** *"Fatal Error"* demektir. "Program müthiş bir hatayla sona erdi." anlamına gelir. Mesela dosya açık kalırsa fatal (ölümcül) error'dür.

## 4) Noktalı Virgül (;)
Her statement, noktalı virgül ile biter. Preprocessor directives denilen (# ile başlayanlar) bu noktalı virgün ile bitme kuralının dışındadır. C++ programlamada yapılan en yaygın hatalardan birisi, statement'leri noktalı virgül ile bitirmeyi unutmaktır.

# Okunabilirlik

 - Kodun genel yerleşimi (tab, indent vb) düzgün ve tutarlı olmalıdır.
 - Küçük mantıksal bölümler satır boşlukları ile bloklanabilir.
 - Kaynak kodun gerekli yerlerine açıklamalar yerleştirilmelidir.
 - Kaynak dosyalarının başına başlık kısmı yerleştirilmelidir.
 - Fonksiyon ismi fonksiyonun yaptığı işi anlatacak şekilde
   oluşturulmalı.
	 - Örnek: GetWindowsDirectory();
 - Sabitler, anlamlı sembolik sabitler olmalıdır.
	 - Örnek: if ( n == OGRENCISAYISI )
 - Değişkenler anlamlı bir biçimde adlandırılmalıdır.
	 - Örnek: long lResult;
 - Kullanılan tür isimleri hangi konuda kullanıldığını açıklayacak
   biçimde olmalıdır.
	 - Örnek: Class Ogrenci();
 - Blockların içine yazılan kodlar {kodlar, kodlar} şeklinde de
   yazılabilir ama bu kodun derlenmesini etkilemese bile
   okunabilirliğini olumsuz etkiler.
	 - int main () { std::cout << " Hello World! "; std::cout << " I'm a C++
   program "; }
 - Büyük sayıları ' işaretini kullanılarak 2'107'153'623 şeklinde
   gösterilebilir. Compiler ' işaretini görmezden gelecektir.

# Macar Rotasyonu
| Sembol | Anlamı | Sembol | Anlamı |
|--|--|--|--|
| c | char | p | pointer |
| l | long | pc | (pointer to) char* |
| d | double | pl | (pointer to) long* |
| s | short | pv | (pointer to) void* |
| f | float | psz | (pointer to string of zero terminated) char* |
| u | unsigned (int) | ul | unsigned long (int) |
| b | BOOL | ull | unsigned long long |(int) |
| w | WORD | dw | DWORD |

# Blockların Çalışma Prensibi
Block açmak için `{ ... }` süslü parantezler kullanılır.
# 1) Local Variable
C++'da bir local (yerel) variable'a (değişkene), yalnızda bulunduğu block'ta ve bulunduğu block'un kapsadığı (içine aldığı) alt block'larda erişilebilir, blunduğu block'u kapsayan (içine alan) üst blocklar erişemez. Başka bir deyişle, bir obje sadece bulunduğu block ve bulunduğu block'u kapsayan (içine alan) scope'lardaki variable'lara erişebilir. Örnek:
```cpp
#include <iostream>
int main() {
	{
		int a = 1;
		std::cout << a << std::endl; // (Çalışır) (a ve x'i görüyor)
		std::cout << x << std::endl; // (Çalışır) (a ve x'i görüyor)
	}

	int x = 1;

	std::cout << x << std::endl; // (Çalışır) (Sadece X'i görüyor)
	std::cout << a << std::endl; // (Çalışmaz) (Sadece X'i görüyor)
	return 0;
}
```

