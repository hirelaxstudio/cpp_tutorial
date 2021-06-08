# decision making statements (Karar verme ifadeleri)
Bir kod bloğunun, belli bir koşul sağlandığı taktirde çalışmasını istenildiğinde decision making statements (karar verme yapıları) kullanılır.

## `if` Statement
Bloğundaki kodları, kendisine tanımlanmış koşulun sağlanıp (`true`) sağlanmamasına (`false`) göre çalıştırır ya da çalıştırmaz. Syntax:
```cpp
if (Condition) {
    // Kodlar...
}
```
`Condition` kısmına `true`/`false`, `true`/`false` döndüren bir logic ifade ya da `true`/`false` anlamına gelen bir value tanımlanabilir. Önemli olan, `Condition` kısmına `true`/`false` anlamına gelen bir şey tanımlanmasıdır. Örnekler:
```cpp
if (true) {
		std::cout << "Worked 1\n";	
	}
	else {
		std::cout << "Not Worked 1\n";
	}

	if (false) {
		std::cout << "Worked 2\n";	
	}
	else {
		std::cout << "Not Worked 2\n";
	}

	if (1<2) {
		std::cout << "Worked 3\n";	
	}
	else {
		std::cout << "Not Worked 3\n";
	}

	if (2-2) {
		std::cout << "Worked 4\n";	
	}
	else {
		std::cout << "Not Worked 4\n";
	}
    char a;
	if (a) {
		std::cout << "Worked 5\n";	
	}
	else {
		std::cout << "Not Worked 5\n";
	}
```
**Output:**
```
Worked 1    
Not Worked 2
Worked 3
Not Worked 4
Not Worked 5
```
**Not:** Görüldüğü gibi `0` sayısı, boş character (char) gibi değerler `false` değerine karşılık gelmektedir.

## `if` - `else` Statement
Yukarıda da gördüğünüz gibi `else` statement, kendinden hemen önceki `if` statement'in çalışmaması durumunda çalışan bir statementtir. `else` statement'in çalışabilmesi için kendinden önceki `if` statement ile arasında herhangi bir kodun olmaması gerekiyor. Örnek:
```cpp
if (false) {
	std::cout << "Worked";	
}
int number = 2;
else { // Hata kodu: `error: 'else' without a previous 'if'`
	std::cout << "Not Worked";
}
```
**Output:**
```
Not Worked
```
Çalışan bir örnek:
```cpp
if (false) {
	std::cout << "Worked";	
}
else {
	std::cout << "Not Worked";
}
```
**Output:**
```
Not Worked
```

## `if` - `else if` - `else` Statement
`else if` statement, `else` statement gibi `if` statement çalışmazsa çalışan bir statementtir. `else` statement'den farkı, `Condition` tanımlayabilmenizdir. `else` statement tanımlama sınırınız bir olmasına karşın, `else if` statement'ten istediğiniz kadar tanımlayabilirsiniz. Örnek:
```cpp
if (false) {
	std::cout << "1. Worked";	
}

else if (false) {
	std::cout << "2. Worked";	
}

else if (true) {
	std::cout << "3. Worked";	
}

else {
	std::cout << "Not Worked";	
}
```
**Output:**
```
3. Worked
```

**Not:** C++'da, expression'lar ve statement'lar arasındaki boşluk bir anlam ifade etmediği için `else if` statement farklı şekillerde karşınıza çıkabilir. Örnek:
```cpp
if (false) {
	std::cout << "1. Worked";	
}

else if (true) {
	std::cout << "2. Worked";	
}
else {
	std::cout << "Not Worked";	
}
```
```cpp
if (false) {
	std::cout << "1. Worked";	
}

else
	if (true) {
		std::cout << "2. Worked";
}
else {
	std::cout << "Not Worked";	
}
```
Bu iki kullanım, birbirinden farklı görünse de aynı şeylerdir.

**Not:** `if`, `else if` ve `else` statement'ları, süslü parantezlerle block oluşturmadan da kullanılabilir. Örnek:
**1)**
```cpp
if (true)
	std::cout << "1. Worked";

else if (true)
	std::cout << "2. Worked";

else
	if (true)
		std::cout << "3. Worked";

else
	std::cout << "Not Worked";
```
**Output:**
```
1. Worked
```
**2)**
```cpp
if (false)
	std::cout << "1. Worked";

else if (true)
	std::cout << "2. Worked";

else
	if (true)
		std::cout << "3. Worked";

else
	std::cout << "Not Worked";
```
**Output:**
```
2. Worked
```
**3)**
```cpp
if (false)
	std::cout << "1. Worked";

else if (false)
	std::cout << "2. Worked";

else
	if (true)
		std::cout << "3. Worked";

else
	std::cout << "Not Worked";
```
**Output:**
```
3. Worked
```
**4)**
```cpp
if (false)
	std::cout << "1. Worked";

else if (false)
	std::cout << "2. Worked";

else
	if (false)
		std::cout << "3. Worked";

else
	std::cout << "Not Worked";
```
**Output:**
```
Not Worked
```
Buradaki en önemli nokta, bu statementleri süslü parantez olmadan bu şekilde kullanmak isterseniz, bloğuna sadece bir statement (`;` ile biten tek bir kod anlamında) ifade ekleyebilirsiniz. Yine de her ihtimale karşı kolaya kaçmak yerine süslü parentez kullanmak en iyisidir.

