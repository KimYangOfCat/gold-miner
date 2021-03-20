> * 原文地址：[Google Cloud Releases Its Healthcare Consent Management API to General Availability](https://www.infoq.com/news/2021/03/gcp-healthcare-consent-api)
> * 原文作者：[Sergio De Simone](https://www.infoq.com/profile/Sergio-De-Simone/)
> * 本文永久链接：[https://github.com/xitu/gold-miner/blob/master/article/2021/gcp-healthcare-consent-api.md](https://github.com/xitu/gold-miner/blob/master/article/2021/gcp-healthcare-consent-api.md)
> * 译者：
> * 校对者：

# Google Cloud Releases Its Healthcare Consent Management API to General Availability

Google Cloud recently announced it would release its Healthcare Consent Management API to general availability to provide healthcare application developers and clinical researchers a simple way to manage individuals' consent over health data use. The Healthcare Consent Management API is part of the [Cloud Healthcare API offering](https://cloud.google.com/healthcare) on the Google Cloud Platform (GCP).

The Healthcare Consent Management API is the latest addition to the Cloud Healthcare API after it became [generally available](https://www.infoq.com/news/2020/04/google-healthcare-api-ga/) in April last year. Moreover, the company later in December [added](https://www.infoq.com/news/2020/12/google-healthcare-ai-ml/) Healthcare Natural Language API and AutoML Entity Extraction for Healthcare.

The public cloud provider [introduced](https://cloud.google.com/blog/topics/healthcare-life-sciences/googles-healthcare-consent-management-api-protects-user-data) a public preview of the Healthcare Consent Management API in the fall of last year. Since then, early adopters have used the API to create personalized patient portals, securely integrate data into clinical workflows based on patient consent, and develop virtual clinical trials. With the current COVID-19 pandemic, healthcare organizations have quickly adopted concepts like virtual care and remote trials – hence patient consent becomes more apparent and requires an easy and secure way. Furthermore, Jameson Rogers, Ph.D., product manager, Google Cloud Healthcare & Life Sciences, wrote in a Google Cloud [blog post](https://cloud.google.com/blog/topics/healthcare-life-sciences/google-cloud-healthcare-consent-management-api-generally-available):

> The explosion of rich data generated by devices such as glucose monitors, wearables, and other sources have emphasized the importance of patient consent and privacy, as patients and caregivers look to safely incorporate data from more sources into their care plans.

With the Healthcare Consent Management API application, developers can quickly create applications to empower patients to better track, modify, and revoke consent around the use of their data. Furthermore, with the patient's permission, the data can be ingested into the Google Cloud for further usages, like analysis for clinical trials.

![Consent Architecture](https://cloud.google.com/healthcare/images/consent_architecture.svg)

Google is not the only public cloud vendor providing healthcare capabilities in the cloud. Microsoft, for instance, [offers the Azure API for Fast Healthcare Interoperability Resource (FHIR)](https://www.infoq.com/news/2019/11/azure-api-fhir-ga/) since November 2019 as part of a series of APIs to help customers with machine learning on protected health information in the cloud. And AWS offers its [Medical Comprehend service](https://aws.amazon.com/comprehend/medical/), which leverages machine learning to extract relevant medical information from unstructured text.

Google Cloud is now taking their offering further with the Consent Management API as [Holger Mueller](https://twitter.com/holgermu), principal analyst and vice president at Constellation Research Inc., told InfoQ:

> APIs are a powerful way to reduce complexity for enterprises, as they only need to use the API correctly, and it takes care of the complex processes that run behind it. Consent in Healthcare is one of these processes characterized by complexity and bureaucracy. It is good to see cloud providers like Google offering a consent API for enterprises to power their next-generation applications. That reduces complexity and saves a few million trees and a few soccer fields of office space where the consent forms are stored in paper form.

Lastly, developers looking to leverage the Healthcare Consent Management API can find more details through the [how-to guides](https://cloud.google.com/healthcare/docs/how-tos/consent) and [documentation](https://cloud.google.com/healthcare/docs/concepts/consent). Pricing details of the Cloud Healthcare API are available on the [pricing page](https://cloud.google.com/healthcare/pricing).

> 如果发现译文存在错误或其他需要改进的地方，欢迎到 [掘金翻译计划](https://github.com/xitu/gold-miner) 对译文进行修改并 PR，也可获得相应奖励积分。文章开头的 **本文永久链接** 即为本文在 GitHub 上的 MarkDown 链接。

---

> [掘金翻译计划](https://github.com/xitu/gold-miner) 是一个翻译优质互联网技术文章的社区，文章来源为 [掘金](https://juejin.im) 上的英文分享文章。内容覆盖 [Android](https://github.com/xitu/gold-miner#android)、[iOS](https://github.com/xitu/gold-miner#ios)、[前端](https://github.com/xitu/gold-miner#前端)、[后端](https://github.com/xitu/gold-miner#后端)、[区块链](https://github.com/xitu/gold-miner#区块链)、[产品](https://github.com/xitu/gold-miner#产品)、[设计](https://github.com/xitu/gold-miner#设计)、[人工智能](https://github.com/xitu/gold-miner#人工智能)等领域，想要查看更多优质译文请持续关注 [掘金翻译计划](https://github.com/xitu/gold-miner)、[官方微博](http://weibo.com/juejinfanyi)、[知乎专栏](https://zhuanlan.zhihu.com/juejinfanyi)。