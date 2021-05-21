# Operators
Operator'ler, compiler'a belirli matematiksel veya logic işlemleri yapmasını söyleyen semboldür. C++ operator açısından zengindir. Aşağıdaki operator'lerin ana başlıkları verilmiştir.
- Arithmetic Operators
- Relational/Comparison Operators
- Logical Operators
- Bitwise Operators
- Assignment Operators
- Misc Operators

## Arithmetic Operators

### Addition Operator
`+` *(Addition)* operatörü, iki objeyi birbirine ekler. Bu değerler `int`, `float` ya da `double` gibi sayı data type'ında olursa normal toplama işlemi, `string` dat type'ında olursa birbirine ekleme işlemi yapar.
```cpp
int addition_operator = 100 + 50;
std::cout << addition_operator; // Output: 150
```

### Subtraction Operator
`-` *(Subtraction)* operatörü, iki `int`, `float` ya da `double` gibi sayı data type'ındaki değerleri birbirinden çıkarır.
```cpp
int addition_operator = 100 - 50;
std::cout << addition_operator << std::endl; // Output: 50
```

### Multiplication Operator
`*` *(Multiplication)* çarpma operatörü, iki `int`, `float` ya da `double` gibi sayı data type'ındaki değerleri birbiri ile çarpar. Bir `string` data type'ı herhangi bir decimal sayı ile çarpamazsın ama bir `char` data type'ı ile bir decimal değeri çarpabilirsiniz çünkü `char` data type'ın ASCII tablosunda decimal değerleri vardır.
```cpp
int multiplication_operator = 100 * 50;
std::cout << multiplication_operator << std::endl; // Output: 5000
```
```cpp
char a = 'a';
std::cout << a*2; // Output: 194 (97*2)
```

### Division Operator
`/` *(Division)* bölme operatörü, iki `int`, `float` ya da `double` gibi sayı data type'ındaki değerleri birbirine böler.
```cpp
int division_operator = 100 / 50;
std::cout << division_operator << std::endl; // Output: 2
```

### Modulus Operator
`%` *(Modulus)* operatörü, iki `int`, `float` ya da `double` gibi sayı data type'ındaki değerlerin birbirine bölümünden kalanı verir.
```cpp
int modulus_operator = 100 % 49;
std::cout << modulus_operator << std::endl; // Output: 2
```

### Increment Operator
`++` *(Increment)* operatörü, bir `int`, `float` ya da `double` gibi sayı data type'ındaki bir değerin değerlerini 1 arttırır.
```cpp
int degeri_1_arttirma_operatoru = 100;
++degeri_1_arttirma_operatoru;
std::cout << degeri_1_arttirma_operatoru << std::endl; // Output: 101
```

### Decrement Operator
`++` *(Decrement)* operatörü, bir `int`, `float` ya da `double` gibi sayı data type'ındaki bir değerin değerlerini 1 azaltır.

**Not:** `++a` ile `a++` farklı şeylerdir. `++a`, "önce `a`'nın değerini bir arttır, sonra `a`'yı ekrana bastır."; `a++`, "önce `a`'nın değerini bastır, sonra `a`'nın değerini bir arttır." demektir. Aynısı `--a` ve `a--` için de geçerlidir. Bu olay, bu operatör farklı operatörlerle birlikte kullanıldığında önem kazanır (örneğin for ve while döngülerinde). Aksi taktirde tek başına `a++`; veya `++a`; şeklindeki kullanımın pek bir esprisi yoktur.

**Not:** Önce gelen eke **prefix** (ön ek), sonra gelen eke **postfix** (son ek) denir. `++a`'daki `++` prefix, `a++`'daki `++` ise postfix'dir.

**Not:** `++` ve `--` ifadesi sadece variable'ler için kullanılabilir. `--5` yazamazsın ama `int x = 5;` tanımladıktan sonra `--x;` yapabilirsin.

## Relational/Comparison Operators
Karşılaştırma operatörleri, iki değeri karşılaştırmak için kullanılır. Sonuç **true (1)** ya da **false (0)** olabilir.

### `==` Operator
İki ifade birbirine eşitse `true` (`1`), eşit değilse `false` (`0`) verir.
```cpp
int a = 10, b = 10;
std::cout << (a == b) << std::endl; // Output: 1
```

