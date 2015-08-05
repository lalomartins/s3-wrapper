# s3-wrapper
Simple command line wrapper for http://s3tools.org/s3cmd

Simplifies deploying files to an s3 bucket. Supports keeping your local version in version control (e.g. git), by ignoring all dotfiles in the project root.

## Usage

Create a .s3.cson file in the project root. For now the only supported property is `bucket`, which should be your bucket name (just the name, no `s3://`). This will be used both for determining the remote bucket, and to find the project root (so you can invoke the script from a subfolder).

To set up s3 access credentials, run `s3cmd --configure` first.

There's a decent `--help` facility should you need a reminder.

To use it, call `s3 push` to send files, or `s3 pull` to get them. Both use `s3cmd sync`, so they should be clever about it (although sync remote to local sometimes still gets too much stuff, at least for me).

For either command, you can specify some paths, and sync just those.

**WARNING:** the paths feature isn't fully done yet; for now, only use that from the project root.

You can also use `-n` or `--dry-run` to see what would be done; those are passed to `s3cmd` directly.

## Dependencies

- Python3
- python-cson installed for python3
- easydict installed for python3
