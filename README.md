# Project 7 - WordPress Pentesting

Time spent: **24** hours spent in total

> Objective: Find, analyze, recreate, and document **3 vulnerabilities** affecting an old version of WordPress

## Pentesting Report

### 1. CVE-2017-9061
  - [ ] Summary: XSS via Large File Upload Error
    - Vulnerability types: XSS
    - Tested in version: 4.2.0
    - Fixed in version: 4.2.15
  - [ ] GIF Walkthrough: 
    - Found in `file_size_xss folder`
  - [ ] Steps to recreate:
    - Sign in as admin
    - Go to http://wpdistillery.vm/wp-admin/media.new
    - Find a file with a size greater than 20 MB
    - Edit the filename to include a simple XSS statement (`image<img src=a onerror=alert('XSS')>.png`)
    - Upload the file
    - That's it!
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/8c7ea71edbbffca5d9766b7bea7c7f3722ffafa6)
### 2. (Required) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
### 3. (Required) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets
Enumerating Wordpress vulnerabilities: `wpscan --url http://wpdistillery.vm --random-user-agent `

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

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