### `!=` Operator
İki ifade birbirine eşit değilse `true` (`1`), eşitse `false` (`0`) verir.
```cpp
int a = 10, b = 20;
std::cout << (a != b) << std::endl; // Output: 1
```

### `>` Operator
Birinci ifade İkinci durumdan büyükse `true` (`1`), eşit ya da küçükse `false` (`0`) verir.
```cpp
int a = 20, b = 10;
std::cout << (a > b) << std::endl; // Output: 1
```

### `<` Operator
Birinci ifade İkinci durumdan küçükse `true` (`1`), eşit ya da büyükse `false` (`0`) verir.
```cpp
a = 10, b = 20;
std::cout << (a < b) << std::endl; // Output: 1
```

### `>=` Operator
Birinci ifade İkinci durumdan büyük ya da eşitse `true` (`1`), küçükse `false` (`0`) verir.
```cpp
a = 10, b = 5, c = 10;
std::cout << (a >= b) << std::endl; // Output: 1
std::cout << (a >= c) << std::endl; // Output: 1
```

### `<=` Operator
Birinci ifade İkinci durumdan küçük ya da eşitse `true` (`1`), büyük `false` (`0`) verir.
```cpp
a = 10, b = 20, c = 10;
std::cout << (a <= b) << std::endl; // Output: 1
std::cout << (a <= c) << std::endl; // Output: 1
```

## Logical Operators
Logical operator'ler, kendilerine verilen ifadelerin boolean değerlerine göre bir değer döndürür.

### Logical AND (`&&`) Operator
| `A` | `B` | `A && B` |
|--|--|--|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

`int x = 5;` için:
| Operator | İşlem | Output | Anlamı |
|--|--|--|--|
| `&&` | `(x < 6) && (x < 4)` | 0 | false |

### Logical OR (`||`) Operator
| `A` | `B` | `A OR B` |
|--|--|--|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

`int x = 5;` için:
| Operator | İşlem | Output | Anlamı |
|--|--|--|--|
| `OR` | `(x < 6) OR (x < 4)` | 1 | true |

### Logical NOT (`!`) Operator
| `A` | `!B` | 
|--|--|
| 0 | 1 |
| 0 | 1 |
| 1 | 0 |
| 1 | 0 |

`int x = 5;` için:
| Operator | İşlem | Output | Anlamı |
|--|--|--|--|
| `!` | `!( (x < 6) && (x < 4) )` | 1 | true |

## Bitwise Operators
Bitwise operatörleri, bitler üzerinde işlem yapmamızı sağlar. Bitwise Operatörleri:
- `&` Bitwise AND Operator
- `|` Bitwise OR Operator
- `^` Bitwise XOR Operator
- `~` Bitwise Complement Operator
- `<<` Bitwise Shift Left Operator
- `>>` Bitwise Shift Right Operator

### Bitwise AND Operator
Bitsel AND `&` operatörü, her iki işlenen de 1 ise 1 döndürür. Aksi takdirde, 0 döndürür. Mantıktaki **"ve"** bağlacına benzer.
| `A` | `B` | `A & B` |
|--|--|--|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |
```
12 = 00001100 (In Binary)
25 = 00011001 (In Binary)

00001100 & 00011001 = 00001000

8 = 00001000 (In Binary)
```
Yukarıdaki işlemin C++'da karşılığı:
```cpp
int bao_1 = 12; // bao_1: bitsel_and_operatoru_1;
int bao_2 = 25; // bao_2: bitsel_and_operatoru_2

cout << "bao_1 = " << bao_1 << endl;
cout << "bao_2 = " << bao_2 << endl;
cout << "bao_1 & bao_2 = " << (bao_1 & bao_2) << endl;
```

### Bitwise OR Operator
Bitsel OR `|` işlenenlerden en az biri 1 ise operatör 1 döndürür. Aksi takdirde 0 döndürür. Mantıktaki **"veya"** bağlacına benzer.
| `A` | `B` | `A OR B` |
|--|--|--|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |
```
12 = 00001100 (In Binary)
25 = 00011001 (In Binary)

00001100 | 00011001 = 00011101

29 = 00011101 (In Binary)
```
Yukarıdaki işlemin C++'da karşılığı:
```cpp
int boo_1 = 12; // boo_1: bitsel_or_operatoru_1;
int boo_2 = 25; // boo_2: bitsel_or_operatoru_2

cout << "boo_1 = " << boo_1 << endl;
cout << "boo_2 = " << boo_2 << endl;
cout << "boo_1 | boo_2 = " << (boo_1 | boo_2 ) << endl;
```

