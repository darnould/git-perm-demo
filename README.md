# git-perm-demo

Proving empirically that if the owner's executable bit is set for the file, the executable bit is is distributed across UGW, when stored in Git.  Other file perms are ignored.

This only applies when `core.fileMode` is set to `true`.

To replicate results:
```
docker run -w /dir -v $(PWD):/dir alpine sh -c 'for FILE in *; do PERM=`stat -c "%A %a %N" $FILE | cut -d " " -f 2`; echo "File: ${FILE} Perm: ${PERM}"; done;'
```

QED. ;)
