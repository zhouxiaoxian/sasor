
下载 [Jenkins](https://www.jenkins.io/)

## 安装：

服务端口设置： 18080

JAVA 只支持 java 21 和 java 25

[Java Downloads | Oracle](https://www.oracle.com/java/technologies/downloads/#java25)



Jenkins 将作为 **Windows 服务**安装。你可以通过浏览来验证这一点 **服务**区如下所示：

![[jenkins win server.png]]


## 安装后安装向导[](https://www.jenkins.io/doc/book/installing/windows/#post-installation-setup-wizard)

下载、安装并运行 Jenkins 后，安装后安装向导会开始。

这个设置向导会带你完成几个快速的“一次性”步骤，解锁 Jenkins，用插件自定义，并创建第一个管理员用户，通过这个用户继续访问 Jenkins。

### [](https://www.jenkins.io/doc/book/installing/windows/#unlocking-jenkins)解锁詹金斯[](https://www.jenkins.io/doc/book/installing/windows/#unlocking-jenkins)

当你首次使用新的Jenkins手柄时，系统会要求你用自动生成的密码解锁它。

第一步

浏览 'http://localhost:18080' （或安装时你设置的Jenkins端口），等解锁**Jenkins**页面出现。
![解锁詹金斯页面](https://www.jenkins.io/doc/book/resources/tutorials/setup-jenkins-02-unlock-jenkins-page.png)

第二步

初始管理员密码应在 Jenkins 安装路径下找到（该路径设置在 Jenkins 安装的第 2 步）。 对于默认安装位置为 C：\Program Files\Jenkins，可以在 C：\Program Files\Jenkins\secrets 下找到一个名为 **initialAdminPassword** 的文件。 不过，如果选择了 Jenkins 安装的自定义路径，那么你应该检查该位置的 **initialAdminPassword** 文件。

![詹金斯初始密码位置](https://www.jenkins.io/doc/book/resources/tutorials/windows-initial-password-location.png)

第三步

打开高亮文件，复制 **initialAdminPassword** 文件的内容。

![詹金斯初始密码文件](https://www.jenkins.io/doc/book/resources/tutorials/windows-initial-password-file.png)

步骤4

在**解锁Jenkins**页面，将此密码粘贴到**管理员密码**字段，点击**继续**。  
**注释：**

- 你也可以从Jenkins主目录中的**jenkins.err.log**文件获取初始管理员密码。
    

![Windows Jenkins 日志文件](https://www.jenkins.io/doc/book/resources/tutorials/windows-jenkins-log.png)

在新安装的Jenkins系统中，必须在安装向导中输入该密码，才能访问Jenkins的主界面。 如果你跳过设置向导中的后续用户创建步骤，这个密码也将作为默认管理员账户的密码（用户名为“admin”）。

### [](https://www.jenkins.io/doc/book/installing/windows/#customizing-jenkins-with-plugins)用插件定制Jenkins[](https://www.jenkins.io/doc/book/installing/windows/#customizing-jenkins-with-plugins)

[解锁詹金斯](https://www.jenkins.io/doc/book/installing/windows/#unlocking-jenkins)后，会出现**“定制詹金斯**”页面。 在这里，你可以在初始设置中安装许多有用的插件。

点击显示的两个选项之一：

- **安装推荐插件**——安装基于大多数常见用例的推荐插件集。
    
- **选择安装插件**——选择最初安装哪一组插件。 当你第一次进入插件选择页面时，默认会选择推荐的插件。
    

|   |   |
|---|---|
||如果你不确定需要哪些插件，可以选择**“建议安装”** 插件。 你可以在以后安装（或移除）更多的 Jenkins 插件 通过 Jenkins 中的 [**Manage Jenkins**](https://www.jenkins.io/doc/book/managing) > [**插件**](https://www.jenkins.io/doc/book/managing/plugins/)页面。|

设置向导显示Jenkins的配置进展以及你选择的Jenkins插件安装过程。这个过程可能需要几分钟。

### [](https://www.jenkins.io/doc/book/installing/windows/#creating-the-first-administrator-user)创建第一个管理员用户[](https://www.jenkins.io/doc/book/installing/windows/#creating-the-first-administrator-user)

最后，在[用插件定制 Jenkins](https://www.jenkins.io/doc/book/installing/windows/#customizing-jenkins-with-plugins) 后，Jenkins 会让你创建第一个管理员用户。

1. 当“**创建第一管理员用户**”页面出现时，在相应字段中指定管理员用户的详细信息，然后点击**“保存并完成**”。
    
2. 当**Jenkins准备好**页面出现时，点击**“开始使用Jenkins**”。  
    **注释：**
    
    - 本页可能表明**詹金斯几乎准备好了！**如果是这样，请点击**“重新开始**”。
        
    - 如果页面在一分钟后不会自动刷新，请使用浏览器手动刷新页面。
        
    
3. 如有需要，请用您刚创建的用户凭证登录Jenkins，您就可以开始使用Jenkins了！
    

## [](https://www.jenkins.io/doc/book/installing/windows/#troubleshooting-windows-installation)排查Windows安装问题[](https://www.jenkins.io/doc/book/installing/windows/#troubleshooting-windows-installation)

### [](https://www.jenkins.io/doc/book/installing/windows/#invalid-service-logon-credentials)无效的服务登录凭证[](https://www.jenkins.io/doc/book/installing/windows/#invalid-service-logon-credentials)

![无效服务登录凭证](https://www.jenkins.io/doc/book/resources/tutorials/windows-invalid-service-logon-credentials.png)

在安装服务以域用户账户运行时，该账户必须有权以服务身份登录。该登录权限严格适用于本地计算机，必须在本地安全策略中授予。

请执行以下步骤，编辑您想定义“登录为服务”权限的计算机的本地安全策略：

1. 用管理员权限登录电脑。
    
2. **打开管理工具**，打开**本地安全策略**，或在运行对话框（Win + R）中输入并按回车。`secpol.msc`
    
3. 如果您的系统缺少**本地安全策略**，请参阅 Windows [10 Home 在哪里下载 GPEdit.msc 中的答案？](https://answers.microsoft.com/en-us/windows/forum/all/where-to-download-gpeditmsc-for-windows-10-home/c39bd656-8d4a-4374-be39-394c09deec4e)关于 Microsoft 社区的故障排除问题
    
4. 在**本地安全策略**窗口中，展开**本地政策**并点击**用户权限分配**
    
5. 在右侧面板，右键点击“**作为服务登录**”，然后选择属性。
    
6. 点击**添加用户或组......**按钮添加新用户。
    
7. 在**“选择用户或组”**对话框中，找到你想输入的用户并点击**确定**
    
8. 点击**“确定****”在“登录为服务属性**”中保存更改。
    

完成上述步骤后，尝试用新增用户再次登录。


### 安装SASUnit Jenkins插件

访问Jenkins**插件管理器，>可使用**。搜索_SASUNIT_，选择并安装，无需重启。安装成功后，你应该会看到：

![1600-SAS9-Test-Automation-Jenkins-plugin-SASUnit-1024x274.png](https://communities.sas.com/t5/image/serverpage/image-id/49276i7385534341F6C86C/image-dimensions/798x213?v=v2 "1600-SAS9-Test-Automation-Jenkins-plugin-SASUnit-1024x274.png")

### 配置SASUnit Jenkins插件

你可以查看 [Jenkins SASUnit 插件文档](https://plugins.jenkins.io/sasunit-plugin/)。不过，请允许我引导你，帮你节省盲目寻找的时间。

去管理**Jenkins的全局工具配置>**。在SASUnit中，查找**SASUnit >SASUnit安装**。

![1610-SAS9-Test-Automation-Jenkins-Global-tool-configuration-SASUnit.png](https://communities.sas.com/t5/image/serverpage/image-id/49277iAC9C065B8C0DAB25/image-dimensions/410x427?v=v2 "1610-SAS9-Test-Automation-Jenkins-Global-tool-configuration-SASUnit.png")

添加SASUnit：

- 名字是_：SASUnit 2.0.2，_和版本一样。
- 将 Home Directory 指向 **/**（这是你在上一篇[帖子](https://communities.sas.com/t5/SAS-Communities-Library/Automate-SAS-9-Code-Unit-Tests-in-a-DevOps-Pipeline-with-Jenkins/ta-p/681941)中定义的SASUNIT_ROOT变量）。

![1620-SAS9-Test-Automation-Jenkins-Global-tool-configuration-SASUnit-advanced.png](https://communities.sas.com/t5/image/serverpage/image-id/49278i85FEA7361D6BA8AD/image-dimensions/438x410?v=v2 "1620-SAS9-Test-Automation-Jenkins-Global-tool-configuration-SASUnit-advanced.png")

顺便说一句，你可以配置自动安装SASUnit，我觉得这是个很棒的功能！通过自动安装程序，你可以编写安装步骤脚本，这样如果你更改代理，SASUnit 会在运行前自动安装。

### 在Jenkins代理上配置SASUnit的位置

我们需要告诉Jenkins，SASUnit安装在代理上的位置，也就是SAS 9机器。去Jenkins Nodes看看。找到你的SAS 9特工。检查工具位置（见底部）。

![1630-SAS9-Test-Automation-Jenkins-agent-tool-locations.png](https://communities.sas.com/t5/image/serverpage/image-id/49279i066A3D2FD4CAF6B1/image-dimensions/689x702?v=v2 "1630-SAS9-Test-Automation-Jenkins-agent-tool-locations.png")

![1640-SAS9-Test-Automation-Jenkins-agent-tool-locations2.png](https://communities.sas.com/t5/image/serverpage/image-id/49280iE9462EEE09F0FC26/image-dimensions/633x289?v=v2 "1640-SAS9-Test-Automation-Jenkins-agent-tool-locations2.png")

选择SASUnit，指向SAS 9 Windows机器上的SASUNIT_ROOT路径：_C：\sasunit_。这正是你之前帖子中在_配置SASUnit批处理文件_时需要更改的位置。[](https://communities.sas.com/t5/SAS-Communities-Library/Automate-SAS-9-Code-Unit-Tests-in-a-DevOps-Pipeline-with-Jenkins/ta-p/681410)

## Jenkins 单元测试流程

### 定义管道

创建一个新的流水线。限制运行到定义的SAS 9代理，其中安装了SASUnit。

![1650-SAS9-Test-Automation-Jenkins-pipeline1.png](https://communities.sas.com/t5/image/serverpage/image-id/49281i134D2F39397768A3/image-dimensions/523x658?v=v2 "1650-SAS9-Test-Automation-Jenkins-pipeline1.png")

点击代理标签下的“高级”。Jenkins需要一个工作区来运行这些工件。

填写 SASUnit 批处理命令的位置，位于 \bin 文件夹中，C_：\sasunit\example\bin_ 。因为我们想要来自_C：\sasunit\example\_文件夹的伪影_，所以_把位置指向C_：\sasunit\example_，向上一级。

![1660-SAS9-Test-Automation-Jenkins-pipeline2-1024x427.png](https://communities.sas.com/t5/image/serverpage/image-id/49282i32E1DC6631D80F9E/image-dimensions/779x325?v=v2 "1660-SAS9-Test-Automation-Jenkins-pipeline2-1024x427.png")

### 在管道中执行SASUnit

添加一个第一步，导航到SASUNIT_ROOT文件夹C_：\sasunit_。

添加第二步“执行SASUnit测试套件”，通过批处理文件执行SASUnit。

这个步骤可以在Jenkins找到，因为你[安装了SASUnit插件](https://communities.sas.com/t5/SAS-Communities-Library/Automate-SAS-9-Code-Unit-Tests-in-a-DevOps-Pipeline-with-Jenkins/ta-p/681410)。该可执行文件对应于 _C：\sasunit\example\__bin\sasunit9.4.windows.en.ci.cmd_。

![1670-SAS9-Test-Automation-Jenkins-pipeline-step1.png](https://communities.sas.com/t5/image/serverpage/image-id/49283iEC1A45AE9D3AAA4B/image-dimensions/470x351?v=v2 "1670-SAS9-Test-Automation-Jenkins-pipeline-step1.png")

选择_sasunit9.4.windows.en.ci.cmd，ci_代表“连续积分”，适用于Jenkins。

_sasunit9.4.windows.en.ci.cmd_和_sasunit.9.4.windows.en.overwrite.ci.cmd_的区别是什么？_En.ci.cmd_只会查看测试单元文件夹中的更改，而_overwrite.en.ci.cmd_会从头重新做所有测试。

### 添加一个构建后操作来归档这些神器

执行时会生成_.log_或_junit.xml_文件等伪影。

JUnit 是最初被许多 Java 应用程序用作单元测试框架的单元框架之一。默认情况下，JUnit 测试会生成简单的报告 XML 文件用于测试执行。这些XML文件随后可用于根据测试需求生成任何自定义报告。

![1670-SAS9-Test-Automation-Jenkins-pipeline-step2.png](https://communities.sas.com/t5/image/serverpage/image-id/49284i56E3D2C832058B04/image-dimensions/639x411?v=v2 "1670-SAS9-Test-Automation-Jenkins-pipeline-step2.png")

文件路径相对于管道定义中定义的自定义工作区 _C：\sasunit\example_。

这些工件在构建时存储在 Jenkins 管道工作区中。

![1680-SAS9-Test-Automation-Jenkins-workspace.png](https://communities.sas.com/t5/image/serverpage/image-id/49285iA36A60285CA5D7D8/image-dimensions/729x344?v=v2 "1680-SAS9-Test-Automation-Jenkins-workspace.png")

### 如何在Jenkins中显示构建和测试结果

通过使用 Jenkins 的构建后步骤“发布 JUnit 测试结果报告”，你可以显示你的 SASUnit 构建结果。剩下的就是告诉詹金斯该去哪里找这个档案。**/*junit.xml 会搜索自定义工作区文件夹 _C：\sasunit\example_ 的所有文件夹，寻找名为 _junit.xml_ 的文件：

![1670-SAS9-Test-Automation-Jenkins-pipeline-step3.png](https://communities.sas.com/t5/image/serverpage/image-id/49286i33E31505CB19DEE9/image-dimensions/720x443?v=v2 "1670-SAS9-Test-Automation-Jenkins-pipeline-step3.png")

健康报告放大因子定义了稳定或不稳定构建的阈值。

### SASUnit 生成 junit.xml 文件

文件包含通过测试（断言）的数量，你可以了解测试结果的概览。

构建状态将由创建的 JUnit-XML 自动确定。如果没有失败断言，构建是稳定的。如果断言失败，构建就是不稳定的。

如果您在 **reportSASUnit** 的宏调用中指定 _o_junit=1，SASUnit_ 将生成 JUnit-XML 文件：

```sas
%reportsasunit(
i_language =%upcase(%sysget(SASUNIT_LANGUAGE))
,o_html     =1
,o_junit    =1
);
```

JUnit.xml文件和HTML文档都创建在_C：\sasunit\example\docsasunit\en\rep_文件夹中。

### 如何在 Jenkins 中显示 SASUnit HTML 报表

在Jenkins中显示SASUnit文档非常简单。你可以使用发布后的构建步骤“发布HTML报告”：

![1670-SAS9-Test-Automation-Jenkins-pipeline-step4.png](https://communities.sas.com/t5/image/serverpage/image-id/49287i89877E566FFC0596/image-dimensions/608x293?v=v2 "1670-SAS9-Test-Automation-Jenkins-pipeline-step4.png")

## 测试结果

最后，当我们运行流水线时，会得到结果，这些结果见上一篇文章《[可视化测试结果](https://communities.sas.com/t5/SAS-Communities-Library/Automate-SAS-9-Code-Unit-Tests-in-a-DevOps-Pipeline-with-Jenkins/ta-p/681410)》。

![1430-SAS9-测试-自动化-Jenkins-pipeline-Tests （1）.png](https://communities.sas.com/t5/image/serverpage/image-id/49288i1FF13D469F6E8CE5/image-dimensions/548x602?v=v2 "1430-SAS9-Test-Automation-Jenkins-pipeline-Tests (1).png")

## 结论

我们研究了如何在Jenkins中设置测试自动化，以及调用SASUnit测试框架和显示测试结果所需的配置。