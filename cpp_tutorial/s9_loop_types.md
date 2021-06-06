# Loop Types
C++'da kodlar yukarıdan aşağıya doğru okunur. Bir kod parçasının birden fazla kez okunması istenildiğinde de **Loop Types** kullanılır.

## While Loop
`(Condition)` doğru (`true`) olduğu sürece tekrarlanan loop çeşitidir. `(Condition)`'a, boolean bir değeri ifade edebilecek herhangi bir expression (örneğin logic ifadeler ya da zero, non-zero ifadeler) ya da direkt `true` - `false` gibi boolean bir değer girilebilir. `(Condition)` doğru (`true`) olunca loop sonlanır. Syntax:
```cpp
while(condition) {
    // Kodlar...
}
```