### Bitwise XOR Operator:
Bitsel XOR `^` operatörü, işlenenler birbirinden farklıysa 1, aynıysa 0 döndürür. Mantıktaki **"ya da"** bağlacına benzer.
| `A` | `B` | `A ^ B` |
|--|--|--|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |
```
12 = 00001100 (In Binary)
25 = 00011001 (In Binary)

00001100 ^ 00011001 = 00010101

21 = 00010101 (In Binary)
```
Yukarıdaki işlemin C++'da karşılığı:
```cpp
int bxoo_1 = 12; // bxoo_1: bitsel_xor_operatoru_1;
int bxoo_2 = 25; // bxoo_2: bitsel_xor_operatoru_2

cout << "bxoo_1 = " << bxoo_1 << endl;
cout << "bxoo_2 = " << bxoo_2 << endl;
cout << "bxoo_1 | bxoo_2 = " << (bxoo_1 | bxoo_2 ) << endl;
```

### Bitwise Complement Operator
Bu operatör sadece bir operand üzerinde çalışır. `~` tanımlayıcısına sahiptir. 1'i 0'a, 0'ı 1'e dönüştürür. `N` adında bir operant olsun. `N` operantı *bitwise complement operatörü*nden etkilenirse `-(N + 1)` değerine dönüşür Örneğin:
```
-36 = -(35+1)

35 = 00100011 (In Binary)
~ 00100011 = 11011100
-36 = 11011100 (In Binary)
```

### Binary Left Shift Operator
Basitçe, Bir binary sayıyı sola kaydırır. Yani '`00010110` binary sayısına eşit bir N variable, `N << 2` işleminden sonra `01011000` dönüşüyor. Biraz daha teknik açıklamak gerekirse, 22 decimal sayısının binary versiyonu `00010110`'dir. `N << 2` işleminden sonra 22 (`N`),  88'e (`N` * (2^2^)) dönüşür. Yani `00010110` binary sayısı, `01011000` binary sayısına dönüştürüyor.
```cpp
unsigned char lso = 22 ; // 22 = 00010110 (In Binary)
std::cout << (lso << 2); // Output: 88 (01011000 [In Binary])
```

### Binary Right Shift Operator
Binary Left Shift Operator'e benzer bir şekilde çalışır. Farkı, sola değil sağa kaydırmasıdır. Yani `00100000` binary sayısına eşit bir N variable, `N >> 2` işleminden sonra `00001000` dönüşüyor. Biraz daha teknik açıklamak gerekirse, 32 decimal sayısının binary versiyonu `00100000`'dir. `N >> 2` işleminden sonra 32 (`N`),  8'e (`N` / (2^2^)) dönüşür. Yani `00100000` binary sayısı, `00001000` binary sayısına dönüştürüyor.
```cpp
unsigned char lro = 32; // 32 = 00001100 (In Binary)
std::cout << (lro >> 2); // Output: 8 (00001000 [In Binary])
```
**Not:** assignment operatör kullanarak `N <<= 2` tarzı bir işlem yapmadığınız sürece `N`'nin orjinal değeri değişmez.
**Not:** Bir decimal sayı üzerinde binary shift operatör kullanırsanız, işlemler binary form'da yapılsa bile output decimal formda verilir. Yukarıda örnekler var.

#### Shift Operator hakkında notlar:
- Negatif sayılar için Binary Left Shift Operator ve Binary Right Shift Operator kullanılmamalıdır. Operand'lardan birisi negatif sayıysa, result (sonuç) her türlü *undefined (tanımsız)* olur.

- Bir sayı, integer data type'ın tutabileceği data boyutundan *(size of integer [32 bit, 64 bit etc.])* daha büyük bir shift operatör işlemine sokulursa, sonuç *undefined* olur. Örneğin, integer'lar 32 bit kullanılarak depolanıyorsa (stored), `1 << 33` işleminin sonucu *undefined'dır (tanımsızdır)*. Böyle bir şey yaparsanız `warning: left shift count >= width of type` hata mesajı alabilirsiniz.

