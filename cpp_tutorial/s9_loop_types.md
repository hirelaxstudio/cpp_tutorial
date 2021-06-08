# Loop Types
C++'da kodlar yukarıdan aşağıya doğru okunur. Bir kod parçasının birden fazla kez okunması istenildiğinde de **Loop Types** kullanılır.

## `while` Loop
`(Condition)` doğru (`true`) olduğu sürece tekrarlanan loop çeşitidir. `(Condition)`'a, boolean bir değeri ifade edebilecek herhangi bir expression (örneğin logic ifadeler ya da zero, non-zero ifadeler) ya da direkt `true` - `false` gibi boolean bir değer girilebilir. `(Condition)` doğru (`true`) olunca loop sonlanır. Syntax:
```cpp
while(condition) {
    // Kodlar...
}
```
**Örnek:**
```cpp
int number = 0;
	std::cout << "number: ";
	while (number < 5) {
		std::cout << number << " ";
		number += 1;
	}
```
**Output:**
```
number: 0 1 2 3 4
```

## `do...while` Loop
while loop ile benzer mantıkta çalışır. While loop önce `(Condition)` kontrol edip sonra bloğundaki işlemleri yaparken, do...while, önce bloğundaki işlemleri yapıp sonra `(Condition)` kontrol eder. Bu yüzden while loop'un aksine en başta bir kere execute edilmesi (çalışması) garantidir. Syntax:
```cpp
do {
	//kodlar...
} while( condition );
```
**Örnek:**
```cpp
int number = 0;
	std::cout << "number: ";
	do {
		std::cout << number << " ";
		number += 1;
	} while (number < 5)
```
**Output:**
```
number: 0 1 2 3 4
```
**Dikkat:** while loop'un `(Condition)` kısmında kullanılan loop control variable'ları olan `i++` ve `++i`, birbirinden farkı sonuçlar doğurur. Örnek:
```cpp
int i = 1;
	int cnt = 7;
	char days[][10] = { "Pazartesi", "Sali", "Carsamba", "Persembe",
						"Cuma", "Cumartesi", "Pazar" };
	do {
		std::cout << "Index: " << i << "   Sira: " << i + 1 << "   Day: " << days[i] << std::endl;
	} while (i++ < cnt);
```
**Output:**
```
Index: 1   Sira: 2   Day: Sali    
Index: 2   Sira: 3   Day: Carsamba
Index: 3   Sira: 4   Day: Persembe
Index: 4   Sira: 5   Day: Cuma
Index: 5   Sira: 6   Day: Cumartesi
Index: 6   Sira: 7   Day: Pazar
Index: 7   Sira: 8   Day:
```
Fazladan bir kere daha çalışmasının sebebi, loop control variable'ı `i++` olarak kullanınca compiler önce `(i < cnt)` işlemini, sonra `i += 1` işlemini yapar. Array'ın 7. index'inde bir şey tanımlı olmadığı için de `Day:` kısmı ya boş ya da garip semboller içeren bir text olacaktır.
```cpp
int i = 1;
	int cnt = 7;
	char days[][10] = { "Pazartesi", "Sali", "Carsamba", "Persembe",
						"Cuma", "Cumartesi", "Pazar" };
	do {
		std::cout << "Index: " << i << "   Sira: " << i + 1 << "   Day: " << days[i] << std::endl;
	} while (++i < cnt);
```
**Output:**
```
Index: 1   Sira: 2   Day: Sali
Index: 2   Sira: 3   Day: Carsamba
Index: 3   Sira: 4   Day: Persembe
Index: 4   Sira: 5   Day: Cuma
Index: 5   Sira: 6   Day: Cumartesi
Index: 6   Sira: 7   Day: Pazar
```
Yukarıdaki loop'un doğru çalışmasının sebebi, loop control variable'ı `++i` olarak kullanınca compiler önce `i += 1` işlemini, sonra `(i < cnt)` işlemini yapar. Bu sayede fazladan bir kere çalışma olayı gerçekleşmemiş olur.

