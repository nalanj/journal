# Installing Node (on Linux)

Here's how I install [Node](https://nodejs.org). It's not the only way to do 
so, but it's how I do it.

I'm using version 13.8.0 here, but replace that with whatever version you need
to install.

```bash
# Download the latest package
curl -O https://nodejs.org/dist/v13.8.0/node-v13.8.0-linux-x64.tar.xz

# Make sure the target directory is set up
mkdir -p ~/.local/lib/nodejs

# Unpack it
tar xvf node-v13.8.0-linux-x64.tar.xz -C ~/.local/lib/nodejs/
```

Once that's done, add the new directory to `~/.profile`:

```bash
# set PATH so it includes the node install if it exists
if [ -d "$HOME/.local/lib/nodejs/node-v13.8.0-linux-x64/bin" ] ; then
    PATH="$HOME/.local/lib/nodejs/node-v13.8.0-linux-x64/bin:$PATH"
fi
```

Then reload your profile and make sure the `node` command is available:

```bash
source ~/.profile
which node
```

If everything is right, you should see the path to the new node command, under
`~/.local/lib`.
