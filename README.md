
******************************************
Launching the project
******************************************

STEP 1

Create folder for project 
(For example, this folder is named "MyAPI")

******************************************

STEP 2

Connect to git and pull project

    git init;
    git remote add origin https://github.com/denetorus/MSUGP.git
    git pull https://github.com/Denetorus/MSUPG.git


******************************************

STEP 3

Update dependencies from composer

    composer update

******************************************

STEP 4

Make directory "config" in the root directory
Make 2 files in config directory, filling DB and ugp_auth information:

console.json

        {
            "default": {
                "controllers_path": "console",
                "router": "router\\RouterConsole",
                "path": "console",
                "sign": "sign\\SignConsole"
            },

            "props":{
                "db_params": {
                    "dsn": "pgsql:host=hostname;port=5432;dbname=DBNAME",
                    "user": "DBUserName",
                    "password": "DBPassword"
                },
                "ugp_auth": {
                    "login": "login",
                    "password": "password"
                }
            }
        }

web.json

        {
            "default": {
                "controllers_path": "web",
                "router": "router\\RouterWeb",
                "sign": "sign\\SignWeb"
            },

            "routers": [
                {
                    "path": "rest",
                    "router": "router\\RouterRest",
                    "sign": "sign\\SignWeb"
                }
            ],
        
            "props":{
                "db_params": {
                    "dsn": "pgsql:host=hostname;port=5432;dbname=DBNAME",
                    "user": "DBUserName",
                    "password": "DBPassword"
                },
                "ugp_auth": {
                    "login": "login",
                    "password": "password"
                }
        
            }
        }




CHECK:

On this STEP you can check project throw the terminal.

Open terminal (console).
Go to the directory when placed project files ("MyAPI")
Run command:

    php sk test

You have to see message

    test console is execute

If you see the mistake

    'php' is not recognized as an internal or external command, 
    operable program or batch file."

You can fix it one of a methods for your system.
The method for Windows was description here

    https://www.codeandtuts.com/php-is-not-recognized-as-an-internal-or-external-command/ 

******************************************

STEP 5

Configure ENTRY POINT in the PHP server to directory "/gate"

(For our example:

If you use Windows Apache :
Open Apache configure file "httpd.conf"
In the file look for parameter "Document Root".
Fill parameter:

    DocumentRoot "Path_to_directory/MyAPI/gate" 

If you use Linux Apache2 :
Change Sites-available configure file parameter

    DocumentRoot "Path_to_directory/MyAPI/gate" 

If you use Linux Nginx :
Change Sites-available configure file parameter

    root Path_to_directory/MyAPI/gate 


)

CHECK:

- Restart Apache/Nginx
- Go to the link

        http://IP_SITE
    
    

