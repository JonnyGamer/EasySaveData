# EasySaveData
Simple Property Wrapper Example for UserDefaults

```swift
@propertyWrapper
struct UserDefault<T> {
    let key: String
    let defaultValue: T
    var wrappedValue: T {
        get { return UserDefaults.standard.object(forKey: key) as? T ?? defaultValue }
        set { UserDefaults.standard.set(newValue, forKey: key) }
    }
}

enum SaveData {
    @UserDefault(key: "coins", defaultValue: 0)
    static var coins: Int
    
    @UserDefault(key: "Mega Array", defaultValue: [[Int]]())
    static var superArray: [[Int]]
}
```

```swift
SaveData.coins += 1
SaveData.superArray = [[1, 2, 3], [4, 5, 6]]
```
