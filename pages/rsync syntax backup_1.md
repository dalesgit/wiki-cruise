## rsync -rvt --info=progress2 "$fromDir2"  "$toDir3/chrome"

n.b. that the "from dir" should end with "/"
the "to dir" does not

## example

eg2
-lptgo

## filtering

rsync -aA -H --numeric-ids -v --progress --delete \
  --filter="merge /tmp/mergefilter.txt" /  /mnt/data/mybackup/

My /tmp/mergefilter.txt says:

+ /mnt/data/i-want-to-rsyncthisdirectory/
- /dev
- /sys/
- /tmp/
- /run/
- /mnt/
- /proc/
- /media/
- /var/swap
- /lost+found/

---

The corrected pattern came with:

+ /mnt/
+ /mnt/data/
+ /mnt/data/i-want-to-rsyncthisdirectory/
- /mnt/data/*
- /mnt/*
- /dev
- /sys/
- /tmp/
- /run/
- /proc/
- /media/
- /var/swap
- /lost+found/

---

https://superuser.com/questions/436070/rsync-copying-directory-contents-non-recursively?newreg=ec836a0b632a434e87fe6124f826e5ed

https://stackoverflow.com/questions/35364075/using-rsync-filter-to-include-exclude-files

> 

rsync -a -f '- /*/*/' /home/dale/ /mnt/chromeos/removable/SD-Card/cruise-25/backup

> This gave me an outline of home with some folders populated.

## Tries

rsync -lptgovzP --exclude /home/dale/.cache --exclude /home/dale/Repositories/ --exclude /home/dale/Downloads/ --exclude /home/dale/Documents/ /home/dale/ /mnt/chromeos/removable/SD-Card/cruise-25/backup 

rsync -avzP --exclude /home/dale/.cache --exclude /home/dale/Repositories/ --exclude /home/dale/Downloads/ --exclude /home/dale/Documents/ /home/dale/ /mnt/chromeos/removable/SD-Card/cruise-25/backup

--exclude .cache, .local/share/nvim

-r recursive
-v verbose
-t times
-a (archive) is all these (for backups)
-P

The -P option is equivalent to --partial --progress. Its purpose is to make it much easier to specify these two options for a long transfer that may be interrupted.

-z compression

One reply said:

It's perfect for backups. My "default" set of switches is -avzP - archive mode, be verbose, use compression, preserve partial files, display progress.

Note: Invariably when the descriptions say "preserve", it means make the destination be like the source.

### 4/2/25 particulars

/home/dale/Repositories
/home/dale/Downloads
/home/dale/Documents
/mnt/chromeos/removable/SD-Card/cruise-25/backup

### It's all of these
-a = -rlptgoD
(my try) = -lptgo

-r, --recursive recurse into directories

-l, --links copy symlinks as symlinks

-p, --perms preserve permissions

-t, --times preserve modification times

-g, --group preserve group

-o, --owner preserve owner (super-user only)

-D same as --devices --specials

--devices preserve device files (super-user only)

--specials preserve special files

It excludes:

-H, --hard-links preserve hard links

-A, --acls preserve ACLs (implies -p)

-X, --xattrs preserve extended attributes

It's perfect for backups. My "default" set of switches is -avzP - archive mode, be verbose, use compression, preserve partial files, display progress.

Note: Invariably when the descriptions say "preserve", it means make the destination be like the source.

## note re. exclude

<https://askubuntu.com/questions/1420321/how-to-exclude-the-multiple-directory-in-rsync>

just add (--exclude) multiples times

rsync -av --exclude some/subdir/linuxconfig --exclude some/other/dir --exclude exampledir /path/to/src/ /path/to/dest/

You can also use --exclude-from and list names of directories to exclude in a file. –

Also think about shell parameter expansion! rsync -av --exclude={'some/subdir/linuxconfig','some/other/dir'} –
Alexis-Emmanuel Haeringer
CommentedOct 25, 2023 at 8:33

## options

