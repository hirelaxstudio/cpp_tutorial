# Variable Definition (Değişken Tanımlamak)
Variable'lar (değişkenler), en küçük depolama birimidir. Variable, compiler'a  nerede ve ne kadar depolama alanı yaratacağını söyler. Her variable spesifik bir data type'a sahiptir. Bir data type ile tek satırda birden fazla variable definition (tanımlama) işlemi yapabiliriz. Örneğin:
```cpp
int a = 1, b = 2, c = 3;
```

# Variable Declaration (Değişken Bildirmek)
İlk kez yapılan variable declaration işlemine **create** denir. Bir variable'a *declaration (bildirmek)* işlemi yaparsanız, elinizde hiçbir value içermeyen bir bellek adresi olur. Bir variable'ı declare ederek (bildirerek) compiler'a böyle bir değişkenin varolduğunun güvencesini vermiş oluyorsunuz. Böylece compiler hata vermeden compile işlemine devam eder. Bu işlem sadece compile kısmında hata vermez. Compiler, link işleminde variable definition'a ihtiyaç duyar. Variable definition, birden fazla dosya ile çalışırken, bir dosyada declaration işlemi yaptığınız variable'a, başka bir dosyada *(extern keyword'ü ile)* definition işlemi yapacağınız zaman yararlıdır. Çünkü böyle yapmazsanız daha önce de bahsettiğim gibi, link işleminde sorun yaşarsınız çünkü compiler *undefined variable* tehlikesi ile karşı karşıya kalır. Bir dosyada declare ettiğiniz bir variable'ı başka bir dosyada define edebilmek için bu iki variable'ın birbirinden haberdar olması lazım. Bunun için **extern** keyword'ünü kullanıyoruz (extern daha sonra açıklanacak). Örnek:

**Dosya 1:**
```cpp
#include <iostream>
using namespace std;

int file1_vrb = 1;
int main() {
	int file1_vrb = 1;
	return 0;
}
```

**Dosya 2:**
```cpp
#include <iostream>
using namespace std;

extern file1_vrb;
int main() {
	cout << file1_vrb << endl;
	return 0;
}
```
**Output:** `1`

# Variable Initialization
Bir data object veya variable için başlangıç değeri atama işlemine denir. Örneğin ilk kez declare ettiğiniz (bildirmeniz) bir variable’ı programda kullanmak için garanti olsun diye define’da  etmeniz (tanımlamanız da) gerekmektir. Bu define işlemine *initialization*, yani başlangıç değeri atama denir. Bu şu işe yarar: Bir variable’ı initialization yapmadan direkt `a += 1` gibi bir işleme sokamazsınız, compiler hata verir. Çünkü C++’da compiler’lar genellikle, declare edilmiş variable’lara otomatik değer atamaz yani otomatik initialization yapmaz. Otomatik değer atanmadan sadece declare edilen variable’ların value’si *NullPointer* olur. Örneğin:
```cpp
#include <iostream>
using namespace std;
int a; // Declaration 
int b = 0; // Initialization
int main() {
	cout << a << endl; // Output: 0
	cout << b << endl; // Output: 0
	return 0;
}
```
Declaration, Definition ve Initialization örnek kod:
```cpp
#include  <iostream>

int  main() {
int number1 = 15; // declaration + definition (initialization)
int number2; // declaration
number2 = 30; // definition

int number3 = 45; // declaration + definition (initialization)
number3 = 60; // Value change

int x = 1, y = 2, z = 3; // declaration + definition Multiple Variables (initialization Multiple Variables)

return  0;
}
```
**Not:** NullPointer'ın value'su sıfırdır. Bu value, sıfır sayısının hexadecimal halidir. Yani: `0x0`

**Not:** Initializer olmadan definition yaparsan, static storage duration variable'lar dolaylı olarak NULL *(NULL ile NullPointer aynı kavram)* ile başlatılır, diğer tüm variable'lar başlangıç değeri *undefined*'dır.

**Not:** *Static storage duration* (statik depolama süresi) olan bir variable için depolama boyutu *(storage size)* ve *adresi (address)* derleme (compile) zamanında (program çalışmaya başlamadan önce) belirlenir. Depolama ömrü (storage lifetime), program çalıştığı sürece (program execution time) devam eder. Dosya (file) veya  namespace kapsamında declare edilen bir variable'ın static storage duration'ı vardır. Daha fazla bilgi için [tıklayın](https://www.sciencedirect.com/topics/engineering/storage-duration).

# Bazı Kavramların Açıklamaları
## extern Keyword
Bir kaynak dosya (source file) içinde define edilen bir variable'a ya da function'a, yalnızca define dildiği kaynak dosya içinde değil, projeyi oluşturan diğer kaynak dosyalarda da erişilebiliyorsa, variable'ın ya da function'ın **dış bağlantısı (external linkage)** vardır denir.

Bir kaynak dosya (source file) içinde define edilen bir variable'a ya da function'a, yalnızca define dildiği kaynak dosya içinde erişilebiliyorsa, projeyi oluşturan diğer kaynak dosyalarda erişilemiyorsa, variable'ın ya da function'ın **iç bağlantısı (internal linkage)** vardır denir.

**extern** keyword'ü, compiler'a, variable'nin dışarıda tanımlandığını bildirmek için kullanılan bir keyword'tür. Compiler, *extern* keyword'ünü gördüğünde, variable için alan tahsisinde bulunmaz. Örneğin, *first_file.cpp* adında bir dosyada `void a = 1;` şeklinde tanımlanmış bir variable olsun. `second_file.cpp` dosyasında ise `extern int a;` şeklinde bir tanımlama yapıp bu variable'ı `std::cout << a;` şeklinde çağırırsak ekrana `1` basıldığını görürüz. Eğer `first_file.cpp` dosyasında `void a = 1;` şeklinde bir definition işlemi yapılmasaydı veya orada da `extern int a;` şeklinde bir declaration işlemi yapılsaydı, compile aşamasında hata vermese bile link aşamasında hata verirdi.

## NULL (NullPointer) ve undefined variable
**NULL** ve **undefined** iki farklı kavramdır. Bilgisayara *NULL*'un açıklaması yapıldıysa, bilgisayar *NULL*'un *"boş value"* anlamına geldiğini bilir. extern ile tanımlanan (Örnek: `extern int a;`) variable'ın value'su *NULL*'dur. Bilgisayar *NULL*'u `0` sayısı ile temsil eder. *Undefined variable* ise *"tanımsız değişken"* anlamına gelir. Bilgisayar bir undefined variable ile karşılaştığında, veri kaybı tehlikesinden ötürü ne yapacağından emin olamaz ve error code verir. Ama sen compiler'a *NULL* olarak define edilmiş bir variable için net bir şekilde *"bu variable boştur"* dediğin için compiler da bunu böyle kabul ediyor.

**Başka önemli kavramlar kavramlar hakkında bilgi için [tıklayınız](https://medium.com/@sddkal/c-ta%C5%9F%C4%B1ma-semantiklerine-neden-i%CC%87htiya%C3%A7-var-51464b594b2e).**

