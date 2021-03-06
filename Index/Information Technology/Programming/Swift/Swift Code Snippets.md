# Swift Code Snippets

## URLRequest as cURL

```swift
extension URLRequest {
    public func cURL(pretty: Bool = false) -> String {
        let newLine = pretty ? "\\\n" : ""
        let method = (pretty ? "--request " : "-X ") + "\(self.httpMethod ?? "GET") \(newLine)"
        let url: String = (pretty ? "--url " : "") + "\'\(self.url?.absoluteString ?? "")\' \(newLine)"
        
        var cURL = "curl "
        var header = ""
        var data: String = ""
        
        if let httpHeaders = self.allHTTPHeaderFields, httpHeaders.keys.count > 0 {
            for (key, value) in httpHeaders {
                header += (pretty ? "--header " : "-H ") + "\'\(key): \(value)\' \(newLine)"
            }
        }
        
        if let bodyData = self.httpBody, let bodyString = String(data: bodyData, encoding: .utf8) {
            data = "--data '\(bodyString)'"
        }
        
        cURL += method + url + header + data
        
        return cURL
    }
}
```

## Convert `Data` into `String`

```swift
let string: String? = String(data: data, encoding: .utf8)

// replaces not convertable characters with � so its never fails
let string: String = String(decoding: data, as: UTF8.self) 
```

### Example

```swift
// swift strings is Unicode so it's always safe to forceunwrap them 
var data: Data = "Café".data(using: .utf8)!
data.removeLast()
print(String(data: data, encoding: .utf8)) // nil
print(String(decoding: data, as: UTF8.self)) // Caf�
```

## Checking for all elements in collection satisfies for some condition (all() method in Python)

```swift
let scores = [85, 88, 95, 92] 
let passed = scores.allSatisfy { $0 >= 85 } // returns true
```

## Checking if integer is even but without using `Int() % 2 == 0`

```swift
let rowNumber = 4 
if rowNumber.isMultiple(of: 2) {
	print("Even")
} else {
	print("Odd")
}
```

## Split array into chunks

```swift
// here choose min in case we don't have enough elements in array for this size
// for example [1...9] by 5 -> [1, 2, 3, 4, 5], [6, 7, 8, 9]
extension Array {
	func chunked(into size: Int) -> [[Element]] {
		return stride(from: 0, to: count, by: size).map {
				Array(self[$0 ..< Swift.min($0 + size, count)])
		}
	}
}

let numbers = Array(1...100)
let result = numbers.chunked(into: 5)
// print [[1, 2, 3, 4, 5], [6, 7, 8, 9, 10], [11, 12, 13, 14, 15], [16, 17, 18, 19, 20], [21, 22, 23, 24, 25], [26, 27, 28, 29, 30], [31, 32, 33, 34, 35], [36, 37, 38, 39, 40], [41, 42, 43, 44, 45], [46, 47, 48, 49, 50], [51, 52, 53, 54, 55], [56, 57, 58, 59, 60], [61, 62, 63, 64, 65], [66, 67, 68, 69, 70], [71, 72, 73, 74, 75], [76, 77, 78, 79, 80], [81, 82, 83, 84, 85], [86, 87, 88, 89, 90], [91, 92, 93, 94, 95], [96, 97, 98, 99, 100]]
```

```swift
struct User {
	var name: String
	var age: Int
}

extension String.StringInterpolation {
	mutating func appendInterpolation(_ value: User) {
		appendInterpolation("My name is \(value.name) and I'm \(value.age)")
	}
}

let user = User(name: "Guybrush Threepwood", age: 33)

// will print User details: My name is Guybrush Threepwood and I'm 33
print("User details: \(user)") 
```

```swift
struct PoliceForce {
	var officers: [String]
	
	subscript(index: Int, default default: String = "Unknown") -> String {
		if index >= 0 && index < officers.count {
			return officers[index]
		} else {
			return `default`
		}
	}
}

let force = PoliceForce(officers: ["Amy", "Jake", "Rosa", "Terry"])
print(force[0])
print(force[5])
print(force[-1, default: "The Vulture"])
```

- Check if array of [Swift Metatypes](Swift%20Notes/Swift%20Metatypes.md) contains some type
```swift
protocol Animal {}

struct Cat: Animal {}
struct Dog: Animal {}
struct Lion: Animal {}

func isNormalHousePet(_ pet: Animal) -> Bool {
 // using contains(where:) here because Metatypes are not Equatable
 return [Cat.self, Dog.self].contains { $0 == type(of: pet) }
}

print(isNormalHousePet(Cat())) // true
print(isNormalHousePet(Lion())) // false
```