-v, --verbose increase verbosity
-q, --quiet suppress non-error messages
--no-motd suppress daemon-mode MOTD (see caveat)
-c, --checksum skip based on checksum, not mod-time & size
-a, --archive archive mode; equals -rlptgoD (no -H,-A,-X)
--no-OPTION turn off an implied OPTION (e.g. --no-D)
-r, --recursive recurse into directories
-R, --relative use relative path names
--no-implied-dirs don't send implied dirs with --relative
-b, --backup make backups (see --suffix & --backup-dir)
--backup-dir=DIR make backups into hierarchy based in DIR
--suffix=SUFFIX backup suffix (default ~ w/o --backup-dir)
-u, --update skip files that are newer on the receiver
--inplace update destination files in-place
--append append data onto shorter files
--append-verify --append w/old data in file checksum
-d, --dirs transfer directories without recursing
-l, --links copy symlinks as symlinks
-L, --copy-links transform symlink into referent file/dir
--copy-unsafe-links only "unsafe" symlinks are transformed
--safe-links ignore symlinks that point outside the tree
-k, --copy-dirlinks transform symlink to dir into referent dir
-K, --keep-dirlinks treat symlinked dir on receiver as dir
-H, --hard-links preserve hard links
-p, --perms preserve permissions
-E, --executability preserve executability
--chmod=CHMOD affect file and/or directory permissions
-A, --acls preserve ACLs (implies -p)
-X, --xattrs preserve extended attributes
-o, --owner preserve owner (super-user only)
-g, --group preserve group
--devices preserve device files (super-user only)
--specials preserve special files
-D same as --devices --specials
-t, --times preserve modification times
-O, --omit-dir-times omit directories from --times
--super receiver attempts super-user activities
--fake-super store/recover privileged attrs using xattrs
-S, --sparse handle sparse files efficiently
-n, --dry-run perform a trial run with no changes made
-W, --whole-file copy files whole (w/o delta-xfer algorithm)
-x, --one-file-system don't cross filesystem boundaries
-B, --block-size=SIZE force a fixed checksum block-size
-e, --rsh=COMMAND specify the remote shell to use
--rsync-path=PROGRAM specify the rsync to run on remote machine
--existing skip creating new files on receiver
--ignore-existing skip updating files that exist on receiver
--remove-source-files sender removes synchronized files (non-dir)
--del an alias for --delete-during
--delete delete extraneous files from dest dirs
--delete-before receiver deletes before transfer (default)
--delete-during receiver deletes during xfer, not before
--delete-delay find deletions during, delete after
--delete-after receiver deletes after transfer, not before
--delete-excluded also delete excluded files from dest dirs
--ignore-errors delete even if there are I/O errors
--force force deletion of dirs even if not empty
--max-delete=NUM don't delete more than NUM files
--max-size=SIZE don't transfer any file larger than SIZE
--min-size=SIZE don't transfer any file smaller than SIZE
--partial keep partially transferred files
--partial-dir=DIR put a partially transferred file into DIR
--delay-updates put all updated files into place at end
-m, --prune-empty-dirs prune empty directory chains from file-list
--numeric-ids don't map uid/gid values by user/group name
--timeout=SECONDS set I/O timeout in seconds
--contimeout=SECONDS set daemon connection timeout in seconds
-I, --ignore-times don't skip files that match size and time
--size-only skip files that match in size
--modify-window=NUM compare mod-times with reduced accuracy
-T, --temp-dir=DIR create temporary files in directory DIR
-y, --fuzzy find similar file for basis if no dest file
--compare-dest=DIR also compare received files relative to DIR
--copy-dest=DIR ... and include copies of unchanged files
--link-dest=DIR hardlink to files in DIR when unchanged
-z, --compress compress file data during the transfer
--compress-level=NUM explicitly set compression level
--skip-compress=LIST skip compressing files with suffix in LIST
-C, --cvs-exclude auto-ignore files in the same way CVS does
-f, --filter=RULE add a file-filtering RULE
-F same as --filter='dir-merge /.rsync-filter'
repeated: --filter='- .rsync-filter'
--exclude=PATTERN exclude files matching PATTERN
--exclude-from=FILE read exclude patterns from FILE
--include=PATTERN don't exclude files matching PATTERN
--include-from=FILE read include patterns from FILE
--files-from=FILE read list of source-file names from FILE
-0, --from0 all \*from/filter files are delimited by 0s
-s, --protect-args no space-splitting; wildcard chars only
--address=ADDRESS bind address for outgoing socket to daemon
--port=PORT specify double-colon alternate port number
--sockopts=OPTIONS specify custom TCP options
--blocking-io use blocking I/O for the remote shell
--stats give some file-transfer stats
-8, --8-bit-output leave high-bit chars unescaped in output
-h, --human-readable output numbers in a human-readable format
--progress show progress during transfer
-P same as --partial --progress
-i, --itemize-changes output a change-summary for all updates
--out-format=FORMAT output updates using the specified FORMAT
--log-file=FILE log what we're doing to the specified FILE
--log-file-format=FMT log updates using the specified FMT
--password-file=FILE read daemon-access password from FILE
--list-only list the files instead of copying them
--bwlimit=KBPS limit I/O bandwidth; KBytes per second
--write-batch=FILE write a batched update to FILE
--only-write-batch=FILE like --write-batch but w/o updating dest
--read-batch=FILE read a batched update from FILE
--protocol=NUM force an older protocol version to be used
--iconv=CONVERT_SPEC request charset conversion of filenames
--checksum-seed=NUM set block/file checksum seed (advanced)
-4, --ipv4 prefer IPv4
-6, --ipv6 prefer IPv6
--version print version number
(-h) --help show this help (see below for -h comment)
