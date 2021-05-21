# Modifier Types
`char`, `int` ve `double` data type'ları, kendinden önce modifier eklenmesine (s2_data_types.md'de bakabilirsiniz) izin verir. Modifier, bir data type'ın *base* type'ını (temel değerini, ilk değerini, yani düz `int` gibi) değiştirmek için kullanılır. Böylece çeşitli durumlarda, ihtiyaca daha uygun data type versiyonları elde etmiş oluruz (*double* yerine *long double* kullanmak gibi).

## Data Modifiers (Veri Değiştiriciler)

 - signed
 - unsigned
 - long
 - short

Bu data modifier'lar, `char`, `int` ve `double` data type'larına aşağıdaki gibi uygulanabilir:

**char:**
```cpp
signed char vrb;
unsigned char vrb;
```

**int:**
```cpp
signed short int vrb;
unsigned short int vrb;

signed int vrb;
unsigned int vrb;

signed long int vrb;
unsigned long int vrb;

signed long long int vrb;
unsigned long long int vrb;
```

**double:**
```cpp
double vrb;
long double vrb;
```

## Type Qualifiers (Tür Niteleyicileri)
**Type Qualifiers**, kendinden sonra yazılan variables hakkında *information (bilgi)* verir.

**Not:** *Execution*, direkt çalıştırılmış program, *Process*, çalıştırmak için belleğe alınmış kod parçası anlamına gelmektedir.

### 1) `const`
`const` keyword'ü, const özelliğinde object'ler oluşturmakta kullanılır. Execution (yürütme) sırasında program tarafından değiştirilemez.

### 2) `volatile`
`volatile` keyword'ü, compiler'in o object'ti ya da variable'ı agresif bir şekilde optimize etmesinden kaçınmasını sağlıyor. "Agresif bir şekilde optimize etmek" derken şu anlatılmak isteniyor: Örneğin, optimize sonucu data type'ı compiler tarafından otomatik olarak `double`'dan `float`'a dönüştürülen bir variable'a `double` value girilemeyeceği için o variable'a `double` value define edilmeye çalışılırsa program hata verir. "Agresif bir şekilde optimize etmek" bu sonucu doğurur. Bir variable, execution (yürütme) sırasında program içinde sürekli değişiyorsa, `volatile` keyword'ünü kullanmak tercih edilebilir.

### 3) `restrict`
`restrict` keyword'ü ile declare edilen bir pointer'a sadece o pointer ulaşabilir. Yani başka pointer'lar kullanıp aynı nesneye ulaşamazsın. Bu da sadece c99'da var. (Orası pek doğru değil birçok cpp compilerı şu an destekliyor bir standart haline gelmese de)
