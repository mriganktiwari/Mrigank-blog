---
title: "Terminal commands"
layout: post
toc: false
categories: [linux, terminal]
---

# ```find```
---
### Search by Type (file or dir)

|Command|Description|
|----   |----       |
| `find .` | Find all the files & directories under current directory |
| `find <dir>` | Find all the files & directories under <dir> |
| `find <dir> -type d` | Find only directories under specific directory |
| `find . -type d` | Find only directories under current directory |
| `find <dir> -type f` | Find only files under specific directory |
| `find . -type f` | Find only files under current directory |

### Search by file name

|Command|Description|
|----   |----       |
| `find <dir> -type f -name "<test1.txt>"` | Find a file with a specific name |
| `find <dir> -type f -name "<test*>"` | Find a file starting with the name 'test' |
| `find <dir> -type f -iname "<test*>"` | Find a file starting with the name 'test' or 'Test' & Case Insensitive |
| `find <dir> -type f -iname "<*.py>"` | Find a file ending with the name '.py' & Case Insensitive |

### Search by time or day

|Command|Description|
|----   |----       |
| `find <dir> -type f -mmin -10` | All the files modified in last 10 mins |
| `find <dir> -type f -mmin +10` | All the files modified in more than last 10 mins ago |
| `find <dir> -type f -mmin +1 -mmin -5` | More than 1 min ago and less than 5 mins ago |
| `find <dir> -type f -mtime -20` | Files modified less than 20 days ago |

### Search by file size

|Command|Description|
|----   |----       |
| `find <dir> -size +5M` | Find all the files over 5 MB under directory |
| `ls -lah <dir>` | List all files and dirs with size in MB |
| `find <dir> -empty` | Find all empty files in directory |

### Search based on permissions

|Command|Description|
|----   |----       |
| `find <dir> -perm 777` | xyv |

### Change user & group for every file & dir under "dir"
|Command|Description|
|----   |----       |
| `-exec` | Executes the following command on the results from preceding command |
| `{}` | Placeholder for just the filenamees that would be be used in case of chown command |
| `+` or `\;` | Either can be used to end the command |
| `find <dir> -exec chown [user]:[group] {} +` | xyz |

### Lets try setting permissions of all directories to 775 and all files to 664
|Command|Description|
|----   |----       |
| `find <dir> -type d -exec chmod 775 {} +` | xyz |
| `find <dir> -type f -exec chmod 664 {} +` | xyz |


### Search and perform actions
|Command|Description|
|----   |----       |
| `find <dir> -type f -name "*.jpg"` | Search all image files ending in .jpg in dir and subsequent directories |
| `find <dir> -type f -name "*.jpg" -maxdepth 1` | Search all image files ending in .jpg only and only in dir |
| `find <dir> -type f -name "*.jpg" -exec rm {} +` | Deletes all the files returned from the command precesing `-exec` |
| `find <dir> -type f -name "*.jpg" -maxdepth 1 -exec rm {} +` | Deletes all the files returned from the command precesing `-exec` |

# _grep (Global Regular Expression Print)
---
- `grep` is case sensitive

### Finding is a given text is present in some file

|Command|Description|
|----   |----       |
| `grep "text_to_find" <file_name>` | Searching for some text in a normal file |
| `grep -w "text_to_find" <file_name>` | Return results from `file_name` only when whole words match `text_to_find` |
| `grep -wi "text_to_find" <file_name>` | Returns results with both lower case and upper case with `text_to_find` |

### Returns results with line number

|Command|Description|
|----   |----       |
| `grep -win "text_to_find" <file_name>` | Returns results with line numbers in `file_name` |
| `grep -win "text_to_find" ./*` | Returns results with line numbers in all files in current directory + Will throw error for any subdirectory that might be present. |
| `grep -win "text_to_find" ./*.txt` | Doesn't try to search in any subdirectory. |
| `grep -winr "text_to_find" .` | To search every file and through every subdirectory, a recursive search, might get lot of results. |

### Getting some additional context of where this match is found, see a certain number of lines before and after a match

|Command|Description|
|----   |----       |
| `grep -win -B 4 "text_to_find" <file_name>` | 4 lines Before all of our match |
| `grep -win -A 4 "text_to_find" <file_name>` | 4 lines After all of our match |
| `grep -win -C 2 "text_to_find" <file_name>` | 2 lines Before and After all of our match |

### If you're only interested in file_names with the matches, NOT in the matches themselves

|Command|Description|
|----   |----       |
| `grep -wirl "text_to_find" .` | Recursive result of all files with the match |
| `grep -wirc "text_to_find" .` | Recursive result of all files with the match + Number of matches in each file |

### Pipe the output of other commands in to **grep** to search for something

|Command|Description|
|----   |----       |
| `history | grep "git commit"` |
| `history | grep "git commit" | grep "dotfile"` |

### ```grep``` uses Posix regular expressions by default

|Command|Description|
|----   |----       |
| `grep "...-...-...." <filename>` | xyz |
| `grep "\d{3}-\d{3}-\d{4}" <filename>` | This wouldn't work, because this is pro compatible regular expressions which grep doesn't use. |
| `grep -P "\d{3}-\d{3}-\d{4}" <filename>` | This would allow it to work on Linux, NOT on Mac |
| `grep -wirlP "\d{3}-\d{3}-\d{4}" <filename>` | Return recursive list of list with matching phone numbers |
| `grep -V` | xyz |
| `brew install grep --with-default-names` | xyz |
| `--with-default-names` | It will install it as grep, else as ggrep (allowing us to use both BSD and GNU grep) |
