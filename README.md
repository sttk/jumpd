# [jumpd][repo-url] ![Version][ver-img] [![MIT License][mit-img]][mit-url]

Jumps to specified or previous directory.

## Install

1. Download `jumpd` file from [github.com][repo-url] and put it in your favorite directory. (ex. `~/tools`)

2. Write an alias   in `.bashrc`

    ```sh
    alias jd='. $HOME/tools/jumpd'
    ```

## Usage

1. This tool jumps specified directory and save it in `~/.jumpd` file.

   ```sh
   $ jd dest/dir
   $ pwd
   /path/to/dest/dir
   $ cat ~/.jumpd
   /path/to/dest/dir
   dir /path/to/dest/dir
   ``` 

2. This tool jumps back to the saved path when specifying no argument.

    ```sh
    $ cd another/dir
    $ jd
    $ pwd
    /path/to/dest/dir
    dir /path/to/dest/dir
    ```

3. If the specified path is not a directory but a file, this tool jumps to the parent directory.

    ```sh
    $ jd dest/dir/file.txt
    $ pwd
    /path/to/dest/dir
    ```


4. This tool supports URL path like `file:///path/to/dest/dir/page.html`.

    ```sh
    $ jd file:///path/to/dest/dir/page.html
    $ pwd
    /path/to/dest/dir
    ```

5. This tool jumps to the real path even if the specified path is a symbolic link.

    ```
    $ ln -s /path/to/dest/dir symdir
    $ jd symdir
    $ pwd
    /path/to/dest/dir
    ```

6. This tool makes the specified directory if it does not exist.

    ```
    $ jd not/exist/dir
    'not/exist/dir' does not exist. Do you make this directory? (Y/n) y
    $ pwd
    /path/to/not/exist/dir
    ```

7. This tool is able to move directory path with basename if saved.

    ```
    $cat ~/.jumpd
    /path/to/dest/dir
    dir /path/to/dest/dir
    $ jd -to dir
    $ pwd
    /path/to/dest/dir
    ```

8. This tool is able to save and move directory path with key.

    ```
    $ jd dir/with/key mykey
    $ pwd
    /path/to/dir/with/key
    $ cat ~/.jumpd
    /path/to/dir/with/key
    dir /path/to/dest/dir
    mykey /path/to/dir/with/key
    $
    $ cd ../..
    $ pwd
    /path/to/dir
    $
    $ jd -to mykey
    $ pwd
    /path/to/dir/with/key
    $ cat ~/.jumpd
    /path/to/dir/with/key
    mykey /path/to/dir/with/key
    dir /path/to/dest/dir
    ```


## License

Copyright (C) 2017-2019 Takayuki Sato

This program is free software under [MIT][mit-url] License.
See the file LICENSE in this distribution for more details.

[repo-url]: https://github.com/sttk/jumpd/
[ver-img]: https://img.shields.io/badge/version-0.2.0-blue.svg
[mit-img]: https://img.shields.io/badge/license-MIT-green.svg
[mit-url]: https://opensource.org/licenses/MIT
