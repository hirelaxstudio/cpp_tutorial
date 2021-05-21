# Storage Classes
Bir storage class, C++ programı içindeki *scope* *(visibility [Görünürlük] )*, variables'in life-time'ı ve functions tanımlar. Bu specifier'lar (Belirleyiciler), modifier'lardan (char, int, float, double etc.) önce gelir. Bu depolama sınıfları aşağıda belirtilmiş:
 - auto
 - register
 - static
 - extern
 - mutable

## The auto Storage Class
*The auto Storage Class*, bütün local variables için default (varsayılan) storage'dır.
```cpp
{
	int a;
	auto int a;
}
```
Yukarıdaki örnekte aynı storage class'a ait iki variable tanımlanmıştır. auto yalnızca functions, yani local variables için kullanılabilir.

## The register Storage Class
İlk önce bazı kavramları açıklayalım:
 - **Cache:** CPU'ya gömülüdür. *Cache*, bir işlemi ikinci defa yaptığımızda (örneğin bir programı ikinci defa açışımızda), sonraki işlemi tahmin eden donanımdır. Teknik olarak açıklarsak: cache, bir sonraki işlemin tamamını *%90* olasılıkla tahmin edip bu bilgiyi tutan **L1**, L1'in *%10* olasılıkla tutturamaması durumunda, işlemi *%90* olasılıkla tahmin eden **L2** adı verilen CPU çekirdeğine gömülü iki adet *statik RAM*'den oluşur. Bilgisayar bir veriye ulaşmak için ilk *cache*'e, orada yoksa *RAM*'e, orada da yoksa *SSD* veya *HHD*'ye bakar. Kavramları daha iyi anlamak için çorbacı örneği verelim. Bir lokantaya ilk defa gidip bir kase çorba istediğinizde çorbanın yapılıp gelmesi uzun sürebilir. Eğer yemeğin yapıldığı yerin (*HDD* ya da *SSD*) hemen ön tarafında belirli bir miktar yemeği sıcak tutabilecek bir hazne varsa (*RAM*) ve siz oradaki çeşitlerden birini yiyecekseniz çorbanın pişmesini beklemezsiniz. Siz eğer aynı yere daha sık gelmeye başlarsanız garson sizi tanır ve sizin geleceğiniz saatlerde yemek arabasına (*L2*) sizin çeşitlerinizi de koyar. Sürekli müşterisi olursanız ve %90 aynı siparişleri veriyorsanız geleceğiniz saatte çorbanızı masanızda (*L1*) hazır bulursunuz.

 - **Static RAM:** Makine açık olduğu sürece üzerine yazılan veriyi tutabilir. Transistörlerden imal edilmiştir. Bu RAM'ler yapılarında transistör kullanıldığı için daha pahalıdır.

 - **Dynamic RAM:** Üzerindeki veriyi tutabilmek için belirli aralıklarla kondansatörlerle tetiklenmeleri gerekir. Aksi takdirde üzerindeki veri kaybolur. Bunun için ana kart üzerinde bu tetiklemeyi yapacak ayrı bir devre dizayn edilmiştir ve bu yüzden dynamic RAM'ler cache bellek olarak çekirdekte kullanılamazlar. Bildiğimiz RAM'ler Dynamic RAM'ler.

**Not:** CPU *deterministiktir*. Ya hep ya hiç mantığıyla çalışır. Bu yüzden parça parça tahmin olayı yoktur. cache'da da böyledir. Daha fazla bilgi için *determinist* kelimesini araştırabilirsiniz.

**Not:** Daha fazla bilgi için [tıklayınız](https://www.chip.com.tr/blog/enginsaklidarkexecut/cache-bellek-nedir-ne-ise-yarar-nasil-calisir_4455.html).

Şimdi register storage class'ı açıklayalım:
**Register Storage Class**, RAM üstünde tutulmak yerine bir register'da depolanması gereken local variable'ları tanımlamak için kullanılır. Bunun anlamı: Variable, register size'a eşit bir maksimum boyuta eşit (genellikle bir kelime) ve tekli '&' operatörü bir bellek konumu olmadığı için uygulanamayacağı anlamına gelir. Register sadece counters gibi hızlı erişim gerektiren variables için kullanılmalıdır. Daha açıklayıcı olmak gerekirse: Register'i CPU cache'deki bellek olarak düşünün. Local variables, CPU cache'e kaydedilmesi gerekiyor. Bunun nedeni şu: Local variables'e kısa süreli ihtiyaç duyulduğu için data'yı RAM'den almak yerine CPU cache'deki register'der alır çünkü zaten o bilgi CPU cache'de hazır halde bulunduğu için daha hızlı. Bu datalar genellikle int ve dword gibi primatif yapılardır yani objects kaybetme olasılığı çok fazla yok. Ayrıca register defining yapmanın, variable'nin bir register'de depolanacağı anlamına gelmediğini unutmayın. Bu, register'in hardware ve implementation kısıtlamalarına bağlı olarak saklanabileceği anlamına gelir.
```cpp
{
	register int miles;
}
```

## The static Storage Class
**static Storage Class**, compiler'a, bir local variable'nin scope'a girip çıktığı her seferinde o local variable'ı creating veya destroying yapmak yerine, programın life-time'ı boyunca o local variable'yi tutması talimatını verir. Bu sayede static local variables'e sahip bir fonksiyon çağırıldığında, o static local varieble'lar belleğe kaydedilir ve programın life-time'ı boyunca silinmeden bellekte kalır. Bu olay function sonlansa bile böyledir. static keyword'ü global variables'e de uygulanabilir. Bunu yapmak, variables'in scope'sinin, declare edildiği file ile sınırlı/kısıtlı (restricted) kalmasına neden oluyor. Static keyword'ü class data member üzerinde kullanıldığı zaman, o class'dan oluşmuş bütün objects'de aynı olmasına sebep olur. Bu aynı olma durumu, o static class data member'ın bir tane kopyasının oluşturulmasından kaynaklanıyor. Yani static class data member'ın değeri bir object'de değiştirilmeye çalıştırılırsa, bütün objects'de değişir (Çünkü bir adet kopyası oluşturuluyor).

## The extern Storage Class
extern storage class, bütün program files tarafından görülebilen bir global değişkenin referansı olarak kullanılır. extern kullanılarak declare edilmiş bir variable initialize edilemez çünkü extern kullanarak yaptığınız tek şey, variable adını, önceden define edilmiş bir storage location'a yönlendirmektir. Bir files'da global variable veya function define yaptığınızda, bunları farklı files'da kullanabilmek için extern keyword kullanarak global variable veya function define yaptığınız file'a referans vermiş olursunuz. Extern keyword'ü ile ilgili daha fazla bilgi 's3_variable_types.cpp' dosyasında bulunmaktadır. Örnek:

First File: main.cpp
```cpp
#include <iostream>

int count ;
extern void write_extern(); // support.cpp'da define edilmiş.

main() {
	count = 5;
	write_extern();
}
```

Second File: support.cpp
```cpp
#include <iostream>

extern int count; // main.cpp'da define edilmiş.
void write_extern(void)

{
std::cout << "Count is " << count << std::endl;
}
```

## The mutable Storage Class
The mutable specifier (belirteç) applies only to class objects, which are discussed later in this tutorial. It allows a member of an object to override const member function. That is, a mutable member can be modified by a const member function.
