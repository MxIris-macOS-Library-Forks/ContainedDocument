[![License][license badge]][license]
[![Platforms][platforms badge]][platforms]

# ContainedDocument

ContainedDocument allows you to nest `NSDocument` instances inside of abstract containers. These can be anything you need, including other `NSDocument` instances. This turns out to be a very tricky thing to do, and requires careful management of an `NSDocumentController` to make it possible.

Supporting the full range of `NSDocument` operations and interactions is challenging. I was able to pull off many of them, but the coordination still requires subclassing both `NSDocument` and `NSDocumentController`. 

## Integration

Carthage:

You can use [Carthage](https://github.com/Carthage/Carthage) to intall this as a static library.

```
github "ChimeHQ/ContainedDocument"
```

Swift Package Manager:

```swift
dependencies: [
    .package(url: "https://github.com/ChimeHQ/ContainedDocument.git")
]
```

## Classes

**ContainedDocumentController**

An `NSDocumentController` subclass that manages the `NSDocument` lifecycle and manages the relationship to your containers. To use it, you must override the three container-document association methods. Restorable state is supported, but is optional.

```swift
open func associateDocument(_ document: NSDocument, to container: Container)
open func disassociateDocument(_ document: NSDocument)
open func documentContainer(for document: NSDocument) -> Container?

open func encodeRestorableState(with coder: NSCoder, for document: NSDocument)
open func restoreState(with coder: NSCoder, for document: NSDocument)
// ...
```

**ContainedDocument**

This is an `NSDocument` subclass that makes it possible to support document duplication and window restoration.

### Suggestions or Feedback

We'd love to hear from you! Get in touch via an issue or pull request.

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.

[license]: https://opensource.org/licenses/BSD-3-Clause
[license badge]: https://img.shields.io/github/license/ChimeHQ/ContainedDocument
[platforms]: https://swiftpackageindex.com/ChimeHQ/ContainedDocument
[platforms badge]: https://img.shields.io/endpoint?url=https%3A%2F%2Fswiftpackageindex.com%2Fapi%2Fpackages%2FChimeHQ%2FContainedDocument%2Fbadge%3Ftype%3Dplatforms

