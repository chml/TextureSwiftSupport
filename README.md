# TextureSwiftSupport

TextureSwiftSupport is a support library for [Texture](http://texturegroup.org/)<br>
It helps writing the code in Texture with Swift's power.

## Requirements

Swiift 5.1+

## LayoutSpecBuilder (Using \_functionBuidler)

Swift5.1 has FunctionBuilder(it's not officially)<br>
With this, we can write layout spec with no more commas. (It's like SwiftUI)

## SwiftUI-like Method Chain API

Inspiring from SwiftUI.

We can build a node hierarchy with the method chain.

For now, we have only a few methods. (e.g Padding, Overlay, Background)

```swift
textNode
  .padding([.vertical], padding: 4)
  .background(backgroundNode)
```

## About Function builders

[`Function builders`](https://github.com/apple/swift-evolution/blob/9992cf3c11c2d5e0ea20bee98657d93902d5b174/proposals/XXXX-function-builders.md) is a feature in Swift Language.<br>
For example, SwiftUI uses it.

[Implementation example](https://github.com/apple/swift/blob/23f707227608d885f1f4172458abca7f63e3b2c2/test/Constraints/function_builder_diags.swift)

### Plain

```swift

override func layoutSpecThatFits(_ constrainedSize: ASSizeRange) -> ASLayoutSpec {
    ASStackLayoutSpec(
        direction: .vertical,
        spacing: 0,
        justifyContent: .start,
        alignItems: .start,
        children: [
            textNode1,
            textNode2,
            textNode3,
        ]
    )
}
```

### With TextureSwiftSupport

```swift
override func layoutSpecThatFits(_ constrainedSize: ASSizeRange) -> ASLayoutSpec {
    LayoutSpec {
        VStackLayout {
            textNode1
            textNode2
            textNode3
        }
    }
}
```

More example

```swift
override func layoutSpecThatFits(_ constrainedSize: ASSizeRange) -> ASLayoutSpec {
    LayoutSpec {
        VStackLayout {
            HStackLayout {
                InsetLayout {
                    node1
                }
                InsetLayout {
                    node2
                }
            }
            node3
            HStackLayout {
                node4,
                node5,
                node6,
            }
        }
    }
}
```

## Layout Specs

- VStackLayout
- HStackLayout
- ZStackLayout
- InsetLayout
- OverlayLayout
- BackgroundLayout
- AspectRatioLayout
- VSpacerLayout
- HSpacerLayout

## Author

Muukii <muukii.app@gmail.com>
