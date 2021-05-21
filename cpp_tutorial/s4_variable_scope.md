# Scope
**Scope**, alan, bölge anlamına gelmektedir. Variable'ların declare edildiği 3 bölge vardır.
 - **Global variable**'ler, herhangi bir block, function, namespace etc. içerisinde olmayan, en dışta tanımlı variable'lardır.
 - **Local variable**'ler, herhangi bir block, function, namespace etc. içerisinde olan variable'lardır.
 - **Formal parameter**'lar (parametreler), function'ların parametrelerinde define edilen variable'lardır.

## 1) Global Variable
Global variables, bütün scope'ların dışına, global'e define edilir. Genellikle programın en üst satırlarına tanımlanır. Global variable'lar, programın life-time'ı (çalıştığı süre) boyunca değerini korur/tutar. Global variable'lara, programın herhangi bir yerinden erişilebilir (accessed).

## 2) Local Variable
Global scope'dan direkt erişilemeyen, local scope'da define edilmiş variable'lardır. Bir function, namespace etc. tarzı yapılar içinde define edilen variable'lar local variable'dır.

### Local ve Global Variable Örneği:
```cpp
#include <iostream>
using namespace std;

int g; // Global variable declaration
int c = 100; // Global variable declaration
int main () {
	int a, b; // Local variable declaration
	int c = 200; // Local variable declaration
	
	a = 10;
	b = 20;
	g = a + b;
	cout << g; // Output: 30
	cout << c; // Output: 200
	return 0;
}
```
**Not:** Aynı isimde hem global hem de local variable varsa, o variable local'deki bir function veya obje tarafından istendiğinde ilk local'deki variable dikkate alınır, local'de yoksa global variable dikkate alınır.

## Formal ve Actual Parameters
**Formal Parameter:** Bir function tanımladığınızda verdiğiniz parametrelere denir. Örnek:
```cpp
int deneme(int a, int b) {
	return 0;
}
```

**Actual Parameter:** Bir function çağırdığınızda (called) verdiğiniz parametrelere denir. Örnek:
```cpp
#include <iostream>
using namespace std;

int deneme(int a, int b) {
	return 0;
}

int main() {
	int x = 1, y = 2;
	cout << deneme(x,y); // Output: 0
}
```

# Initializing Local and Global Variables
Local variable define edildiğinde sistem tarafından otomatik olarak initialize edilemez. Sizin initialize etmeniz gerekmektedir. Örneğin function içine define edilmiş bir variable'ı, o fonksiyonu çağırarak local variable'ı initialize etmiş olursunuz. Yani o function'u çağırdığınızda, function'un içindeki kodlar çalışacak ve local variable bu sırada initialize edilmiş olacak. Global variable'lar ise data type'ı (int, char, float etc.) belirtilmişse, sistem tarafından otomatik olarak initialize edilir ve programın life-time'ı boyunca varlığını sürdürür. Örnek:
```cpp
#include  <iostream>
using  namespace  std;

int  global_vrb = 200; // Global variable initializing 
  
int  deneme(){
	int  local_func_vrb = 100; // Local variable initializing
	return  local_func_vrb;
	}
  
int  main(){
	int  b;
	b = deneme();
	cout  <<  b  <<  "\n"  <<  global_vrb;
	return 0;
}
```
