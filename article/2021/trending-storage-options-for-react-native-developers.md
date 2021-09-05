> * 原文地址：[Trending Storage Options for React Native Developers](https://javascript.plainenglish.io/trending-storage-options-for-react-native-developers-8671fbffb686)
> * 原文作者：[Vithushan Jey](https://medium.com/@vithushjeytharma)
> * 译文出自：[掘金翻译计划](https://github.com/xitu/gold-miner)
> * 本文永久链接：[https://github.com/xitu/gold-miner/blob/master/article/2021/trending-storage-options-for-react-native-developers.md](https://github.com/xitu/gold-miner/blob/master/article/2021/trending-storage-options-for-react-native-developers.md)
> - 译者：[KimYangOfCat](https://github.com/KimYangOfCat)
> - 校对者：

# React Native 开发者的流行存储方案

![Cover Picture](https://cdn-images-1.medium.com/max/4480/1*4L_oTx-TV7euxNgR-_8w9A.png)

数据是任何移动应用程序的关键部分。它赋予朴素的用户界面以意义。但是存储、检索和维护数据才是真正的难题。使用不同方式的存储机制（加密存储、离线存储、面向服务的存储、自动同步存储）对于存储各种数据至关重要，并且可以加速移动应用程序开发全过程。因为应用程序的每个用户界面和功能都需要不同的数据存储机制来使该应用程序更自然。我列出了所有现有的可用于提升应用程序可用性的数据存储方法。

## 异步存储

AsyncStorage 是一个**未加密的、异步的、持久的键值**存储系统，可以在应用程序上全局访问。

在 iOS 上，由 native 代码实现的 AsyncStorage 将小值存储在序列化字典中，并将较大值存储在单独的文件中。在 Android 上，AsyncStorage 将根据可用性使用 [RocksDB](http://rocksdb.org/) 或 SQLite。 AsyncStorage **在 Android 上仅支持 6 MB，**在 iOS 上支持无限量的数据。如果你的目标是构建跨平台应用程序，6MB 是限制。

JavaScript 代码充当接口并提供清楚的基于 promise 的 API 方法、错误对象和 non-multi 功能函数。

此方案是存储用户、应用程序逻辑和其他人的公共数据的理想场所。

[**GitHub - react-native-async-storage/async-storage: 一个用于React Native 的异步的、持久的、键值存储系统。**](https://github.com/react-native-async-storage/async-storage)

## 安全存储

安全存储有助于存储**加密数据**。 React Native 没有捆绑任何存储敏感数据的方式。但是，已有适用于 Android 和 iOS 平台的解决方案。

![Picture from iOS developer documentation](https://cdn-images-1.medium.com/max/2000/1*rQu7_2pJ0VwNqOMe92rbCA.png)

在 iOS 上， [Keychain Services](https://developer.apple.com/documentation/security/keychain_services) 允许安全地存储应用程序的小块敏感信息。在 Android 上， [Shared Preference](https://developer.android.com/reference/android/content/SharedPreferences) 相当于持久键值数据存储，可被用于安全存储。 Shared Preference 中的数据默认不加密，但[Encrypted Shared Preferences](https://developer.android.com/topic/security/data)包装了 Android 的 Shared Preferences 类，并自动加密键和值。

除了 Shared Preferences，Android 有另一个可用于安全存储的名为[Android Keystore](https://developer.android.com/training/articles/keystore)的系统，用于将加密密钥存储在容器中，使其更难以从设备中提取。并且， [react-native-sensitive-info](https://github.com/mCodex/react-native-sensitive-info) 的[一个分支](https://github.com/mCodex/react-native-sensitive-info/tree/keystore)使用的就是 Android Keystore。

此方案是存储证书、令牌、密码和任何其他不属于异步存储的敏感信息的理想场所。

[**GitHub - oblador/react-native-keychain: React Native 的钥匙链存取**](https://github.com/oblador/react-native-keychain)

[**GitHub - mCodex/react-native-sensitive-info: React Native 用钥匙库加密将敏感数据保存到安卓的 Shared Preferences / iOS 的 Keychain 中**](https://github.com/mCodex/react-native-sensitive-info)

[**GitHub - emeraldsanto/react-native-encrypted-storage: 围绕 EncryptedSharedPreferences 和 Keychain 的 React Native 包装器，为 Async Storage 提供安全的替代方案。**](https://github.com/emeraldsanto/react-native-encrypted-storage)

[**SecureStore - Expo 文献**](https://docs.expo.io/versions/latest/sdk/securestore/)

## MMKV 存储

[MMKV](https://github.com/Tencent/MMKV) 是腾讯开发的一个**高效、小型的移动键值**存储框架，应用于微信。

MMKV 使用 mmap 保持内存与文件同步，使用 **protobuf** 编码/解码值，充分利用 Android 实现最佳效率性能。它支持进程间的并发读写访问，允许多进程并发。由于完全同步调用，很容易保持数据。

此方案是存储用户、应用程序逻辑和其他人的公共数据的理想场所。它是 **Async Storage** 的替代品。

[**GitHub - ammarahm-ed/react-native-mmkv-storage: 可用于 React Native 的一个超快（0.0002s读/写）、小型、加密的移动键值存储框架，其使用了 JSI 并由 C++ 编写。**](https://github.com/ammarahm-ed/react-native-mmkv-storage)

[**GitHub - mrousavy/react-native-mmkv: ⚡️ 一个用于 React Native 的极快的键/值存储库。~比 AsyncStorage 快 30 倍!**](https://github.com/mrousavy/react-native-mmkv)

## SQLite 存储

SQLite 是一个 C 语言库，它实现了一个**小型、快速、自包含、高可靠性、功能齐全的 SQL 数据库引擎**。它是最常用的数据库引擎。它**内置于所有手机**和大多数计算机中，并捆绑在人们每天使用的无数其他应用程序中。开发人员承诺其文件格式稳定、跨平台且向后兼容。

此方案是存储比异步、安全和 MMKV 存储更多数据的理想场所，它可以支持离线应用程序开发。

[**GitHub - Nozbe/WatermelonDB: 🍉 为强大的 React 和 React Native 应用提供反应式异步数据库 ⚡️**](https://github.com/Nozbe/WatermelonDB)

[**GitHub - andpor/react-native-sqlite-storage: 用于 React Native 的全功能 SQLite3 Native 插件（安卓和 iOS）。**](https://github.com/andpor/react-native-sqlite-storage)

[**GitHub - craftzdog/react-native-sqlite-2：适用于 iOS、安卓、Windows 和 macOS 的 React Native 的 SQLite3 Native 插件。**](https://github.com/craftzdog/react-native-sqlite-2)

[**GitHub - ospfranco/react-native-quick-sqlite：⚡️ 为 react-native提供最快的 SQLite 实现。**](https://github.com/ospfranco/react-native-quick-sqlite)

[**SQLite - Expo 文献**](https://docs.expo.dev/versions/v42.0.0/sdk/sqlite/)

## 数据库服务

有不同类型的数据库服务可用于通过遵循不同的方法来执行移动应用程序数据层的各种功能。这些都在这里列出。

1. Firebase Firestore
2. Firebase Database
3. Firebase Storage
4. Realm by Mongo DB
5. Pouch DB

### Firebase Firestore

Cloud Firestore 是一个 **NoSQL 文档数据库**，可让你轻松**存储、同步和查询** Google 规模级的移动和 web 应用的数据。可以使用集合和文档轻松结构化数据，并使用层次结构存储数据以及轻松使用表达式查询来检索数据。

[**GitHub - react-native-firebase: 一个 NoSQL 文档数据库，让你轻松为你的移动和 web 应用存储、同步和查询数据。**](https://github.com/invertase/react-native-firebase/tree/master/packages/firestore)

### Firebase Database

Firebase 实时数据库是由云托管的。数据**以 JSON 格式存储并实时同步**到每个连接的客户端。当你使用我们的 React Native SDK 构建跨平台应用程序时，所有客户端共享一个实时数据库实例并自动接收最新数据的更新。

[**GitHub - react-native-firebase：一个实时的云托管数据库**](https://github.com/invertase/react-native-firebase/tree/master/packages/database)

### Firebase Storage

Firebase 的 Cloud Storage 是在云中存储**图像、音频、视频或其他用户生成内容**的理想场所。它是一种功能强大、简单且经济高效的对象存储服务，专为 Google 规模打造。 无论网络质量如何，Cloud Storage 的 Firebase SDK 为应用的文件上传和下载添加了 Google 级安全防护。

[**GitHub - react-native-firebase:一个强大、简单、经济的对象存储服务，专为 Google 规模打造**](https://github.com/invertase/react-native-firebase/tree/master/packages/storage)

### Realm by Mongo DB

Realm 是一个**直接在手机**、平板电脑或可穿戴设备中运行的移动数据库。数据直接作为对象暴露并可通过代码查询，从而无需 ORM。它支持关系、泛型和向量化。它**比原始 SQLite 更快，**可以替代**键值方式存储的 SQLite **。Realm 的本地数据库将数据保存在磁盘上，因此应用程序也可以 **离线工作**。

[**GitHub - realm/realm-js: Realm is a mobile database：Realm 是一个移动数据库：可以替代键值方式存储的 SQLite**](https://github.com/realm/realm-js)

### Pouch DB

PouchDB 是一个袖珍型数据库，使应用程序可以**在离线时**将数据存储在本地，然后在应用程序重新上线时将其与 CouchDB 和兼容服务器同步，无论用户下次登录何处，都可以保持用户的数据同步。 实际上，PouchDB 是专为网络设计。但是现在开发者社区已经创建了第三方库来支持 React Native。

[**GitHub - seigel/pouchdb-react-native:  支持异步存储的 Pouchdb**](https://github.com/seigel/pouchdb-react-native)

[**GitHub - craftzdog/pouchdb-react-native: 🐨 - PouchDB 是一个袖珍的数据库，有一些支持在 React Native 上运行的补丁。**](https://github.com/craftzdog/pouchdb-react-native)

## 总结

试试这些数据存储库，以增强 React Native 应用程序中的数据存储和检索功能。我相信这些令人兴奋的存储选项对于执行不同面向数据的任务以及创建全面的移动应用程序都非常有用。

感谢你阅读这篇文章。

> 如果发现译文存在错误或其他需要改进的地方，欢迎到 [掘金翻译计划](https://github.com/xitu/gold-miner) 对译文进行修改并 PR，也可获得相应奖励积分。文章开头的 **本文永久链接** 即为本文在 GitHub 上的 MarkDown 链接。

---

> [掘金翻译计划](https://github.com/xitu/gold-miner) 是一个翻译优质互联网技术文章的社区，文章来源为 [掘金](https://juejin.im) 上的英文分享文章。内容覆盖 [Android](https://github.com/xitu/gold-miner#android)、[iOS](https://github.com/xitu/gold-miner#ios)、[前端](https://github.com/xitu/gold-miner#前端)、[后端](https://github.com/xitu/gold-miner#后端)、[区块链](https://github.com/xitu/gold-miner#区块链)、[产品](https://github.com/xitu/gold-miner#产品)、[设计](https://github.com/xitu/gold-miner#设计)、[人工智能](https://github.com/xitu/gold-miner#人工智能)等领域，想要查看更多优质译文请持续关注 [掘金翻译计划](https://github.com/xitu/gold-miner)、[官方微博](http://weibo.com/juejinfanyi)、[知乎专栏](https://zhuanlan.zhihu.com/juejinfanyi)。
