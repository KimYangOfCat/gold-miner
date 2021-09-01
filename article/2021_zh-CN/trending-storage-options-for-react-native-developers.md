> - 原文地址：[Trending Storage Options for React Native Developers](https://javascript.plainenglish.io/trending-storage-options-for-react-native-developers-8671fbffb686)
> - 原文作者：[Vithushan Jey](https://medium.com/@vithushjeytharma)
> - 译文出自：[掘金翻译计划](https://github.com/xitu/gold-miner)
> - 本文永久链接：[https://github.com/xitu/gold-miner/blob/master/article/2021/trending-storage-options-for-react-native-developers.md](https://github.com/xitu/gold-miner/blob/master/article/2021/trending-storage-options-for-react-native-developers.md)
> - 译者：[KimYangOfCat](https://github.com/KimYangOfCat)
> - 校对者：

# React Native 开发人员的流行存储方案

![封面图片](https://cdn-images-1.medium.com/max/4480/1*4L_oTx-TV7euxNgR-_8w9A.png)

数据是任何移动应用程序的关键部分。它赋予简单的用户界面以意义。但是存储、检索和维护数据才是真正的障碍。使用不同的存储机制（加密存储、离线存储、面向服务的存储、自动同步存储）对于存储可以提升移动应用程序开发全过程的各种数据至关重要。因为应用程序的每个用户界面和功能都需要不同的数据存储机制来使该应用程序自发。我列出了用于利用应用程序可用性的所有现有数据存储方法。

## 异步存储

AsyncStorage 是一个**未加密的、异步的、持久的、键值**存储系统，可以在应用程序上全局访问。

在 iOS 上，AsyncStorage 由本机代码支持，该代码将小值存储在序列化字典中，并将较大值存储在单独的文件中。在 Android 上，AsyncStorage 将[根据可用性使用 RocksDB](http://rocksdb.org/)或 SQLite。 AsyncStorage**在 Android 上仅支持 6 MB，**在 iOS 上支持无限量的数据。如果您的目标是构建跨平台应用程序，6MB 是限制。

JavaScript 代码充当接口并提供干净的基于 promise 的 API 方法、错误对象和非多功能函数。

存储用户、应用程序逻辑和其他人的公共数据的理想场所。

[**async-storage,React Native 的异步、持久、键值存储系统,下载async-storage的源码_GitHub_酷徒**](https://github.com/react-native-async-storage/async-storage)

## 安全存储

安全存储有助于存储**加密数据**。 React Native 没有捆绑任何存储敏感数据的方式。但是，已有适用于 Android 和 iOS 平台的解决方案。

![图片来自iOS开发者文档](https://cdn-images-1.medium.com/max/2000/1*rQu7_2pJ0VwNqOMe92rbCA.png)

在 iOS 上， [钥匙串服务](https://developer.apple.com/documentation/security/keychain_services)允许安全地存储应用程序的小块敏感信息。在 Android 上， [共享首选项](https://developer.android.com/reference/android/content/SharedPreferences)相当于用于安全存储的持久键值数据存储。 Shared Preferences 中的数据默认不加密，但[Encrypted Shared Preferences](https://developer.android.com/topic/security/data)包装了 Android 的 Shared Preferences 类，并自动加密密钥和值。

但 Android 有另一个安全选项而不是共享首选项，称为[Android Keystore](https://developer.android.com/training/articles/keystore)系统，用于将加密密钥存储在容器中，使其更难以从设备中提取。然而， [react-native-sensitive-info 的](https://github.com/mCodex/react-native-sensitive-info) [一个分支](https://github.com/mCodex/react-native-sensitive-info/tree/keystore)使用了 Android Keystore。

存储证书、令牌、密码和任何其他不属于异步存储的敏感信息的理想场所。

[**react-native-keychain,React Native 的钥匙串访问,下载react-native-keychain的源码_GitHub_酷徒**](https://github.com/oblador/react-native-keychain)

[**react-native-sensitive-info,使用密钥库加密将敏感数据保存到Android的共享首选项/iOS的React Native钥匙串,下载react-native-sensitive-info的源码_GitHub_酷徒**](https://github.com/mCodex/react-native-sensitive-info)

[**react-native-encrypted-storage,React Native 包装器围绕 EncryptedSharedPreferences 和 Keychain 提供异步存储的安全替代方案,下载react-native-encrypted-storage的源码_GitHub_酷徒**](https://github.com/emeraldsanto/react-native-encrypted-storage)

[**SecureStore - Expo 文档**](https://docs.expo.io/versions/latest/sdk/securestore/)

## MMKV 存储

[MMKV](https://github.com/Tencent/MMKV)是**腾讯开发的一个高效、小型的移动键值**存储框架，用于微信。

MMKV 使用 mmap 保持内存与文件同步，使用**protobuf**对值进行编码/解码，充分利用 Android 实现最佳效率性能。它支持进程间的并发读写访问，允许多进程并发。由于完全同步调用，很容易保持数据。

存储用户、应用程序逻辑和其他人的通用数据的理想场所。它是**Async Storage**的替代品。

[**react-native-mmkv-storage,使用 JSI 用 C++ 编写的用于 React Native 的超快速 (0.0002s 读/写)、小型加密移动键值存储框架,下载react-native-mmkv-storage的源码_GitHub_酷徒**](https://github.com/ammarahm-ed/react-native-mmkv-storage)

[**react-native-mmkv, ⚡️ 一个非常快的 React Native 键/值存储库,下载react-native-mmkv的源码_GitHub_帮酷比 AsyncStorage 快 30 倍！**](https://github.com/mrousavy/react-native-mmkv)

## SQLite 存储

SQLite 是一个 C 语言库，它实现了一个**小型、快速、自包含、高可靠性、功能齐全的 SQL 数据库引擎**。它是最常用的数据库引擎。它**内置于所有手机**和大多数计算机中，并捆绑在人们每天使用的无数其他应用程序中。该文件格式稳定、跨平台且向后兼容，开发人员承诺保持这种方式。

存储比异步、安全和 MMKV 存储更多数据的理想场所，它可以支持离线应用程序开发。

[**WatermelonDB,用于强大的 React 和 React Native 应用程序的 🍉 反应式和异步数据库 ⚡️,下载WatermelonDB的源码_GitHub_帮酷**](https://github.com/Nozbe/WatermelonDB)

[**react-native-sqlite-storage,全功能 SQLite3 Native Plugin for React Native (Android 和 iOS),下载react-native-sqlite-storage的源码_GitHub_酷徒**](https://github.com/andpor/react-native-sqlite-storage)

[**react-native-sqlite-2,适用于 iOS、Android、Windows 和 macOS 的 React Native 的 SQLite3 原生插件,下载react-native-sqlite-2的源码_GitHub_酷徒**](https://github.com/craftzdog/react-native-sqlite-2)

[**GitHub - ospfranco/react-native-quick-sqlite:⚡️ react-native 最快的 SQLite 实现**](https://github.com/ospfranco/react-native-quick-sqlite)

[**SQLite - Expo 文档**](https://docs.expo.dev/versions/v42.0.0/sdk/sqlite/)

## 数据库服务

有不同类型的数据库服务可用于通过遵循不同的方法来执行移动应用程序数据层的各种功能。这些都在这里列出。

1. Firebase 火力库
2. Firebase 数据库
3. Firebase 存储
4. Mongo DB 的领域
5. 袋数据库

### Firebase 火力库

Cloud Firestore 是一个**NoSQL 文档数据库**，可让您轻松**存储、同步和查询**Google 规模的移动和网络应用数据。可以使用集合和文档轻松构建数据，并使用层次结构使用表达查询轻松存储和检索数据。

[**GitHub - react-native-firebase：一个 NoSQL 文档数据库，可让您轻松存储、同步和查询移动和 Web 应用程序的数据**](https://github.com/invertase/react-native-firebase/tree/master/packages/firestore)

### Firebase 数据库

Firebase 实时数据库是云托管的。数据**以 JSON 格式存储并实时同步**到每个连接的客户端。当您使用我们的 React Native SDK 构建跨平台应用程序时，所有客户端共享一个实时数据库实例并自动接收最新数据的更新。

[**react-native-firebase,实时云托管数据库,下载react-native-firebase的源码_GitHub_酷徒**](https://github.com/invertase/react-native-firebase/tree/master/packages/database)

### Firebase 存储

Cloud Storage for Firebase 是在云中存储**图像、音频、视频或其他用户生成内容**的理想场所。它是一种功能强大、简单且经济高效的对象存储服务，专为 Google 规模而构建。适用于 Cloud Storage 的 Firebase SDK 为应用的文件上传和下载添加了 Google 安全性，无论网络质量如何。

[**GitHub - react-native-firebase：为 Google 规模构建的强大、简单且经济高效的对象存储服务**](https://github.com/invertase/react-native-firebase/tree/master/packages/storage)

### Mongo DB 的领域

Realm 是一个**直接在手机**、平板电脑或可穿戴设备中运行的移动数据库。数据直接作为对象公开并可通过代码查询，从而无需 ORM。它支持关系、泛型和向量化。它**比原始 SQLite 更快，**并且是**SQLite 和键值存储**的替代品。 Realm 的本地数据库将数据保存在磁盘上，因此应用程序也**可以离线工作**。

[**realm-js,Realm 是一个移动数据库:SQLite 和键值存储的替代品,下载realm-js的源码_GitHub_酷徒**](https://github.com/realm/realm-js)

### 袋数据库

PouchDB 是一个袖珍型数据库，使应用程序可以**在离线时**将数据存储在本地，然后在应用程序重新上线时将其与 CouchDB 和兼容服务器同步，无论用户下次登录何处，都可以保持用户的数据同步。 实际上，PouchDB 是专为网络设计。但是现在开发者社区已经创建了第三方库来支持 React Native。

[**pouchdb-react-native,具有异步存储的Pouchdb,下载pouchdb-react-native的源码_GitHub_帮酷**](https://github.com/seigel/pouchdb-react-native)

[**pouchdb-react-native, 🐨 - PouchDB 是一个袖珍型数据库, 有一些补丁可以在 React Native 上运行,下载pouchdb-react-native的源码_GitHub_帮酷**](https://github.com/craftzdog/pouchdb-react-native)

## 结论

试试这些数据存储库，以增强 React Native 应用程序中的数据存储和检索功能。我相信这些令人兴奋的存储选项对于执行不同的面向数据的任务以创建成熟的移动应用程序非常有用。

感谢您阅读这篇文章。

> 如果发现译文存在错误或其他需要改进的地方，欢迎到[掘金翻译计划](https://github.com/xitu/gold-miner)对译文进行修改并公关，也可以获得相应的奖励积分。文章**开头的本文永久链接**即为本文在 GitHub 上的 MarkDown 链接。

---

> [掘金](https://github.com/xitu/gold-miner)是一个翻译优质互联网技术文章的社区，文章来源为[掘金](https://juejin.im)上的中文文章。内容覆盖[Android](https://github.com/xitu/gold-miner#android) 、 [iOS](https://github.com/xitu/gold-miner#ios) 、[前端](https://github.com/xitu/gold-miner#%E5%89%8D%E7%AB%AF)、[想翻译计划](https://github.com/xitu/gold-miner#%E5%90%8E%E7%AB%AF)、[区块链](https://github.com/xitu/gold-miner#%E5%8C%BA%E5%9D%97%E9%93%BE)、[产品](https://github.com/xitu/gold-miner#%E4%BA%A7%E5%93%81)、[设计](https://github.com/xitu/gold-miner#%E8%AE%BE%E8%AE%A1)、 [人工智能](https://github.com/xitu/gold-miner#%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD)等，领域要查看更多优质译文，请持续关注[掘金翻译计划](https://github.com/xitu/gold-miner)、[官方微博](http://weibo.com/juejinfanyi)、[知乎专栏](https://zhuanlan.zhihu.com/juejinfanyi)。
