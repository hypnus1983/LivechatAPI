## IIS as a web server
The next part will show you how to use the Application Request Routing (ARR) and URL Rewrite features of Internet Information Services (IIS) to implement a forward proxy server.

### Prerequisites
To set up a forward proxy server using ARR, you must have the following:
- IIS 7.0 or above on Windows 2008 (any SKU) or newer with Tracing role service installed for IIS.
- Microsoft Application Request Routing Version 3 and dependent modules
- Minimum of one worker server with working sites and applications.

#### Step 1 - Install ARR
If Application Request Routing Version 3 has not been installed, it is available for download [here](https://www.microsoft.com/en-us/download/details.aspx?id=39715). The download site displayed by this link includes installation instructions.

#### Step 2 - Install URL Rewrite
Install the URL Rewrite module for IIS through the Server Manager. For more information, see [Installing IIS 8.5 on Windows Server 2012 R2](https://docs.microsoft.com/en-us/iis/install/installing-iis-85/installing-iis-85-on-windows-server-2012-r2).

#### Step 3 - Configure ARR as a Forward Proxy
To enable ARR as a proxy, and to create a URL Rewrite rule to enable ARR as a forward proxy, proceed as follows:
1. Open Internet Information Services (IIS) Manager.
2. In the Connections pane, select the **server**.
3. In the server pane, double-click **Application Request Routing Cache**.
![IIS](https://docs.microsoft.com/en-us/iis/extensions/configuring-application-request-routing-arr/creating-a-forward-proxy-using-application-request-routing/_static/image3.jpg)

4. In the **Actions** pane, click **Server Proxy Settings**.
![iis](https://docs.microsoft.com/en-us/iis/extensions/configuring-application-request-routing-arr/creating-a-forward-proxy-using-application-request-routing/_static/image4.jpg)

5. On the **Application Request Routing** page, select **Enable proxy**.
![iis](https://docs.microsoft.com/en-us/iis/extensions/configuring-application-request-routing-arr/creating-a-forward-proxy-using-application-request-routing/_static/image5.jpg)

6. In the **Actions** pane, click **Apply**. This enables ARR as a proxy at the server level.
![iis](https://docs.microsoft.com/en-us/iis/extensions/configuring-application-request-routing-arr/creating-a-forward-proxy-using-application-request-routing/_static/image6.jpg)

#### Step 4 - Add a Proxy Site  
1. Right-click on the **Sites** node in the **Connections** pane and select **Add Website**.
2. Config the website and click **OK** to save settings.
   - Physical path - Could be an empty directory.
   - Host name - Partner own independent-domain, e.g. www.proxyserver.com.
   - Binding type - https   
   ![](https://raw.githubusercontent.com/hypnus1983/LivechatAPI/master/add%20website.png)
3. Explodes the **Sites** node in the **Connections** pane, and click the proxy site.
4. In the server pane, double-click **Compression**.
5. In the **Compression page**, unselect **Enable dynamic content compression**.In the Actions pane, click Apply. This disenables dynamic content compression at the site level.

#### Step 5 - Config URL Rewrite Rules
1. Click the proxy site in **Sites** node in the **Connections** pane. In the **Actions** pane, click **Explore** to open the website's directory.
2. Open the **web.config** by notepad.
3. Edit the file as follows example. Make sure to replace ***www.proxyserver.com*** to the partner own independent-domain, and replace **app.platform.comm100.com** to the Comm100's partner sub-domain.Save the web.config file at last.

```
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="test">
                    <match url="^(.*)" />
                    <conditions>
                        <add input="{HTTP_HOST}" pattern="^www.proxyserver.com$" />
                    </conditions>
                    <action type="Rewrite" url="https://app.platform.comm100.com/{R:1}" />
                </rule>
            </rules>
            <outboundRules>
                <rule name="test" preCondition="IsHTML">
                    <match filterByTags="A" pattern="http.+?/app.platform.comm100.com/(.+)" />
                    <conditions>
                    </conditions>
                    <action type="Rewrite" value="https://www.proxyserver.com/{R:1}" />
                </rule>
                <preConditions>
                    <preCondition name="IsHTML">
                        <add input="{RESPONSE_CONTENT_TYPE}" pattern="^text/html" />
                    </preCondition>
                </preConditions>
            </outboundRules>
        </rewrite>
        <urlCompression doDynamicCompression="false" />
    </system.webServer>
</configuration>

```


#### Step 6 - Test
1. Click the proxy site in **Sites** node in the **Connections** pane. In the **Actions** pane, click **Restart** to restart the website.
2. Type the partner own independent-domian in the brower, e.g. https://www.proxyserver.com. If everything is ok, the brower will lead you to the login page as follows: https://www.proxyserver.com/adminManage/login.aspx. Then the custom of the partner can use the product and the service.
