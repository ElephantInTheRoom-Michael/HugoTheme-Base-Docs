---
date: '2026-01-19T00:45:30-08:00'
draft: true

weight: 1

title: 'Getting Started'
---

# Create a New Theme

Start by creating a new Hugo project for the theme. Do not follow any of the Hugo documentation to add the theme using
submodules or adding it `hugo.yaml`. Instead, it will be added as a Go module.

Follow the [Hugo docs](https://gohugo.io/hugo-modules/use-modules/) to initialize the new Hugo theme project as a new Go 
module.

## Add the Base Theme

Add the base theme to the project configuration in `hugo.yaml`:

```yaml
module:
  imports:
  - path: github.com/ElephantInTheRoom-Michael/HugoTheme-Base
```

Run `hugo mod get -u` to create the `go.mod` and `go.sum` files. These files should be committed to the Git repository.

You can run `hugo mod graph` to verify the module dependency has been added properly.

# Concurrent Development of Base and Theme

If you need to make changes to the base theme and would like to see them reflected in the theme without needing to push
to Git first, it is possible to use a module workspace. 

Clone the base theme repository under the same parent directory as the theme project.

Create a `hugo.work` file in the root of the theme project with the following contents (replacing `<version>` with 
the version of Go you are currently using):

```go
go <version>

use .
use ../HugoTheme-Base
```

This also works while you are developing a site using your new theme. In the root of that project add the following 
`hugo.work` file:

```go
go <version>

use .
use ../<your-theme>
use ../HugoTheme-Base
```

Running `hugo server` will not reflect your local changes, it will still use the version of the base theme committed
to Git. To see your local changes, run hugo command prefixed with `HUGO_MODULE_WORKSPACE=hugo.work`. For example:

```shell
HUGO_MODULE_WORKSPACE=hugo.work hugo server -D
```
