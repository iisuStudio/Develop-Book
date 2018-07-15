## Tool Package

- [Install IIS](https://docs.microsoft.com/en-us/iis/application-frameworks/scenario-build-a-php-website-on-iis/configuring-step-1-install-iis-and-php)
- [Install PHP](https://windows.php.net/download/)
- [MariaDB](https://downloads.mariadb.org/mariadb/10.3.8/)
- [phpMyAdmin](https://www.phpmyadmin.net/)
- [Git](https://git-scm.com/download/win)
- [Composer](https://getcomposer.org/download/)
- [PhpStorm](https://www.jetbrains.com/phpstorm/download/download-thanks.html?platform=windows)


## 如何安裝在IIS上安裝PHP應用

1.1 安裝 IIS

1. 點擊'開始'，輸入'控制台'，點擊控制台的圖示開啟控制台。
2. 在控制台中，點擊'程式與功能'，並於右側點擊'開啟或關閉Windows功能'。
3. 在功能選項中，選擇並點擊'Internet Information Services'，自動選擇預設功能選項。
4. 在功能選項中，目錄'Internet Information Services/World Wide Web 服務/應用程式開發功能'，選擇CGI及.Net擴充性，點擊確認後執行安裝。

確認IIS安裝成功，於瀏覽器中輸入：
[http://localhost](http://localhost)

將會看到IIS歡迎頁面

1.2 安裝 PHP

- [Web Platform Installer 3.0](https://www.microsoft.com/web/downloads/platform.aspx)
- PHP 7.1.14
- Windows Cache Extension 2.0 for PHP 7.1
- URL Rewrite 2.0

The preferred method to install PHP on a Windows or Windows Server computer is to use Web Platform Installer (Web PI).

To install PHP by using Web PI

1. Open a browser to the following website: Microsoft Web Platform Installer 3.0.
2. Click Download It Now, and then click Run.
3. At the top of the Web Platform Installer window, click Products.
4. Click Frameworks, and then select the current version of PHP.
5. Click Install. The Web Platform Installation page displays the version of PHP and its dependencies that will be installed.
6. Click I Accept. Web PI installs the PHP packages.
7. Click Finish.

1.3 安裝 PHP

If you decide to download PHP and install it manually, the procedures in this section guide you the following tasks:

- Download PHP and the WinCache extension.
- Install PHP and WinCache.
- Add the PHP installation folder to the Path environment variable.
- Set up a handler mapping for PHP.
- Add default document entries for PHP.
- Test your PHP installation.

To keep this procedure simple, install the WinCache extension but do not configure it. You will configure and test WinCache in [Step 2: Configure PHP Settings.](https://docs.microsoft.com/en-us/iis/application-frameworks/scenario-build-a-php-website-on-iis/configuring-step-2-configure-php-settings)

**To download and install PHP and WinCache**

1. Open your browser to Windows for PHP Download Page and download the PHP non-thread-safe zip package.
2. Download the WinCache extension from the List of Windows Extensions for PHP.
3. Extract all files in the PHP .zip package to a folder of your choice, for example C:\PHP\.
4. Extract the WinCache .zip package to the PHP extensions folder (\ext), for example C:\PHP\ext. The WinCache .zip package contains one file (Php_wincache.dll).
5. Open Control Panel, click System and Security, click System, and then click Advanced system settings.
6. In the System Properties window, select the Advanced tab, and then click Environment Variables.
7. Under System variables, select Path, and then click Edit.
8. Add the path to your PHP installation folder to the end of the Variable value, for example ;C:\PHP. Click OK.
9. Open IIS Manager, select the hostname of your computer in the Connections panel, and then double-click Handler Mappings.
10. In the Action panel, click Add Module Mapping.
11. In Request path, type *.php.
12. From the Module menu, select FastCgiModule.
13. In the Executable box, type the full path to Php-cgi.exe, for example C:\PHP\Php-cgi.exe.
14. In Name, type a name for the module mapping, for example FastCGI.
15. Click OK.
16. Select the hostname of your computer in the Connections panel, and double-click Default Document.
17. In the Action panel, click Add. Type Index.php in the Name box, and then click OK.
18. Click Add again. Type Default.php in the Name box, and then click OK.

**To test your PHP installation**

1. Open a text editor, for example Notepad, as Administrator.
2. In a new file, type the following text: <?php phpinfo(); ?>
3. Save the file as C:\inetpub\wwwroot\Phpinfo.php.
4. Open a browser and enter the following URL:

   http://localhost/phpinfo.php

   A nicely formatted webpage is displayed showing the current PHP settings.

1.4. Add Your PHP Application

Once you have IIS and PHP installed, you can add a PHP application to your web server. This section describes how to set up your PHP application on an IIS web server with PHP installed. It does not explain how to develop a PHP application.

**To add a PHP web application**

1. Open IIS Manager.

- For Windows Server 2012, on the Start page click the Server Manager tile, and then click OK. On the Server Manager Dashboard, click the Tools menu, and then click Internet Information Services (IIS) Manager.
- For Windows 8, on the Start page type Control Panel, and then click the Control Panel icon in the search results. On the Control Panel screen, click System and Security, click Administrative Tools, and then click Internet Information Services (IIS) Manager.
2. In the Connections pane, right-click the Sites node in the tree, and then click Add Website.
3. In the Add Website dialog box, type a friendly name for your website in the Site name box.
4. If you want to select a different application pool than the one listed in the Application Pool box, click Select. In the Select Application Pool dialog box, select an application pool from the Application Pool list and then click OK.
5. In the Physical path box, type the physical path of the website's folder, or click the browse button (...) to navigate the file system to find the folder.
6. If the physical path that you entered in step 5 is to a remote share, click Connect as to specify credentials that have permission to access the path. If you do not use specific credentials, select the Application user (pass-through authentication) option in the Connect As dialog box.
7. Select the protocol for the website from the Type list.
8. The default value in the IP address box is All Unassigned. If you must specify a static IP address for the website, type the IP address in the IP address box.
9. Type a port number in the Port text box.
10. Optionally, type a host header name for the website in the Host Header box.
11. If you do not have to make any changes to the site, and you want the website to be immediately available, select the Start Web site immediately check box.
12. Click OK.

## Other

    netstat -ano|findstr "0.0.0.0:80"
    netstat -ano|findstr "0.0.0.0:443"
