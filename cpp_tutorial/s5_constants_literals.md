# Constants ve Literals
**Constants** kelime anlamı olarak *sabitler*, **Literals** ise *değişmezler* anlamına gelir. Bu iki kavram birbirine benzerdir.

**Constants**, değiştirilemez sabit value'ları ifade eder. Bir variable `const` olarak initialize edilirse, programın başka bir yerinde o variable'a başka bir value define edilemez. Örneğin `const int a;` şeklinde bir declare işlemi yaparsanız, o variable *undefined* olarak kalır, değiştiremezsiniz. Constant variable'lar, genellikle 3.14 gibi program boyunca değiştirmeyeceğiniz variable value'lar için kullanılabilir. Örnek const:
```cpp
const int a = 15; // Artık a'nın değeri her zaman 15
a = 10;  // error: assignment of read-only variable 'a'
```
Base value type'ların (temel değer türlerinin) değiştirilemez (literal) sabitleri (constant'ları) vardır. Bunlara ise **Literals** denir.

## Defining Constants (Sabit tanımlama)
Defining Constants tanımlamanın 2 yolu vardır.

### 1) `#define` preprocessor (önişlemci) kullanmak
**SYNTAX:** `#define identifier(name) value`
```cpp
#include <iostream>
using namespace std;

#define LENGTH 10
#define WIDTH  5
#define NEWLINE '\n'

int main() {
	int area;
	area = LENGTH * WIDTH;
	cout << area;
	cout << NEWLINE;
	cout  <<  "Alt satıra geçildi.";
	return 0;
}
```
Output:
```
50
Alt satıra geçildi.
```

### 2) `const` keyword kullanmak
**SYNTAX:** `const type variable = value;`
```cpp
#include <iostream>
using namespace std;
int main() {
	const int  LENGTH = 10;
	const int  WIDTH  = 5;
	const char NEWLINE = '\n';
	int area;
	
	area = LENGTH * WIDTH;
	cout << area;
	cout << NEWLINE;
	cout  <<  "Alt satıra geçildi.";
	return 0;
}
```
Output:
```
50
Alt satıra geçildi.
```
**Not:** Constants variable defining (tanımlama) için en uygun yöntem, büyük harf kullanmaktır. Örnek: LENGTH, WIDTH, NEWLINE

## Numeric Literals (Integer ve Floating-point Literals)

### Integer Literals
Bir **Integer Literal**, decimal, octal, hexadecimal constant olabilir. **base** ve **radix** kavramları, **prefix** (ön ek) kavramını belirtir. Binary için `0b` ya da `0B`, hexadecimal için `0x` ya da `0X`, octal için `0` prefix'lerini kullanırken, decimal için de hiçbir prefix kullanmayız.

