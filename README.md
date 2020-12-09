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
    
    @UserDefault(key: "Mega Array", defaultValue: [[.init(repeating: [Bool](), count: 16)]])
    static var superArray: [[Bool]]
}
```

```swift
SaveData.coins += 1
SaveData.superArray[0] == []
```
