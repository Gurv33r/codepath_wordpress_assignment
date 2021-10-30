# Project 7 - WordPress Pentesting

Time spent: **24** hours spent in total

> Objective: Find, analyze, recreate, and document **3 vulnerabilities** affecting an old version of WordPress

## Pentesting Report

### 1. CVE-2017-9061
  - [ ] Summary: XSS via Large File Upload Error
    - Vulnerability types: XSS Injection
    - Tested in version: 4.2.0
    - Fixed in version: 4.2.15
  - [ ] GIF Walkthrough: 
    - Found in `file_size_xss folder`
  - [ ] Steps to recreate:
    - Sign in as admin
    - Go to http://wpdistillery.vm/wp-admin/media.new.php
    - Find a file with a size greater than 20 MB
    - Edit the filename to include a simple XSS statement (`image<img src=a onerror=alert('XSS')>.png`)
    - Upload the file
    - That's it!
  - [ ] Affected source code:
    - [Patch to Source Code](https://github.com/WordPress/WordPress/commit/8c7ea71edbbffca5d9766b7bea7c7f3722ffafa6)
### 2. CVE-2017-14719
  - [ ] Summary: Path Traversal in Unzipping in the Customizer
    - Vulnerability types: Path Traversal
    - Tested in version: 4.2.0
    - Fixed in version: 4.2.16
  - [ ] GIF Walkthrough: Found in `path_unzip` folder
  - [ ] Steps to recreate:
    - Download the `zip_poc.zip`file below or in the `path_unzip folder`
    - Go to http://wpdistillery.vm/wp-admin/plugin-install.php?tab=upload
    - Upload the zip file
    - Check your /tmp folder for additional files that shouldn't be there.  
  - [ ] Affected source code:
    - [Patch to Source Code](https://core.trac.wordpress.org/changeset/41457)
### 3. CVE-2019-9787
  - [ ] Summary: XSS via Post Comments
    - Vulnerability types: XSS Injection
    - Tested in version: 4.2.0
    - Fixed in version: 4.2.23
  - [ ] GIF Walkthrough: found in `comment_xss`folder
  - [ ] Steps to recreate: 
    - Create a post
      - Wordpress 4.2's security against XSS injection in the comments of a Post is to just display it inside a p-tag. 
      - This is bad, because once you figure it out (which required just a few clicks), it's really easy to bypass the mechanism:
        - Start your XSS by closing the p-tag with `</p>`
        - Enter the XSS as a script tag, for example: `<script>alert('XSS')</script>`
        - Finish it off with `<p>` since there is closing p-tag waiting for you on the backend, and doing so will create another blank but valid p-tag
    - All in all, comment `</p><script>alert('XSS')</script><p>`
    - Post the comment
    - That's it!
  - [ ] Affected source code:
    - [Patch to Source Code](https://github.com/WordPress/WordPress/commit/0292de60ec78c5a44956765189403654fe4d080b)

## Assets
- Enumerating Wordpress vulnerabilities: `wpscan --url http://wpdistillery.vm --random-user-agent` 
- Zip file used to for path traversal vulnerability = [zip_poc.zip](http://github.com/Gurv33r/codepath_wordpress_assignment/path_unzip/zip_poc.zip)
## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Vagrant and Wordpress installation was a mess. I cannot access http://wpdistillery.vm/ from my host OS but my guest Kali can. I ran Wordpress on a VirtualBox instance and Kali off of VMWare.

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