**Binary Literals:** 0,1 (sadece C++20'de var.)
```cpp
int a = 0b1010
int a = 0B1010
```

**Octal Literals:** 0,1,2,3,4,5,6,7
```cpp
int a = 0174;  // No Error
int a = 0192; // Error: 9 octal sistemde yoktur.
```

**Decimal Literals:** 0,1,2,3,4,5,6,7,8,9
```cpp
int a = 562;  // No Error
int a = 0158; // Error: decimal sayılar 0 ile başlayamaz.
```

**Hexadecimal Literals:** 0,1,2,3,4,5,6,7,8,9,a,b,c,d,e,f(A,B,C,D,E,F)
```cpp
int a = 0x1fc8
int a = 0x1Fc8
int a = 0x1fC8
int a = 0x1FC8
```

**U ve L Postfix:** Bir integer literal ayrıca *unsigned* ve *long* için **U** ve **L** harflerinden oluşan bir **portfix**'e (son ek) sahip olabilir. Bu postfix için büyük ya da küçük harfle kullanılabilir. Bu U ve L postfix'leri basit ya da önemsiz bir şey değildir. Compiler'ın programı yorumlamasına etki eder. Örnekler:
```cpp
#include  <iostream>
using  namespace  std;

void func1(unsigned int x) {
	// işlemler
}

void func2(int x) {
	// işlemler
}

int  main() {
	f(3);  // f(int x)
	f(3u); // f(unsigned int x)
	return  0;
}
```
```cpp
30      // int
30U     // unsigned int
30u     // unsigned int
30L     // long int
30l     // long int
30UL    // unsigned long int
30ul    // unsigned long int
30ULL	// unsigned long long int
30ull	// unsigned long long int
```

### Floating-point Literals
Bir **floating-point literal** bir *integer part (tamsayı kısmı)*, bir *decimal point (integer ve fractional kısmı ayıran nokta)*, bir *fractional part (kesirli kısım)* ve bir *exponent part (üslü kısım)* kısımlarından oluşur. Floating-point literal, *decimal form* (3.14159) ya da *exponential form* (314159e-5L) şeklinde yazılabilir. Varsayılan floating-point tipi double olmakla birlikte sayı gösterimi float (F veya f) ve long double (L veya l) son ekleri ile de gösterilebilir. Dikkat edilmesi gereken yer, long double (L veya l) işaretinin double ile karıştırılmamasıdır.
```cpp
// Doğru Kullanım:
12.65f // 12.65 (float tipinde)
12.65F // 12.65 (float tipinde)
12.65l // 12.65 (long double tipinde)
12.65L // 12.65 (long double tipinde)

// Yanlış Kullanım:
510E // Illegal: incomplete exponent
210f // Illegal: no decimal or exponent
.e55 // Illegal: missing integer or fraction
```
**Not:**
```
12.65e2 = 1265.0 = 12.65*10^2
314159e-5L = 3.14159L = 314159*10^-5
```

## Boolean Literals
**true** ve **false** olmak üzere 2 boolean değer vardır ve bunlar standart C++ keyword'dür.

## Pointer Literals
C++11 standardı, başlangıç değeri sıfır olan **nullptr** adlı bir pointer (işaretçi) değer tanımlamıştır. Integer bir sayısal değer olan 0 veya **NULL** makrosunun kullanımı yerine nullptr değeri kullanılabilir.

## Character Literals
**Character Literals** *tek tırnak* içinde gösterilir. Character Literals, bir *character* **('x')**, bir *kaçış dizisi* **('\n')** veya *universal character* **('\u02C0')** olabilir. *Backslash'*dan **( \ )** sonra gelen belirli character'lerin özel anlamları vardır. Örneğin satır sonu **"\n"**, TAB **"\t"** anlamına gelir.
| Characters | ASCII Representation | ASCII Code | Escape Sequence |
|--|--|--|--|
| Newline | NL (LF) | 10 | \n |
| Horizotal tab | HT | 9 | \t |
| Vertical tab | VT | 11 | \v |
| Backspace | BS | 8 | \b |
| Carriage return | CR | 13 | \r |
| Formfeed | FF | 12 | \f |
| Alert | BEL | 7 | \a |
| Backslash character | \ | 92 | \\ |
| Question mark (Keyword) | ? | 63 | \? |
| Single quotation mark (Keyword) | ' | 39 | \' |
| Double quotation mark (Keyword) | " | 37 | \" |
| Octal number | ooo | -- | \ooo |
| Hexadecimal number | hhh | -- | \xhhh |
| NULL character | NUL | 0 | \0 |

## String Literals
**String Literals** *çift tırnak* içinde gösterilir. Bu Literal, **L** *(sadece büyük harf)* ile başlarsa *(L"merhaba" gibi)*, bu **wide character literal**'dır ve **wchar_t** olarak depolanır (stored). Aksi taktirde **narrow (dar) character literal**'dır *("merhaba" gibi)* ve **char** olarak saklanır. Bir string, Character Literals'e benzer character'ler içerir: Characters, Escape Sequences, Universal Characters.

**Not:** Aşağıdaki stringlerin hepsi aynı output'u verir:
```cpp
cout << "hello, dear" << endl; // Output: hello, dear

cout << "hello, \
dear" << endl; // Output: hello, dear

cout << "hello, " << "d" << "ear" << endl; // Output: hello, dear
```

### String değerle:
```cpp
"Test String"   // const char*
u8"Test String" // const char* , UTF-8 Encoded
u"Test String"  // const char16_t* , UTF-16 Encoded
U"Test String"  // const char32_t* , UTF-32 Encoded
L"Test String"  // const wchar_t*
```

### String değerler (`<string>` kullanımı sayesinde) `s` postfix ile birlikte:
```cpp
"Test String"s    // std::string
u8"Test String"s  // std::string
u"Test String"s   // std::u16string
U"Test String"s   // std::U32string
L"Test String"s   // std::wstring
```

### Raw String Değerler (`\` ve `"` için escape karakteri kullanmadan)
```cpp
R"("Test String")" // const char*
u8R"("Test String")" // const char* , UTF-8 Encoded
uR"("Test String")" // const char16_t* , UTF-16 Encoded
UR"("Test String")" // const char32_t* , UTF-32 Encoded
LR"("Test String")" // const wchar_t*
```
