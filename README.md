# lua-module-path
Lua 5.1 tested Path module provides just string path manipulations.

### path()
return new path object with current path directory (debug.getinfo), also you can set path manually through first string argument of module call (like regular constructor call)

### path("this/is/my/path")
Creates path object with defined string literals. if path ends with delimeter slash, it means path is folder (catalogue) path.
If it is ends with non slash character, it means path is file path.
## forexample
### print(path("this/is/my/path"):isfile()) - true
### print(path("this/is/my/path"):isfolder()) - false

You can make sum with two path. It works like an OOP sum works. It will return new Path object with string concat, that makes one check before sum action. You can't sum file path with another path, because file path means completed path.

### path("path/to/file.lua") + path("another/path/segment/") will accept an error.
#### But
### path("path/to/file") + path("another/path/segment/")
#### Will return
### path("path/to/file/another/path/segment/")

You can sum with file path, but you need to cut last segment by calling :up(i) operation.
### path("path/to/file.lua"):up() + path("another/path/segment/") will return path("path/to/another/path/segment/")
Because :up() just removes last path segment and it will allow to make sum action.

