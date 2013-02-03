SVNCompleteSync
===============

This programm syncs your local folder to a subversion repository.
All new files get added, deleted files will be removed.
The functionality is similar to Mercurial's addremove command but without the similarity option.

There is one single good reason to use this program:
You have autogenerated files that you want to check 
into your subversion repository by your buildsystem.

I use it for my scripted database objects. I first delete all .sql files from 
the working folder (del *.sql /s). Then I generate the scripts into this folder.
After that I run SVNCompleteSync.

Invoke by: SVNCompleteSync "your folder to sync" -m "your optional log message"

This application calls svn status for each folder and sub-folder. Then it calls 'svn add' for files with an unversioned local status and 'svn delete' for files with a missing status. Finally, 'svn commit' is called.

This tool is designed to be useful when you want to track history on files that are generated by tools.

This is a console application written in c#. It uses .Net framework 3.5. The SVN client (SharpSvn) version is 1.6.

Thanks to the people from SharpSvn http://sharpsvn.open.collab.net. This project made all very easy for me.
