

# Compilation #

1. Install MySQL Connector/C++. Download MySQL Connector/C++ from http://dev.mysql.com/downloads/connector/cpp, unzip the downloaded package and copy the files in "lib" and "include" to "/usr/lib/" and "/usr/include/", respectively.


For MAC users, the library might be located in "/opt/local/include" and "/opt/include/cppconn", and please make corresponding changes in "makefile".


2. Type "make" to compile "AuthorReward.cpp".

# Run #
Since edit distance is estimated for two different revisions for any wiki page, it may take time to run AuthorReward at the first time.


1. Before running AuthorReward, export the following environmental variable.

```
   export LD_LIBRARY_PATH=/usr/local/lib
```

2. Below is the command to run AuthorReward.

```
   ./AuthorReward [hostname] [username] [password] [database name] [database table prefix]
```

For example:  export results into a file named "results.txt"
```
./AuthorReward localhost root 123456 ricewiki rice > results.txt &
```

# Extension installation #
Install the extension by adding the following code to your "LocalSettings.php".

```
   require_once( "$IP/extensions/AuthorReward/AuthorReward.php" );
```


Please note that it requires "ToggleDisplay" extension, which is located in the package of AuthorReward. If  "ToggleDisplay" was not installed, please also add the following code to "LocalSettings.php".

```
   require_once( "$IP/extensions/AuthorReward/ToggleDisplay.php" );
```

# Set in crontab #
Since changes in wiki are probably made frequently, it might be better to set AuthorReward to run automatically in background.


1. Open the file named "AuthorReward.sh" and set the corresponding variables according to your wiki.


2. To run at a given time, please type "crontab -e" and install "AuthorReward.sh" in crontab. The time could be set depending on the frequency of changes made in the wiki as well as the server.


For example, the following command is to run "AuthorReward.sh" at every 30 minutes.

```
   */30	*	*	*	*  sh /Your Pathway/AuthorReward.sh 
```

<br />

More updated information can be found at http://cbb.big.ac.cn/software. For any question or comment, please feel free to contact me.