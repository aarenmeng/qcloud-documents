
## 生成 CSR 文件

生成 Certificate Signing Request(CSR)：
 <img src="//mccdn.qcloud.com/static/img/d9a5bfba8bd35bc9d32cea2e8c1e201b/image.png" width=640 />
填写您的邮箱（这个邮箱是申请 AppID 的付费帐号）和常用名称（一般默认是计算机名，不用更改），并选择保存到硬盘：
 <img src="//mccdn.qcloud.com/static/img/712cd7c494f0bb36ebb1126ed3757046/image.png" width=640 />
单击继续：
 <img src="//mccdn.qcloud.com/static/img/fa7f2ee807a551ff09e052d317739406/image.png" width=640 />
 已经在本地生成了一个 TXIMDemoAPS.certSigningRequest 的 CSR 文件。

## 生成 App ID

登录 developer.apple.com，选择 Member Center ：
<img src="//mccdn.qcloud.com/static/img/5d2f381f85718559b708390aa3cc7c5e/image.png" width=640 />
进入后选择 Certificates，Identifiers & Profiles：
<img src="//mccdn.qcloud.com/static/img/133a316468454a2514201111b785332d/image.png" width=640 />
再选择 Identifiers 进行到 Identifiers 管理页：
<img src="//mccdn.qcloud.com/static/img/441c328294ddca6e9906e3f35d989ea2/image.png" width=640 />
生成 App ID：
Identifiers 的右侧列表中，如果您已经配置您的应用，跳到第3步，否则单击“+”号添加 App ID。
<img src="//mccdn.qcloud.com/static/img/b1c257146018480e246be45f3889d5c4/image.png" width=640 />
输入您的 App ID 描述信息，可以输入工程名；Bunble ID（在工程的 General 信息中），一般格式为 com.youcompany.youprojname，选择需要支持 Push Notification，Continue：
<img src="//mccdn.qcloud.com/static/img/1b403cd5e1dcccf0153eb23b3e87d8c6/image.png" width=640 />
Submit 提交：
<img src="//mccdn.qcloud.com/static/img/ff761eaa370eb22b487c7b549e2ceab1/image.png" width=640 />

## 创建 App 的 APS 证书

回到 App IDs 选择您需要推送的 App。展开单击“Edit”：
<img src="//mccdn.qcloud.com/static/img/1d4b185be699bda3f1bb87b8232e7907/image.png" width=640 />
找到最底部的 Push Notifications，单击“Create Cerifcate…”创建 push 证书，这里**开发环境的证书和发布环境的证书需要分别创建，也就是相同的流程要走两遍**：
<img src="//mccdn.qcloud.com/static/img/17f9f4648c333306abc307777557075e/image.png" width=640 />
单击 Continue 继续：
<img src="//mccdn.qcloud.com/static/img/7674151826f92e8209d6cbb8ac7dd74d/image.png" width=640 />
上传创建好 CSR 文件（参照第一节）xxx.certSigningRequest（例子为：TXIMDemoAPS.certSigningRequest），单击“Generate”：
<img src="//mccdn.qcloud.com/static/img/9e043e3c71ebe7fd5403fb52390642e7/image.png" width=640 />
aps 证书创建成功了，单击 Download 下载到本地。（文件名：开发版本为 aps_development.cer，发布版本为 aps.cer）：
<img src="//mccdn.qcloud.com/static/img/9f112c857a992f6b8636a352963a21c4/image.png" width=640 />
单击 Done，您会发现该环境的 push 配置状态已经 Enabled：
<img src="//mccdn.qcloud.com/static/img/c932c852924ac49c0823e9e5ba84a6a4/image.jpg" width=640 />
注意：有的 App ID 的 Apple Push Notification service 列是灰色的，并且不允许使用 Configure 按钮，这是因为 APNS 不支持带通配符的 App ID。

## 生成 Push 证书

导入证书
双击上一节下载的文件（aps_development.cer 和 aps.cer）将其安装到电脑，在“钥匙串访问”中，可以看到已经导入的证书。
<img src="//mccdn.qcloud.com/static/img/b51376be915c6a2c0ec2c6f7d12ac5fb/image.png" width=640 />
右键选择导出为 p12 文件, （例：存储为 TXIMDemoAPS.p12）：
<img src="//mccdn.qcloud.com/static/img/969cd435f95a07ffbe6460c7f8b749f8/image.png" width=640 />
注意：开发版本证书只有在 debug 模式下开发的时候会生效，正式发布版本的证书，一定要使用正式版本的证书。

## 生成 Provisioning Profile 文件（PP 文件）
生成对应的描述文件，这里演示开发版描述文件的创建（发布版本的创建流程一样，用户可以自行操作），单击"Continue"
<img src="//mccdn.qcloud.com/static/img/195f72d281e3f11d22b233c9dab87b7b/image.png" width=640 />
选择3.3步骤中创建推送证书那个 App ID，单击"Continue"，
<img src="//mccdn.qcloud.com/static/img/e2aac5aa523d8ed1b49701ee52e62c58/image.png" width=640 />
选择3.3中创建的开发版推送证书（创建发布版描述文件时，选择3.3中创建的发布版推送证书），单击"Continue"，
<img src="//mccdn.qcloud.com/static/img/cf37c59285c20f1b17b29caf18fbb62f/image.png" width=640 />
选择需要加入开发的设备，只有加入了的设备才能进行真机调试，创建发布版本时没有这个步骤，单击"Continue",
<img src="//mccdn.qcloud.com/static/img/49f2c471766dfd91897c27ec3c7c0a4a/image.png" width=640 />
输入 PP 文件的名称，这里以 IMDevPP 为例
<img src="//mccdn.qcloud.com/static/img/893bf26cf3bb3d7c6ed0a7c626941f8a/image.png" width=640 />
生成 PP 文件完成
<img src="//mccdn.qcloud.com/static/img/ebc8de7f1f26ee244ccd18a0566e0f87/image.png" width=640 />

注：以上所有的步骤，除了生成 p12 文件时必须要下载证书安装到本地，其它生成的文件都可以不下载到本地。

检查生成的 PP 文件
查看 pp 文件的状态一定要为 Active
<img src="//mccdn.qcloud.com/static/img/9d93ca1d2952503c0f423b6c7419bcc8/image.png" width=640 />
单击 PP 文件进入详细资料页面，状态也要是 Active
<img src="//mccdn.qcloud.com/static/img/74ace2bdacc1db038363589c36d2fc82/image.png" width=640 />
## Xcode 中的配置
新版 Xcode 已经不需要手动配置证书和描述文件了，只需在 General 中选择正确的 Team，Fix Issue 即可，这也是上面所说的不用下载证书到本地安装的原因
<img src="//mccdn.qcloud.com/static/img/fa11494e822b8ce34b6c03a436805275/image.png" width=640 />
