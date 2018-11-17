
## HOW TO INSTALL HUMHUB UNDER IIS 

**IMPORTANT**

The instalation assumes some settings in order to work:

   A. Humhub is at 'public root folder'. We have our webs at **"C:\_wbes_" not at "C:\interpud\..."**

   B. The 'public root folder' is named **"public"** (not "www").
   
   C. **PHP is at "C:\PHP\..."** not under "program files"



### Steps

1. Download zip version of Humhub from https://www.humhub.org/en/download

   and unzip to public IIS folder



2. Add "[web.host](https://github.com/Buliwyfa/humhub_windows_installation/blob/master/web.config)" to public dir



3. Add write permission using  "[_permission_humhub__RUN_as_ADMIN_.bat](https://github.com/Buliwyfa/humhub_windows_installation/blob/master/_permission_humhub__RUN_as_ADMIN_.bat)"
   
   It must be a folder run/execute from folder under the 'public root folder'.
                  
         For example: If web root folder is at C:\interpud\mysite\public\
                      the .bat file must be at C:\interpud\mysite\

4. Create database, go to humhub web and finish the instalation



5. To enable "pretty URLs"

     Edit
	        common.php

     locate at
	        public\protected\config\

     Add:

```php
	<?php

	return [
	    'components' => [
		'urlManager' => [
		    'showScriptName' => false,
		    'enablePrettyUrl' => true,
		],
	    ]
	];
```

6. **Emulate cronojobs on Windows**.

To do it you have **to create your own .bat files and schedule them to run them on intervals, this is done via Windows Task Schedule**. On this code example, there are some **important paths to consider**:

   6.1. Copy folder "[cronojobs](https://github.com/Buliwyfa/humhub_windows_installation/blob/master/cronojobs/)"
        to under the 'public root folder' for your website.

       For example: If web root folder is at **C:\interpud\mysite**\public\
                   the "cronojobs" folder at **C:\interpud\mysite**\cronojobs\
		   

   **NOTE**: our public root folder for a website is named "**public**" not "www" or "html" or....
   Please, fix it if needed.
		   


   6.2. Edit the .bat files and adjunt the PHP paths to php-win.exe
  
      * On example bat files path is "C:\PHP\php-7.0.x-nts-VC14-x64\php-win.exe". Please, fix it!
      
  
   6.3. Update all XML files:
  
      * Change on all XML files "my-humhub-web.com" to your real web name path (path to 'public root folder')
  
      * Update all paths on files from "x:\_path_to_my-humhub-web.com_\cronjobs\" to you path.
      
      * This XML files are tested on Windows 2016 and 2019 server.
      They may work on windows 10 and other version but we have not test them.


   6.4. Open task manager and import the XMLs
  
      * On server: Remember to set the task to run "Run whether user is logged on or not".





