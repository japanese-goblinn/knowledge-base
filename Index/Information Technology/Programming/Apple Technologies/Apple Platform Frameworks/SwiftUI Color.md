- **Links**
	- [Encode and Decode SwiftUI Color](https://nilcoalescing.com/blog/EncodeAndDecodeSwiftUIColor/)
- **Notes**
	```swift
	extension Color {
	  	var isDarkColor: Bool {
			var r, g, b, a: CGFloat
			(r, g, b, a) = (0, 0, 0, 0)
			UIColor(self).getRed(&r, green: &g, blue: &b, alpha: &a)
			let lum = 0.2126 * r + 0.7152 * g + 0.0722 * b
			return lum < 0.50
	  	}
	}
	```