## `for` Loop
Bir kod parçasının belli bir sayıda tekrar etmesi istenildiğinde kullanılan loop'dur. Syntax:
```cpp
for ( initialization ; condition ; increment ) {
    //kodlar...
}
```
**Örnek:**
for (int i = 0; i < 5; ++i) {
    std::cout << i << " ";
}
**Output:**
```
0 1 2 3 4
```
Yukarıdaki kod şöyle çalışır:
- İlk `int i = 0` bir kereliğine çalışıp loop control variable'ı initialize edilir. Bu loop control variable, **local** bir variable'dır.
- Hemen ardından `i < 5` sorgusu yapılır. Buraya kadar her şey uygunsa, loop çalışır.
- Loop çalışıp başa döndükten sonra `++i` kısmı çalışır ve loop control variable değeri bir arttırılır ve hemen ardından `i < 5` sorgusu yapılır. Her şey uygunsa, loop çalışır.
- Bu işlemler devam eder ve en sonunda `++i` kısmı çalışıp `i < 5` sorgusu yapıldıktan sonra `i < 5` kısmı `false` olursa, loop sonlanır.

**Not:** `increment` kısmını for loop'un bloğunda ve parametresinde kullanmak, birbirinden farklı sonuçlar doğurur. Örnek:
```cpp
for (int i = 0; i < 5; ++i) {
		std::cout << i << ". Tekrar" << std::endl;
	}
```
**Output:**
```
0 1 2 3 4
```
Burada, for loop ilk çalıştığında `i` değeri 0 olur ve bunu bastırır.
```cpp
for (int i = 0; i < 5;) {
		std::cout << ++i << ". Tekrar" << std::endl;
	}
```
**Output:**
```
1 2 3 4 5
```
Burada, for loop ilk çalıştığında `i` değeri 0 olur ama `cout` kısmında `++i` şeklinde kullanıldığı için `i` bastırılmadan önce değeri bir arttırılır. Bunun bir önceki koddan tek farkı, 0 yerine 1'den başlıyor olması. Bunun duşunda output sayıları vs. aynı.

**Not:** Initialization (loop control variable) kısmını for loop dışında tanımlayıp for loop içinde kullanabilirsiniz.
```cpp
int i = 0;
for ( ; i < 3; ++i) {
	std::cout << i << ". Tekrar" << std::endl;
}
```
**Output:**
```
0. Tekrar
1. Tekrar
2. Tekrar
```

**Not:** Loop control variable'ın isminde başka bir variable'ı for dışında tanımlarsanız, for içinde loop control variable kullanılırken, for sonlandıktan sonra local variable olan loop control variable silineceği için for loop dışında tanımlanan variable kullanılır. Örnek:
```cpp
char i = 'a';
for (int i = 0; i < 3; i++) {
	std::cout << i << ". Tekrar" << std::endl;
}
std::cout << i << ". Tekrar" << std::endl;
```
**Output:**
```
0. Tekrar
1. Tekrar
2. Tekrar
a. Tekrar
```

### for-each Loop
for-each loop, arrrays, vectors ya da diğer data set'lerin elementleri (öğeleri) üzerinden loop'a devam eden bir for loop çeşitidir. Syntax:
```cpp
for(type variable_name : array/vector_name) {
	// Kodlar...
}
```
**Örnek:**
```cpp
int arr[] = { 1,2,3 };
for (int i : arr) {
	std::cout << i << " ";
}
```
**Output:**
```
1 2 3
```
Bu for-each loop (yani for loop), `arr` adındaki array'ın içindeki elemanlar bitene kadar loop tekrarlanır ve her tekrarda `i` variable'ı, array'ın o anki elementine eşit olur. Buradaki önemli kısım, `i` variable'ının data type'ı ile array'ın elementlerinin data type'ının aynı olması gerekmektedir. Aynı durum vector'lerde de geçerlidir. Vector örneği:
```cpp
vector<int> vec = { 11,22,33,44,55,66 };
cout << "The elements are: ";
for (auto i : vec) {
	cout << i << " ";
}
```
Bu durumun ortaya çıkaracağı sorunları önlemek için `auto` keyword'ünü kullanabilirsiniz. `auto` keyword'ü ile declare edilmiş bir variable, kendisine tanımlanan ilk value'nin type'ına göre özelleşir. Yani `auto i;` şeklinde declare edilmiş bir variable'a integer type bir değer girerseniz, bu variable bundan sonra integer değerleri tutacak şekilde özelleşir. Bu özelleşmeden sonra bu variable'a farklı bir type value atamaya çalıştığınızda hata alırsınız.

