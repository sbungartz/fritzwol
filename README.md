# fritzwol
Trigger Fritz!Box wake on lan from command line.

This is a slightly modified version of the `wakeup.pl` script from https://github.com/n0rc/fritzbox, so kudos to n0rc for writing the actual script.
The script now supports a configuration file, so that it can be installed in /usr/bin/ and the actual Fritz!Box URLs, user names and host MAC-Addresses can be configured by the user.

# Installation
The Script requires perl and some perl modules to be installed.
The modules can be installed with CPAN:

    sudo cpan LWP::UserAgent Encode Digest::MD5 Config::Simple Term::ReadKey

The script itself is installed by cloning this git repository to an arbitrary location and invoking make in it:

    git clone https://github.com/sbungartz/fritzwol
    cd fritzwol
    sudo make install

It can be uninstalled again with `sudo make uninstall`.

# Usage
Assuming you have a PC attached to a Fritz!Box at home that you want to start remotely and you have already set up wake on lan on your Fritz!Box and tested that it works by clicking in the Fritz!Box GUI.

The configuration has to be in the file `~/.fritzwolconfig` and could look like this:

    [box:homebox]
    url=blablabla.myfritz.net
    port=443
    user=theusername
    
    [host:home]
    box=homebox
    mac=12:34:56:78:90:AB

You can then start the computer with the mac address `12:34:56:78:90:AB` with

    fritzwol home

which will prompt for the Fritz!Box password and then start the respective computer.

    
