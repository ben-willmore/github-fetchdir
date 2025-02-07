## github-fetch: Fetch a file or directory from Github by pasting its URL into the command line
  
Syntax: `github-fetch <url> [<dest_dir>]`, where `<url>` is of the form:

`https://github.com/ben-willmore/github-fetch` (whole repo, default branch)

`https://github.com/ben-willmore/github-fetch/tree/testbranch/test` (subdirectory, alternate branch)

`https://github.com/ben-willmore/github-fetch/tree/aa25db658a2013f8a0004cbdbff3ff59ce3e0aaa/test` (subdirectory, specific commit)

`https://github.com/ben-willmore/github-fetch/blob/main/README.md` (single file, main branch)

You can get the URL by navigating to the relevant file/directory\'s page on github and then copy-pasting from the URL bar.  

If `<dest_dir>` is supplied, the fetched content will be put there; otherwise it will be put in the current directory.

This should work on any unix system with basic tools installed (bash, sed, grep, ...), including jq and wget.

### Rate limit

Note that github has an API limit of about 60 requests per hour for unauthenticated users. `github-fetchdir` will use API calls to step down to the directory containing the target (`$repo/$dir/$target` = 2 calls), so you may need to be careful about this. `github-fetchdir -l` will tell you how many requests you have left and when your quota will reset.
