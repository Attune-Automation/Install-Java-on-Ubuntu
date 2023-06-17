Pre-seed the 
[debconf](https://manpages.ubuntu.com/manpages/trusty/en/man1/debconf-set-selections.1.html)
database with answers to silence Oracle License Agreement.

To value key is identified in the `oracle-java17-installer.preinst` file.

```
license=oracle-license-v1-3

db_get shared/accepted-$license
if [ "$RET" = "true" ]; then
    echo "$license license has already been accepted" >&2
    exit 0
fi
```