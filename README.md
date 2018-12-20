# Cocoapods git post-checkout
The following will execute pod install between checkouts if needed

## Installation:
* Navigate to your project on terminal.
* Open .git/hooks/post-checkout with your favourite text editor. Create hooks directory if it's not exists.
* Copy and paste the following script:
```
#!/bin/sh
export LANG=en_US.UTF-8

diff "./Podfile.lock" "./Pods/Manifest.lock" > /dev/null
if [ $? != 0 ] ; then
  echo Pod install
  /usr/local/bin/pod install
fi

```
* Set permissions for the post-checkout directory:
```
[sudo] chmod +x .git/hooks/post-checkout
```

Cocoapods will now install from the podfile between checkouts.
