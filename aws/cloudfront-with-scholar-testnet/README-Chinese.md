# Amazon Web Services

## 配置AWS Cloudfront和ScholarTestnet

#### [Click me switch to English version](README.md)

使用GitHub页面设置网站是发布自定义网站的最简单方法之一，而且无需支付任何网站托管费用。 您只需将`index.html`添加到您的根存储库并在设置中单击发布即可。使用GitHub页面的一个缺点是无法使用带SSL的自定义域（加密和安全的网站）。

以下是本教程中要讲述的内容：

- 使用GitHub Pages设置网站
- 从AWS请求SSL证书
- 配置AWS Cloudfront
- 使用AWS Route 53路由您的CNAME

### 使用GitHub Pages设置网站

在你的一个GitHub仓库的根目录中包含一个`index.html`，然后转到**（设置）**并启用GitHub页面。 您可以包含自定义域名，但SSL不支持自定义域。

例如，我们已经使用GitHub Pages配置了ScholarTesnet：

https://github.com/ScholarTestnet/ScholarTestnet.github.io

![image](https://user-images.githubusercontent.com/550895/38103012-17a6c49e-3353-11e8-95e3-67f7757e6308.png)

### 从AWS请求SSL证书

转到 **服务** => **证书管理** => **请求证书**

在右上角，确保您位于**美国东部（弗吉尼亚北部）**，因为必须在该地区配置证书才能在将来的步骤中被CloudFront检测到。

<img src="https://user-images.githubusercontent.com/550895/38103041-32bd1f4e-3353-11e8-8397-ac8e24a4644a.png" width=500/>

为将来要添加的任何子域添加根域和通配符（最常见的是“www”）。

<img src="https://user-images.githubusercontent.com/550895/38103053-3e47c800-3353-11e8-821f-4f56836d5fc4.png" width=500/>

完成DNS验证或电子邮件验证，如果您选择DNS验证，您可以让AWS通过简单的点击创建53路由记录。

### 配置AWS Cloudfront

转到 **服务** => **CloudFront分配** => **创建分配** => **Web /入门**

将您的GitHub页面URL添加到**Origin Domain Name**。

> 注意：如果您在同一个GitHub组织下有许多GitHub页面，则需要通过将其包含在原始路径(**Origin Path**）中来指定特定项目。

<img src="https://user-images.githubusercontent.com/550895/38103082-5c100aaa-3353-11e8-88f7-dd40a5767e0f.png" width=500/>

将查看器协议策略更改为“**将HTTP重定向到HTTPS**”，这样您的所有查看者将被重定向到仅安全的HTTPS网站。

<img src="https://user-images.githubusercontent.com/550895/38103102-6d8154ce-3353-11e8-985f-74acc7d9ec23.png)" width=500/>

将您的子域添加到“**别名记录（CNAME）**”。 该域名必须与您先前创建的SSL证书相匹配。

其次，通过选择SSL证书的名称来包含自定义SSL证书。

![image](https://user-images.githubusercontent.com/550895/38103121-7fd65b74-3353-11e8-84f4-c41d2f39ca7a.png)

所有其他设置可以保留为默认设置。

选择**“创建分配”(Create Distribution)**

您现在应该在域名下看到一个带有cloudfront.net URL的新分发，此URL将作为使用Route 53的CNAME提供。

![image](https://user-images.githubusercontent.com/550895/38103139-8f92329a-3353-11e8-9f84-d6b0c5202901.png)

### 使用AWS Route 53路由您的CNAME

转到 **服务**=>**路由53** =>**托管区域**

选择您用作GitHub页面域名的某个托管区域。

选择**创建记录集(Create Record Set )**使用cloudfront URL创建CNAME记录。

<img src="https://user-images.githubusercontent.com/550895/38103171-a85f3750-3353-11e8-96f7-fcfbfac55036.png" width=500/>

### 完成

在最终设置好这些配置之后，您应该能够看到您的GitHub页面网站，并且您的自定义域名通过SSL（安全/加密网站）运行。

https://scholar.eosnation.io

![image](https://user-images.githubusercontent.com/550895/38103201-bbc44132-3353-11e8-9d1b-644665b8ca82.png)
