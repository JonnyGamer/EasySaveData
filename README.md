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
}
```

```swift
SaveData.coins += 1
```