- Her veri tipinin memory'de (bellekte) kapladığı bir yer vardır. Daha büyük değerler üzerinde shift operatör kullanabilmek için 64 bit yer kaplayan 'Unsigned long long' kullanılır. Bu da normal 'int' den daha fazla bit tutabilmesini sağlar.

- The left-shift by 1 and right-shift by 1 are equivalent to the product of first term and 2 to the power given element(1<<3 = 1*pow(2,3)) and division of first term and second term raised to power 2 (1>>3 = 1/pow(2,3)) respectively. As mentioned in point 1, it works only if numbers are positive.

- The left-shift of 1 by i is equivalent to 2 raised to power i. As mentioned in point 1, it works only if numbers are positive.

## Assignment Operators

### Simple assignment operator (`=`)
Sağ taraftaki operantı sol taraftaki operanta (örneğin bir variable'a) atar (assignment).
```cpp
int vrb_1 = 1, vrb_2 = 2, vrb_3 = 3;
vrb_1 = vrb_2 + vrb_3;
std::cout << vrb_1 << std::endl; // Output: 5
```

### Add AND assignment operator (`+=`)
Kısaca `a += b` işlemi ile matematiksel `a = a + b` işlemi aynı mantıkta çalışır.
```cpp
int vrb_1 = 1, vrb_2 = 2;
vrb_1 += vrb_2; // vrb_1 = vrb_1 + vrb_2
std::cout << vrb_1 << std::endl; // Output: 3
```

### Subtract AND assignment operator (`-=`)
Kısaca `a -= b` işlemi ile matematiksel `a = a - b` işlemi aynı mantıkta çalışır.
```cpp
int vrb_1 = 1, vrb_2 = 3;
vrb_2 -= vrb_1; // vrb_2 = vrb_2 - vrb_1
std::cout << vrb_2 << std::endl; // Output: 2
```

### Multiply AND assignment operator (`*=`)
Kısaca `a *= b` işlemi ile matematiksel `a = a * b` işlemi aynı mantıkta çalışır.
```cpp
int vrb_1 = 2, vrb_2 = 3;
vrb_1 *= vrb_2; // vrb_1 = vrb_1 * vrb_2
std::cout << vrb_1 << std::endl; // Output: 6
```

### Divide AND assignment operator (`/=`)
Kısaca `a /= b` işlemi ile matematiksel `a = a / b` işlemi aynı mantıkta çalışır.
```cpp
int vrb_1 = 4, vrb_2 = 2;
vrb_1 /= vrb_2; // vrb_1 = vrb_1 / vrb_2
std::cout << vrb_1 << std::endl; // Output: 2
```

### Modulus AND assignment operator (`%=`)
`a %= b` işlemi, `a = a % b` işlemi ile aynı mantıkta çalışır. Bir sayının başka bir sayıya bölümünden kalanı verir.
```cpp
int vrb_1 = 4, vrb_2 = 2;
vrb_1 %= vrb_2; // vrb_1 = vrb_1 % vrb_2
std::cout << vrb_1 << std::endl; // Output: 0

vrb_1 = 4, vrb_2 = 3;
vrb_1 %= vrb_2; // vrb_1 = vrb_1 % vrb_2
std::cout << vrb_1 << std::endl; // Output: 1
```

### Left shift AND assignment operator (`<<=`)
`a <<= b` işlemi, `a = a << b` işlemi ile aynı mantıkta çalışır. *Binary Left Shift Operator*'ün yaptığı işi yapar.
```cpp
unsigned char lso = 22; // 22 = 00010110 (In Binary)
lso <<= 2
std::cout << lso; // Output: 88 (01011000 [In Binary])
```

### Right shift AND assignment operator (`>>=`)
`a >>= b` işlemi, `a = a >> b` işlemi ile aynı mantıkta çalışır. *Binary Right Shift Operator*'ün yaptığı işi yapar.
```cpp
unsigned char lso = 32; // 32 = 00100000 (In Binary)
lso >>= 2
std::cout << lso; // Output: 8 (00001000 [In Binary])
```

### Bitwise AND assignment operator (`&=`)
`a &= b` işlemi, `a = a & b` işlemi ile aynı mantıkta çalışır. *Bitwise AND Operator*'ün yaptığı işi yapar.
```cpp
unsigned char lso = 12; // 12 = 00001100 (In Binary)
lso &= 25 // 25 = 00011001 (In Binary)
std::cout << lso; // Output: 8 (00001000[In Binary])
```

### Bitwise inclusive OR assignment operator (`|=`)
`a |= b` işlemi, `a = a | b` işlemi ile aynı mantıkta çalışır. *Bitwise inclusive OR Operator*'ün yaptığı işi yapar.
```cpp
unsigned char lso = 12; // 12 = 00001100 (In Binary)
lso |= 25 // 25 = 00011001 (In Binary)
std::cout << lso; // Output: 29 (00011101 [In Binary])
```

### Bitwise exclusive OR assignment operator (*^=*)
```cpp
unsigned char lso = 12; // 12 = 00001100 (In Binary)
lso ^= 25 // 25 = 00011001 (In Binary)
std::cout << lso; // Output: 29 (00010101 [In Binary])
```

## Misc Operators

### `sizeof` Operator
`sizeof` operatör, bir variable'ın veya data type'ın byte türünden boyutunu verir. Class'lar, structure'lar, union'lar ve diğer herhangi user defined data type'ın (kullanıcı tanımlı veri türünün) boyutunu elde etmek için kullanılabilir.
```cpp
std::cout << "Size of char : " << sizeof(char) << std::endl
```
**Output:** `Size of char : 1`

### Conditional `? :` Operator (Koşullu Operatör)
`Exp1 ? Exp2 : Exp3;` syntax yapısına sahiptir. `Exp1` içinde yer alan koşul değerlendirilir (evaluated), koşul doğru (true) ise `Exp2`, koşul yanlış (false) ise `Exp3` return edilir. `Exp1 ? Exp2 : Exp3;` yapısındaki `?` işaretinin sipesifik bir anlamı yoktur. ` ? : ` yapısı **Ternary operator** olarak bilinir.

**Ternary operator (short if...else) (Üçlü Operatör)**, `data_type variable = (condition) ? expressionTrue : expressionFalse;` syntax yapısına sahiptir. Aşağıda mantığını anlamanıza yardımcı olacak 2 örnek vardır. Bu örneklerden birisi *if...else statement* kullanılarak oluşturulmuştur. Diğeri ise *Ternary operator* kullanılarak oluşturulmuştur. Çalışma mantıkları tamamen aynıdır.
```cpp
// if...else statement
int veb = 20;
if (vrb< 18) {
	std::cout << "vrb 18'den bütüktür.";
}
else {
	std::cout << "vrb 18'den bütük değildir.";
}
```
```cpp
// Ternary operator
int vrb = 20;
std::string result = (vrb < 18) ? "vrb 18'den bütüktür." : "vrb 18'den bütük değildir."
std::cout << result;
```
**Not:** `?` işaretinden sonra illa bir string değer tanımlamak zorunda değilsiniz. Matematiksel bir işlem, logic bir ifade veya bir fonksiyon da tanımlayabilirsiniz. Maksat, return edilen değerin `data_type variable = (condition) ? expressionTrue : expressionFalse;` syntax yapısındaki `data type` kısmında belirtilen data type ile uyumlu olmasıdır. Örneğin yukarıdaki örnekte, `result` variable'ı `string` data type'ına sahip ve return edilen değerler de `string` data type'ında olduğu için sıkıntı çıkmıyor.

### Comma Operator (`,`)
Comma Operator'ün (virgül operatörü) amacı, birbirinden farklı ifadeleri bir araya getirmektir. Virgülle ayrılmış işlemler **soldan sağa** gerçekleşir. Örnek:
```cpp
	int  a, b = 10;
	
//  a = b++;      // Output: 10     // 1. Satır
//  a = b + 100;  // Output: 111    // 2. Satır
//  a = 999 + b;  // Output: 1010   // 3. Satır
	a = (b++, b + 100, 999 + b);    // 4. Satır
	
	std::cout << a << std::endl; // Output: 1010
```
Dördüncü satırda yapılan işlemin açılımı sırasıyla birinci, ikinci ve üçüncü satırlarda verilmiştir.

### Member (dot & arrow) Operators
"." (dot) ve "->" (arrow) operatörü, classes, structures ve unions'a individual members (kısaca member'larına) referans vermek (erişmek) için kullanılır. Sadece farklı senaryolar için kullanılır. C++'da class, struct ve onion olarak declare edilen türler "class type" olarak kabul edilir. (Class ve pointer öğrenince tekrar bak)

