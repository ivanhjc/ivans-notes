---
title: "Duplicati: Failed to Restore files"
excerpt: "Reasons and solutions of failing to restore files with Duplicati"
last_modified_at: 2020-11-02
categories:
  - productivity
tags:
  - duplicati
  - backup
---

Working on Windows 10 and after using the web interface to create and run a backup job called "test-backup" with destination pointing to a USB-connected external hard drive successfully, the restoring process is acting strange.

1. If just one file is selected to restore and the source folder remains where it is originally, the file can be restored to a new location but an error such as below is still reported:

    ``` example
    2020-11-02 17:00:13 +08 - [Error-Duplicati.Library.Main.Operation.RestoreHandler-PatchingFailed]: Failed to patch with remote file: "duplicati-b5b00656e1c2e4399905807e3f1c00507.dblock.zip.aes", message: Failed to decrypt data (invalid passphrase?): Invalid password or corrupted data
    ```

	See [complete log](/_demo/duplicati-failed-to-download-files.json){:target="_blank"}.

2. If just one file is selected to restore and the source folder is moved or renamed, the file can't be restored and errors such as below  are reported:

    ``` example
    2020-11-02 16:41:54 +08 - [Error-Duplicati.Library.Main.Operation.RestoreHandler-PatchingFailed]: Failed to patch with remote file: "duplicati-b0c61469407564d3588544e9f1e13423a.dblock.zip.aes", message: Failed to decrypt data (invalid passphrase?): Invalid password or corrupted data
    2020-11-02 16:41:54 +08 - [Error-Duplicati.Library.Main.Operation.RestoreHandler-RestoreFileFailed]: Could not find a part of the path 'D:\test-backup\【5】剑桥雅思真题5.pdf'.
    ```
	See [complete log](/_demo/duplicati-failed-to-download-files-after-renaming.json){:target="_blank"}.

It seems to me that Duplicati is just trying to restore the files from the source folder instead of the backup folder. What's the reason that it can't download a file from a USB-connected hard drive? I've cross-checked the passphrase to make sure it's correct, but even if it's restored from the existing job where no passphrase input is involved, the errors would still show up.

This is probably with relation to the GUI interface because running in command line works just fine. After consulting this [discussion](https://forum.duplicati.com/t/failed-to-restore-failed-to-decrypt/10750/9?u=ivanhjc){:target="_blank"} it's proved to be caused by the browser's auto-filling feature. Some hidden fields may be filled with the saved passwords when you submit the forms where it should be something else. Make sure when the browser asks to save password for you select "Never". You can try to refill the password field with something different to invoke the password-saving dialog. After making the browser never save password for the site restoring from the web interface worked fine for me.

You can use command line if the web interface doesn't work for you. For example, to restore a file to the original location:

``` bash
"D:\programs\Duplicati 2\Duplicati.CommandLine.exe" restore "file://F:\test-backup" "<file>" --encryption-module=aes --compression-module=zip --dblock-size=50mb --passphrase="<passphrase>" --disable-module=console-password-input
```

To restore from b2 (see [The RESTORE command](https://duplicati.readthedocs.io/en/latest/04-using-duplicati-from-the-command-line/#the-restore-command) and [B2 Cloud Storage](https://duplicati.readthedocs.io/en/latest/05-storage-providers/#b2-cloud-storage)):

``` bash
"D:\programs\Duplicati 2\Duplicati.CommandLine.exe" restore "b2://<bucket>/<folder>" "<file>" --b2-accountid="<accountId>" --b2-applicationkey="<applicationKey>" --encryption-module=aes --compression-module=zip --dblock-size=50mb --passphrase="<passphrase>" --disable-module=console-password-input
```

Note that there should be no spaces before and after the `=` sign such as `--b2-accountid = "foo"`, because spaces are shell delimiters. You would see the error message if there are spaces:

``` example
ErrorID: B2MissingUserID
No "B2 Cloud Storage Account ID" given
```