## `switch` statement
`switch` statement, bir variable'ı bir value list'e karşı eşitlik durumunu test etmek için kullanılabilir. Her value'nin sorgusunun yapıldığı yapıya `case` denir. Örnek:
```cpp
switch(expression) {
	case constant-expression:
		// kodlar...
		break; // Optional (İsteğe Bağlı Eklenebilir ya da Eklenmez)
	
	case constant-expression:
		// kodlar...
		break; // Optional (İsteğe Bağlı Eklenebilir ya da Eklenmez)
	.
	.
	.

	default: // Optional (İsteğe Bağlı Eklenebilir ya da Eklenmez)
		// kodlar...
		break; // Optional (İsteğe Bağlı Eklenebilir ya da Eklenmez)
```
Buradaki şeyleri teker teker açıklamak gerekirse:
- `expression`, `switch` statement'de kullanabilmek bir for-each uyumlu class ya da sabit tek bir object value olarak verilmelidir.
- `case`'lerde tanımlanan `constant-expression`'lardan herhangi biri `expression` ile eşleşirse, ilgili `case` çalışır. Bu `constant-expression`'lar `expression` ile aynı data type'a sahip olmalı ve `constant` ya da `literal` olmamalıdır.
- Bir `case` çalıştığında, `break` statement ile karşılaşana kadar kendinden sonraki `switch` kapsamındaki bütün kodları çalıştırır. Örneğin bir `case` çalışırsa, `break` statement ile karşılaşana kadar altındaki statementler de çalışır. Bu yüzden `break` statement kullanımı optional olsa da önemlidir çünkü `switch` statement, `break` statement ile karşılaşınca sonlanır.
- İstenilen sayıda `case` kullanılabilir.
- Hiçbir `case` çalışmazsa `default` çalışır. Bu yüzden `default`, `constant-expression` almaz.
- Bir `switch` statement'in hiçbir yerinde `break` statement kullanılmazsa bile, flow (programın akışı) o `switch` statement'in sonuna geldiğinde `switch` sonlanır (terminates). Yani `for` ya da `while` gibi loop davranışı sergilemez.
```cpp
int number;
std::cout << "Bir number gir: ";
std::cin >> number;
switch (number)
{
case 10:
	std::cout << "number is: 10" << std::endl;
	break;

case 20:
	std::cout << "number is: 20" << std::endl;
	break;

case 30:
	std::cout << "number is: 30" << std::endl;
	break;

default:
	std::cout << "number is not 10, 20 or 30" << std::endl;
	break;
}
```
**Output:**
```
Bir number gir: 10
number is: 10
```
**Not:** `case`'lerde variable initialization işlemi yapmaya çalışırsanız `crosses initialization` hatası alırsınız. Bu hatayı almamak için basitçe variable initialization işlemlerini `switch` statement'in dışında yapabilirsiniz. Konuyla alakalı daha ayrıntılı bilgiye ulaşmak için [tıklayınız](https://stackoverflow.com/questions/11578936/getting-a-bunch-of-crosses-initialization-error).

## Nested `if`, `else if`, `else` Statements
Basitçe, `if`, `else if`, `else` statement'ler nested olarak kullanılabilir. Örnek:
```cpp
if (true) {
	std::cout << "1. Worked\n";
	if (false) {
		std::cout << "2. Worked\n";
	}
	else {
		std::cout << "2. Not Worked\n";
	}
}
else {
	std::cout << "1. Not Worked\n";
}
```
**Output:**
```
1. Worked
2. Not Worked
```

## Nested `switch` Statements
Basitçe, `switch` statement nested olarak kullanılabilir. Örnek:
```cpp
int number;
std::cout << "Sayi gir: ";
std::cin >> number;
switch (number)
{
case 5:
	std::cout << "1. case 5 worked\n";
	break;

case 10:
	std::cout << "1. case 10 worked\n";
	switch (number)
	{
	case 5:
		std::cout << "2. case 5 worked\n";
		break;

	case 10:
		std::cout << "2. case 10 worked\n";
		break;

	case 15:
		std::cout << "2. case 15 worked\n";
		break;
	
	default:
		std::cout << "2. default 15 worked\n";
		break;
	}
	break;

case 15:
	std::cout << "1. case 10 worked\n";
	break;

default:
	std::cout << "1. default 15 worked\n";
	break;
}
```
**Output:**
```
Sayi gir: 5
1. case 5 worked

Sayi gir: 10
1. case 10 worked
2. case 10 worked

Sayi gir: 15
1. case 10 worked
```
Bazı özellikleri:
- En üstteki `switch`'e **enclosing**, onun kapsadığı diğer `switch`'lere **nested** denir.
- En fazla 256 tane nested `switch` statement tanımlanabilir.
- Nested `switch`'ler kendilerini kapsayan `switch`'lerin `expression`'larına erişebilirler (yukarıda görüldüğü gibi).
- Her `switch` kendi `expression`'undan sorumludur. Yani bir `switch`'in bloğundaki `case`'ler, sadece ilgili `switch`'in `expression`'unu tanırlar. Bu `case`'ler, başka `switch`'lerin ya da kendilerini kapsayan diğer `switch`'lerin `expression`'ları ile ilgilenmezler.

## Conditional `? :` Operator (Koşullu Operatör)
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