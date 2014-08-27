# resrc (/ˈrēˌsôrs/)

`resrc` is a tool for managing your dot files. It's still in development, so make sure you have all of your dot files
backed up before you install it.


## Usage

After installing `resrc` on a new machine (see below), you can easily set up your
user to act just like your local environment. You must have your dotfiles in a
public repo on Github called `.dotfiles` or `.files`. Then, you can add yourself
to the server with:

```bash
resrc add smurthas  # insert your github username instead of mine
```

Then you can become that user with:

```bash
resrc become smurthas  # again, your username, not mine
```

On your local machine, you probably have a working copy of your git repo. In
some circumstances it can be easier to simply link that working copy in instead
of cloning from github. That way, when you make local changes, they'll work
right away. In this case, use the `link` command:

```bash
resrc link smurthas /path/to/local/repo
```

You can easily try out a friend's environment!

```bash
resrc add kristjan
resrc become kristjan

# try out kristjan's vim settings
vim test.txt

# ...

# go back to being you
resrc become smurthas  # yet again, your username, not mine
```

### Take it with you!

You can automatically take your dot files with you when you ssh:

```bash
resrc ssh <any normal ssh args>
```

This will do some set up work first by sshing into the remote box, installing
`resrc` on that machine, and becoming you.

It's even safe to `alias ssh="resrc ssh"` as resrc will only do fancy set up
work for ssh commands of the form `ssh [user@]host [-i /path/to/key]`. If the
command is not of that form, it will just call ssh directly.

## Installation

To install, simply curl the script somewhere on your path and make it
executable:

```bash
curl https://raw.githubusercontent.com/smurthas/resrc/master/bin/resrc > /usr/local/bin/resrc
chmod +x /usr/local/bin/resrc
```