**for-each kullanmanın avantajları:**
- Uygulaması kolaydır.
- Iterator'ün pre-initialization'ını (yenileyicinin ön başlatılması) gerektirmez.
- Element sayısı belli olduğu için loop açısından hata olasılığı yoktur.

**for-each kullanmanın dezavantajları:**
- for-each loop'da kullanılan array ya da vektörün elementlerine doğrudan ulaşılamaz.
- for-each loop'da kullanılan array'ın elementleri ters (reverse) sırada kullanılamaz.
- for-each loop'da kullanılan array'ın herhangi bir elementi atlanamaz (skip).
- for-each loop, for ile yapılan index loop'dan daha yavaş çalışır.

**Not:** for ile yapılan index loop: array, vector etc.'nin uzunluğuna göre for loop oluşturup, loop içinde array, vector etc.'nin index'lerine erişmek.
**Not:** Index, array, vector etc.'nin elemenlerinin sırasına verilen isimdir. Örneğin `{1,2,3}` array'ının `1` elemanı 0. index'te, `2` elemanı 1. index'te, `3` elemenı 2. index'tedir. Index mantığında **reverse indexing** (ters indexleme) yoktur. Yani python'daki gibi -1. index'te `3` elemanına ulaşamazsınız.

### Infinite for Loop
for loop'ın syntax'ı:
```cpp
for ( initialization ; condition ; increment ) {
    //kodlar...
}
```
şeklindedir. `condition` kısmını tanımlamazsanız, for loop'un sonlanma koşulunu tanımlamadığınız için bu for loop sonlanmak için hiçbir koşula bağlı olmaz ve **Infinite** olur. Örnekler:
```cpp
for (int i = 1; ; ++i) {
	std::cout << i << std::endl;
}
```
```cpp
for (int i = 1; ; ) {
	std::cout << ++i << std::endl;
}
```
```cpp
int i = 1;
for (; ; ++i) {
	std::cout << i << std::endl;
}
```
```cpp
int i = 1;
for (; ; ) {
	std::cout << ++i << std::endl;
}
```
**Not:**  Bir infinity loop'u sonlandırmak için terminal ekranındayken `ctrl + c` tuş kombinasyonunu kullanabilirsiniz.

## Nested Loops
Bir loop, başka bir loop'un bloğuna tanımlanabilir. Bunlara Nested (iç içe) Loops nedir.

### Nested for Loop
Biri birinin block'una tanımlanmış for yapısına verilen isimdir. Örnek:
```cpp
for (int i = 0; i < 3; ++i) {
	std::cout << i << " (";
	for (int j = 0; j < 3; ++j) {
		std::cout << j;
	}
	std::cout << "), ";
}
```
**Output:**
```
0 (012)
1 (012)
2 (012)
```
En dıştaki loop **enclosing**, enclosing'in scope'una tanımlanan bütün loop'lar da **nested** olarak isimlenirilir. Nested loop'lar, kendisini kapsayan bütün loop'ların loop control variable'ları dahil bütün local variable'larına erişimi vardır. Örnek:
```cpp
for (int i = 0; i < 3; ++i) {
std::cout << "A";
	for (int j = 0; j < 3; ++j) {
		std::cout << i;
	}
}
```
**Output:**
```
A000A111A222
```

### Nested while Loop
Biri birinin block'una tanımlanmış while yapısına verilen isimdir. Örnek:
```cpp
int number1 = 0;
while (number1 < 3) {
	int number2 = 0;
	std::cout << number1 << " (";
	while (number2 < 3) {
		std::cout << number2 << "";
		number2 += 1;
	}
	std::cout << ")\n";
	number1 += 1;
}
```
**Output:**
```
0 (012)
1 (012)
2 (012)
```
En dıştaki loop **enclosing**, enclosing'in scope'una tanımlanan bütün loop'lar da **nested** olarak isimlenirilir. Nested loop'lar, kendisini kapsayan bütün loop'ların bütün local variable'larına erişimi vardır. Örnek:
```cpp
int number1 = 3;
	while (number1 < 6) {
	int number2 = 0;
	std::cout << number1 << " (";
	while (number2 < 3) {
		std::cout << number1 << "";
		number2 += 1;
	}
	std::cout << ")\n";
	number1 += 1;
}
```
**Output:**
```
3 (333)
4 (444)
5 (555)
```

# Loop Control Statements
Loop'ları davranışlarını kontrol etmek için kullanılan bazı keyword'ler vardır.

