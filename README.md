# mailfilter

This is a simple [maildrop](https://www.courier-mta.org/maildrop/) script which
sorts incoming mails according to their recipients (*To*, *CC* and *BCC*).

## Usage:
Store the script and filtering lists in a directory
(mine is `$/HOME/.mailfilter`) and update
```
MAILFILTERDIR="the path to this directory"
MAILDIR="the path of your mail directory"
SUBDIR1="$MAILDIR/.your-first-mail-subdirectory"
SUBDIR2="$MAILDIR/.your-second-mail-subdirectory"
... further subdirectories ...
```

If a mail subdirectory does not exist yet, it is created by the line
`test -d "$SUBDIR1/" || maildirmake "$SUBDIR1/"`.
Attention: normally your mail client does not subscribe to new mail folders
automatically.

For each mail subdirectory there is a pattern list in `/lists` defining the
rules for sorting mails into. Make sure that every pattern starts with `\s`
since the recipients stored in `ADDRLIST` are separated by a space.

Finally update the domains you want to take account of in the
*# Fetch all relevant recipients* part.

Mails not matching any of the filters are sorted to the `Catchall` mail
subdirectory.

**Attention: change the access permission of all involved files to**
`chmod 600 file`, **otherwise maildrop will terminate immediately.**


## Further reading
* The documentation of the [maildrop filtering language](https://www.courier-mta.org/maildrop/maildropfilter.html).
* The documentation of the [Perl Compatible Regular Expressions](https://www.pcre.org/).
