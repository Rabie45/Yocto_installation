## Yocto installation

Yocto refers to the Yocto Project, an open-source collaboration project under the Linux Foundation. Its هدف (hadaf, Arabic for “goal”) is to provide developers with the tools and processes needed to build custom Linux systems for embedded devices, like routers, smart TVs, and wearables.

in this article we will se how to install Yocto in ubuntu distribution based.

# First:

 - make directory and give it a name (source) using this command

   ‘’’ mkdir source’’’

 - then go to the directory u just created using this command

   ‘’’ cd source ‘’’

 - use the command shown in the documentation

then clone poky repo(Poky is closely related to the Yocto Project for embedded Linux development. Here’s how they connect:
Yocto Project: This is the overarching framework that provides tools, processes, and metadata to build custom embedded Linux distributions.
Poky: Think of Poky as the reference implementation of the Yocto Project. It serves as a foundation and example, showcasing how to use Yocto Project features. Poky includes essential components)

''' git clone git://git.yoctoproject.org/poky '''

then check out the branch using this command

''' git checkout krogoth '''

then initialize build environment as shown in documentation using
the additional build command to create a file called build and build the file on it

''' source oe-init-build-env ../../build '''

it must be looks like that

now you can try to write bitbake to see if it works or not

''' bitbake -h '''

if you got error like that

''' traceback (most recent call last): File “/home/rabi3/Desktop/source/poky/bitbake/bin/bitbake”, line 19, in <module> import bb File “/home/rabi3/Desktop/source/poky/bitbake/lib/bb/init.py”, line 74, in <module> import bb.msg File “/home/rabi3/Desktop/source/poky/bitbake/lib/bb/msg.py”, line 20, in <module> import bb.event File “/home/rabi3/Desktop/source/poky/bitbake/lib/bb/event.py”, line 23, in <module> import bb.compat File “/home/rabi3/Desktop/source/poky/bitbake/lib/bb/compat.py”, line 7, in <module> from collections import MutableMapping, KeysView, ValuesView, ItemsView, OrderedDict ImportError: cannot import name ‘MutableMapping’ from ‘collections’ (/usr/lib/python3.10/collections/init.py) '''

this is because you use python 3 which have deprecated functions so you have to use old distro with python 2.7 and this mentioned in the documentation

the last step is to run this command to build

''' bitbake core-image-minimal ''


the command ''' bitbake core-image-minimal ''' is used in the Yocto Project with Poky to build a specific type of embedded Linux system image.

and it may take a while (may be 2 hours).