### Casting Operators
`cast`, bir data type'ı diğerine dönüştürmeye (convert) zorlayan özel bir operatördür. *Type Casting* (tür dönüşümü) dediğimiz olay bununla yapılıyor. Yani, `float` bir variable'ı `double`'a dönüştürmek için bu işlemi yapmak zorundasınız. O variable'ı yeniden `double a;` diye declare etmek programı bozabilir. Çünkü declare ettiğin bu variable'ı kullanabilmek için define etmen de gerekiyor. Syntax'ı `(type_name) expression` şeklindedir. Örnek:
```cpp
int a = 17, b = 5;
double result;
result = (double) a / b;
std::cout << result << std::endl; // Output: 3.400000
```
Burada önce `a`, `double` data type'ına dönüştürülür, sonra bölme işlemi yapılır. Buradan cast operatörünün bölme işleminden daha öncelikli olduğu sonucunu çıkarabilirsiniz. Bunun gibi type casting işlemleri genellikle compiler tarafından otomatik olarak yapılır ama iyi bir program oluşturmak için spesifik olarak kendiniz yapmanız daha uygundur.

#### Integer Promotion
Integer promotion (integer yükseltme), `int` veya `unsigned int`'den küçük integer type value'lerin `int` veya `unsigned int` type'a dönüştürüldüğü (convert edildiği) süreçtir (process'dir).
```cpp
int vrb_1 = 17;   // 17
char vrb_2 = 'c'; // 99
int toplam = vrb_1 + vrb_2;
std::cout << toplam; // Output: 116
```
Burada `toplam` output'unun 116 olmasının sebebi, compiler toplama işlemi yapmadan önce `vrb_2`'ye **integer promotion** yapıyor ve `c`'nin değeri ASCII'deki decimal değerine dönüştürülüyor.