## `break` statement
Bir loop `break` statement ile karşılaştığında derhal sonlanır. Bu sonlanma işlemini `if` - `else` yapısını kullanarak belli bir koşula bağlayabiliriz.
```cpp
int number = 0;
	while (number < 10) {
		number++;
		std::cout << number << " ";
		if (number == 5) {
			break;
		}
	}
```
**Output:**
```
1 2 3 4 5
```
`break` statement, switch statement'de bir case'i sonlandırmak için de kullanılabilir.
```cpp
int number;
std::cout << "Bir numara girin: ";
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
Bir numara girin: 50
number is not 10, 20 or 30
```

## `continue` statement
Bir loop `continue` statement ile karşılaştığında kendinden sonraki kodları çalıştırmadan loop'un başına geri döner (loop'u yeniler). Bu sonlanma işlemini `if` - `else` yapısını kullanarak belli bir koşula bağlayabiliriz. Kullanılırken dikkatli olunması gerekmektedir çünkü kolayca infinite loop'a sebep olabilir. Infinite loop örneği:
```cpp
for (int i = 0; i < 10;) {
	if (i < 8) {
		std::cout << i << " ";
		i++;
	}
	else {
		std::cout << i;
		continue;
	}
	i++;
}
```
**Output:**
```
0 2 4 6 Loop End! Loop End! Loop End! Loop End! Loop End!... (Sonsuza kadar gider)
```
Doğrusu:
```cpp
for (int i = 0; i < 10; i++) {
	if (i < 9) {
		std::cout << i << " ";
	}
	else {
		std::cout << "Loop End! ";
		continue;
	}
	
}
```
**Output:**
```
0 1 2 3 4 5 6 7 8 Loop End! 
```

## `goto` statement
Bir `goto` statement, aynı label'e (etikete) sahip başka bir `goto` statement'e koşulsuz/şartsız (unconditional) atlar/sıçrar (jump). Syntax:
```cpp
goto label;

label: ...
```
ya da
```cpp
label: ...

goto label;
```
**Not:** `label`, kendinden sonraki bütün kodları çalıştırır. Eğer `goto` statement'i label'in altına tanımlarsanız, infinite loop'a girme riskine girebilirsiniz. Bunu önlemek için `label`'dan sonra herhangi bir yere `return 0;` ekleyerek `main()`'i sonlandırabilirsiniz.

`goto` statement kullanılması önerilmez çünkü programın kontrol akışını (control flow) takibini zorlaştırır. Ama bazı durumlarda işe yarayabilir. Örneğin bir sürü nested loop içeren bir yapıda, baya içlerdeki bir loop'a `goto` statement ekleyerek, control flow'u en dıştaki loop'u sonlandıran `break` statement'e yönlendirebilirsin. Örnek:
```cpp
for (int i = 0; i < 3; ++i){
	std::cout << "i" << " ";

	for (int j = 0; j < 3; ++j){
		std::cout << "j" << " ";

		for (int k = 0; k < 3; ++k){
			std::cout << "k" << " ";
			if (i==1){
				goto label1;
			}
		}
		std::cout << "\n  ";
	}
	std::cout << "\n";
	if (false){
		label1:
			break;
	}
}
```
**Output:**
```
i j k k k 
  j k k k
  j k k k

i j k
```
Burada for loop'ların oluşturduğu yapı bir kere çalıştıktan sonra `i == 1` olunca `if (i==1)` çalışır ve bloğundaki `goto label1;` çalışır. `goto label1;` control flow'u `label1`'e yönlendirdiği için `label1`'in altındaki `break` statement çalışıp en sonraki loop'u sonlandırır.

**Not:** Bloğuna `label1` tanımlı olan `if` statement `false` koşuluna sahip olduğu için asla çalışmaz. Bu yüzden `label1`'e tanımlı olan `break` statement'e ulaşabilmek için `goto` kullanmamız şart oluyor. Bu durumda, `if (i==1)` koşulunu `if (i==5)` şeklinde değiştirirsek, bu `if` statement çalışmayacağı için `goto` da çalışmaz ve dolayısıyla control flow `label1`'e yönlendirilemeyeceği için bütün for loop'lar sonlanana kadar çalışır ve aşağıdaki output'u elde edersiniz:
```
i j k k k 
  j k k k
  j k k k

i j k k k
  j k k k
  j k k k

i j k k k
  j k k k
  j k k k 

```