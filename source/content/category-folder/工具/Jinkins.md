
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