#### Usual Arithmetic Conversion
Usual arithmetic conversion işlemi, value'leri ortak bir type'a dönüştürme işlemidir. Compiler ilk olarak integer promotion işlemini yapar. Hala farklı data type'lar varsa, 1'den 8'e doğru:
1) int
2) unsigned int
3) unsigned long int
4) signed long long int
5) unsigned long long int
6) float
7) double
8) long double

sırasını takip ederek dönüştürme işlemini yapar. Usual arithmetic conversion işlemi, *assignment* ve *logical* operatörler için gerçekleştirilemez. Bu dönüşüm işleminin mantığı için bir örnek vereyim: Yukarıdaki `toplam` variable'ı, `int` data type'ında output verir. Bunu `float` yapmak şu yapıyı kullanabilirsiniz için:
```cpp
int vrb_1 = 116;
vrb_1 = (float) vrb_1;

std::cout << vrb_1; // Output: 116
```
Yukarıdaki `toplam = (float) toplam;` işleminde, `toplam` variable'ını `float` data type'ına çevirip tekrar `toplam` variable'a atıyor. Ama `toplam` variable'ı daha önce `ìnt` data type'ı olarak declare edildiği için `(float) toplam` value'su tekrardan `int` data type'ına dönüştürülür ve sonuçta `toplam` variable'ı eski `int` haline geri dönmüş oluyor. Bunu sorunla karşılaşmamak için value'yu farklı bir variable'a atayın. Örnek:
```cpp
double vrb_1 = 116.16542;
int vrb_2;
vrb_2 = (int) vrb_1;

cout << vrb_2; // Output: 116
```
Yukarıdaki işlemde, `vrb_1`'in değeri `double` olarak kalırken, `vrb_2`'ye `vrb_1`'in `int` versiyonu atanır. Eğer sadece, bir variable'ın value data type'ını değiştiri bastırmak istiyor ve hiçbir variable'ı değiştirmek veya ekstra variable eklemek istemiyorsanız şunu kullanabilirsiniz:
```cpp
double vrb_1 = 116.16542;

cout << (int) vrb_1; // Output: 116
```

#### C++'ın Desteklediği Diğer Casting Operator'leri
Önce iki kavramdan bahsedelim:
- **Base Class:** Derived Class'ların türetildiği base (ana) class'tır. Base class'ı devralan (inherit) class, base class'ın tüm member'larına ve bası ek özelliklerine sahip olabilir. Derived class'ın nesnesi, base class'ın member'larını ve memeber function'larını devralabilir (inherit). Base class'a **parent class** ya da **superclass**'da denir.

