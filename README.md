How-To-Find-Your-I2P-Site-Root
==============================

I2P comes with a bundled webserver, one popular in the Java world known as
Jetty, which we use for lots of features, but one of the most important of them
is providing the bundled I2P site that comes with every Java I2P installation,
historically called the "eepSite." Any file you copy to the I2P Site "document
root" will be published to I2P, just like any other webserver. Everyone on the
I2P peer-to-peer network is a first class citizen, and we want them all to start
on equal footing when they learn to host services and share their first content
on I2P. So here's how you use the Default I2P Site:

Step Zero - Make some Stuff!
----------------------------

I can't tell you what to do here, create any content you like! Write a blog,
publish your software, or just share your personal .torrent files. If you want
a place to start, try contributing to the [REDACTED]

Step One - Determine your Platform and Install Location
-------------------------------------------------------

When installed, I2P creates a directory to store the files that it works with,
including the I2P Site document root. To locate the configuration directory,
determine which platform(Windows, Mac OSX, Linux) you are using and refer to the
instructions below.

### Windows

On Windows, the I2P Site docroot is in a hidden directory, so to see it you will
need to either make hidden directories visible or provide the exact path to
Windows Explorer. Hidden files are an organization/visual feature, not a
security feature, so it is OK to unhide them.

To unhide the files, open the Windows Explorer(The program you use to navigate
around your files) and **1)** open the "View" menu, **2)** open "Options" and
**3)** select "Change Folder and Search Options." In the menu that is opened,
**1)** open the "View" tab and **2)** activate "Show Hidden Files and Folders."

To find the Windows eepSite docroot without unhiding the directories, it is
possible to navigate to them directly. Open Windows Explorer, and double-click
the bar at the top where the path is indicated. No you will be able to enter
text into that area, so copy-and-paste the following:

        %LOCALAPPDATA%\I2P\eepsite\docroot

That should take you to C:\\Users\\**username**\\AppData\\Roaming\\I2P\\eepsite\\docroot.
If that does not work, you may have I2P installed as a system application, and
you should try this path instead.

        %PROGRAMDATA%\I2P\eepsite\docroot

**Create a shortcut to that somewhere, so you do't have to go through this**
**whole process again.** **This is very important, you will need this for the**
**next step.**

### Linux/BSD

On Linux and BSD systems, the I2P Site docroot is much easier to find. It is
always installed(by default) to the directory ```$HOME/.i2p``` where $HOME
is the directory owned by the user running I2P. So unless you know for sure you
need to do otherwise, you can always use ```~/.i2p``` to find your I2P
directory.

To test whether this will work for you, open a terminal and use the command:

        ls ~/.i2p/eepsite/docroot

You should see a list of files displayed by the default I2P Site. If not, try
the following instructions.

#### Ubuntu or Debian GNU/Linux

One case where using ```~/.i2p``` will not work is if you installed I2P as a .deb
package on Ubuntu or Debian, then it was installed as it's own system
user(called "i2psvc") to restrict it from accessing other user's files and keep
other applications and other users from manipulating it accidentally, or without
permission. This additonal security means that you will need to enter a password
to copy the files into the directory owned by the i2psvc user. In order to do
this, you will need to prefix your commands with ```sudo -u i2psvc```. In order
to test whether this will work for you, use this command:

        sudo -u i2psvc ls /var/lib/i2p/i2p-config/eepsite/docroot

You should see the list of files displayed by the default I2P Site.

### Mac OSX

Step Two - Copy the Files
-------------------------

Now that you have located your I2P Site docroot(And you know how to find it
again if you need to), the only thing you really need to do is copy the files
there. The most convenient way will depend on your platform, and configuration,
but for the majority of people, a graphical file manager will be perfectly
sufficient.

### Windows

If you found your I2P docroot at C:\\Users\\**username**\\AppData\\Roaming\\I2P\\,
then all you need to do is drag the files from the website into the shortcut you
created in the first step. **That's it!**

#### Windows as a System User

If you found your I2P docroot in %PROGRAMDATA%, then you will need to also
elevate your privileges before you copy the website files into the shortcut that
you created in the first step. Windows may prompt you to elevate your privileges
if you try to copy without them.

### Linux/BSD

If you found your I2P docroot at ~/.i2p/eepsite/docroot, simply copy-and-paste
your website files with your preferred file manager or via the terminal.

#### Debian and Ubuntu GNU/Linux

If you are using a Debian package and thus a system-wide install as the i2psvc
user, then you will need to copy the files with that user's permissions. In
order to do this, you can use either:

        sudo install \
            -o i2psvc -g -i2psvc \
            PATH_TO_WEBSITE_FILES/* \
            /var/lib/i2psvc/i2p-config/eepsite/docroot

or:

        sudo -u i2psvc cp \
            PATH_TO_WEBSITE_FILES/* \
            /var/lib/i2psvc/i2p-config/eepsite/docroot

### Mac OSX