- **Derived Class:** Mevcut bir class'dan oluşturulan class'tır. Derived Class, bir base class'ın bütün members ve member functions'ını devralabilir (inherit). Derived class, base class'dan daha işlevsel (functionality) olabilir ve base class'a kolayca erişebilir. Derived Class'a **child class** veya **subclass**'da denir. Genellikle **subclass** kullanılır.

| Base Class | Derived Class |
|--|--|
| subclasses'a inherit (devralmak) verir. | base class'dan inherit (devralmak) alır. |
| parent class veya superclass olarak bilinir. | child class veya subclass olarak bilinir. |
| Derived Class'ın properties (özellikler) ve methods (yöntemler) inherit (devralmak) alamaz. | Base Class'in properties (özellikler) ve methods (yöntemler) inherit (devralmak) alır. |

**Syntax:**
```cpp
class base_classname
{
	// members....
	// member function
}
  
class derived_classname : public base_classname
{
	// members....
	// member function
}
```
**Not:** Bir function **override** olduğunda, teknik olarak `override` ya da `virtual` yazmaya gerek yoktur. Original base class (orjinal temel class) declare etmek, onu sanal olarak işaretlemek (mark) için `virtual` keyword'üne ihtiyaç duyar.

**`override`, `virtual`, `abstract` keyword'leri:** Overriding, bir class'a ait bir method'un, o class'dan türetilmiş bir subclass içerisinde aynı isimli bir method tanımlanarak, bu method'un base class'daki method'un yerine geçirmeye denir. Bu işlem, bir method'un aynı class'dan türetilmiş farklı subclass'larda farklı işlere yaramasını sağlar. subclass'daki method'un adından önce `override` anahtar sözcüğü eklenerek base class'daki method geçersiz kılınır. Bu işlem sonucunda base class'daki method aynı kalır, subclass'daki değişir. Burada dikkat edilmesi gereken nokta, iki method'un da aynı erişilebilirlik derecesine sahip olması gerekir ve bu erişilebilirlik derecesi `private` olamaz. Bir method'u geçersiz kılmak (override) için önce o method'un geçersiz kılınmasına izin verilmesi gerekir. Bunun için iki yol vardır: `virtual` ve `abstract` keyword'leri.

`virtual` keyword'ü, base class'daki method'un override edilmesine izin veririr. `abstract` keyword'ü, base class'daki method'un override işlemini zorunlu kılar. Base class'daki method'un `abstract` olarak tanımlanması için base class'ın da `abstract` olması gerekir ve `abstract` method'lar sadece declaration (bildirim) olarak tanımlanır. Implementation (uygulama) kısmı eklenmez ve bu kısım subclass'daki method'lara bırakılır. Eğer subclass ve method'ları `abstract` ise, `override` işlemi zorunlu değildir fakat daha sonra tekrar türetilip `override` edilmesi gerekir. Türetilmiş ve `override` edilmiş bir method, herhangi bir keyword eklemeden tekrar `override` edilebilir. Bunu engellemek için `sealed` keyword'ü kullanılır. Bu keyword, sadece `override` edilmiş method'larda işe yarar ve o method'un tekrar `override` edilmesini engeller. Örnekler:
```cpp
public abstract class  vehicle  // Bu base class olarak tanımlanmışdır.
{
	public int wheels;
	public abstract void  Definition();
	public void  NoOfWheels(int w)
	{
		wheels = w;
	}
	public abstract void  WheelExp();
}
 
  
public class  bike : vehicle // vehicle base class'dan üretilmiş Subclass
{
	public override void  Definition()
	{
		Console.WriteLine("This is a bike.");
	}
  
	new public void  NoOfWheels(int w)
	{
		wheels = 2;
	}
  
	public sealed override void  WheelExp()
	{
		Console.WriteLine("It has 2 wheels.");
	}
}
```
Burada `WheelExp` ve `NoOfWheels` method'ları `vehicle` class'dan farklıdır. Ayrıca `WheelExp` class'ı `sealed` anahtar kelimesi ile geçersiz kılma işlemine kapalı hale getirilmiştir.
```cpp
public class  car : vehicle // vehicle base class'dan üretilmiş Subclass
{
	public override void  Definition()
	{
		Console.WriteLine("This is a car.");
	}
  
	new public void  NoOfWheels(int w)
	{
		wheels = 4;
	}
  
	public sealed override void  WheelExp()
	{
		Console.WriteLine("It has 4 wheeels.");
	}
}
  
public class  pickup : car // car subclass'dan üretilmiş Subclass
{
	public override void  Definition()
	{
		Console.WriteLine("This is a pickup.");
	}
}
```
Örnekte de görüldüğü gibi `Definition` method'u, `override` edilmiş bir metod olduğu için, `virtual` veya `abstract` anahtar kelimelerine ihtiyaç duyulmadan geçersiz kılınmıştır. Ek bilgi için [tıklayınız](https://www.fluentcpp.com/2020/02/21/virtual-final-and-override-in-cpp/).

**`const_cast<type>` (expr):** The const_cast operator is used to explicitly override const and/or volatile in a cast. The target type must be the same as the source type except for the alteration of its const or volatile attributes. This type of casting manipulates the const attribute of the passed object, either to be set or removed.

**`dynamic_cast<type>` (expr):** The dynamic_cast performs a runtime cast that verifies the validity of the cast. If the cast cannot be made, the cast fails and the expression evaluates to null. A dynamic_cast performs casts on polymorphic types and can cast a A* pointer into a B* pointer only if the object being pointed to actually is a B object.

**`reinterpret_cast<type>` (expr):** The reinterpret_cast operator changes a pointer to any other type of pointer. It also allows casting from pointer to an integer type and vice versa.

**`static_cast<type>` (expr):** The static_cast operator performs a nonpolymorphic cast. For example, it can be used to cast a base class pointer into a derived class pointer.

#### Pointer Operators
Pointer, bir variable veya bir object'in bellek adresini tutan bir variable'dir. Bir pointer, başka bir pointer'ı da tutabilir. "`&` ve `*`  olmak üzere 2 pointer operatör vardır. `&` adresini alır, `*` da tutulan adresin gösterdiği veriyi verir. `&` operatörü, diğer unary (tekli) operatörlerle aynı öncelik sırasına (precedence) sahip olduğu için işlemler **sağdan sola** yapılır. Örnek:
```cpp
int vrb; // vrb: variable
int *ptr; // ptr: pointer
int val; // val: value
  
vrb = 3000;
ptr = &vrb;
val = *ptr;
  
std::cout << "Value of vrb :" << vrb << std::endl; // Value of vrb :3000
std::cout << "Value of ptr :" << ptr << std::endl; // Value of ptr :00B9F9B8
std::cout << "Value of val :" << val << std::endl; // Value of val :3000
```

#### Operators Precedence (operatör öncelik sırası)
Aşağıdaki tabloda öncelik sırası **en yüksekten en düşüğe** şeklinde **yukarıdan aşağıya doğru** sıralanmıştır. Yani *Postfix* en yüksek önceliğe sahip olanlardır ve aşağıya doğru öncelik sırası azalır.
| Category | Operator | Associativity |
|--|--|--|
| Postfix | `()`, `[]`, `->`, `.`, `++`, `--` | Soldan Sağa |
| Unary | `+`, `-`, `!`, `~`, `++`, `--`, `(type)`, `*`, `&`, `sizeof` | Sağdan Sola |
| Multiplicative | `*`, `/`, `%` | Soldan Sağa |
| Additive | `+`, `-` | Soldan Sağa |
| Shift | `<<`, `>>` | Soldan Sağa |
| Relational | `<`, `<=`, `>`, `>=` | Soldan Sağa |
| Equality | `==`, `!=` | Soldan Sağa |
| Bitwise AND | `&` | Soldan Sağa |
| Bitwise XOR | `^` | Soldan Sağa |
| Bitwise OR | `Bitwise OR Operator` | Soldan Sağa |
| Logical AND | `&&` | Soldan Sağa |
| Logical OR | `Logical OR Operator` | Soldan Sağa |
| Conditional | `? :` | Sağdan Sola |
| Assignment | `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `>>=`, `<<=`, `&=`, `^=`, `Bitwise inclusive OR assignment operator` | Sağdan Sola |
| Comma | `,` | Soldan Sağa |

**Not:** MarkDown tablo oluşturma azizlikleri yüzünden yukarıdaki tabloda bazı operatörlerin sadece isimlerini yazabildim. O operatörlerin işaretleri sırasıyla: Bitwise OR Operator (`|`), Logical OR Operator (`||`), Bitwise inclusive OR assignment operator (`|=`).
