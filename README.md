# rpcfetch resources

> This is the resources repository for [rpcfetch](https://github.com/rpcfetch/rpcfetch)

Collection of operating systems, Linux distros, window managers and other applications with their icons.

## Usage

This use this in your own projects, you'll need to get the [resources.json](./resources.json) file.

To download the latest release programmatically, use the GitHub releases API: `https://api.github.com/repos/rpcfetch/resources/releases/latest` (docs: https://docs.github.com/en/rest/releases/releases#get-the-latest-release)

### resources.json structure

The JSON file consists of:
1. The current version ([semver](https://semver.org/))
2. Categories:
   - app
   - os
   - wm

Each category is a list of resource items.

## Resource item definition

| Field name | Type    | Default value | Description                                |
| ---------- | ------- | ------------- | ------------------------------------------ |
| `pattern`  | string  | *(required)*  | Pattern to match                           |
| `regex`    | boolean | false         | Treat pattern as a Perl 5 compatible regex |
| `icase`    | boolean | false         | Ignore case (does not require regex)       |
| `image`    | string  | *(required)*  | Image URL                                  |

## Discord limitations

- supports image URLs with a maximum size of 128 bytes
- supported image formats: PNG, JPEG, WEBP, GIF (this is the only animated format client-side)
- images other than 1:1 aspect ratios are stretched on desktop
- images are fully rounded
- images should have enough contrast (or a background color) to stand out against the dark theme background: `#111214` and the light theme background: `#ffffff`

### Examples of valid resource items

Name must match `dwm`:
```json
{
  "pattern": "dwm",
  "image": "https://raw.githubusercontent.com/rpcfetch/resources/main/assets/wm/dwm.png"
}
```

Name must match `firefox` but the case can be ignored:
```json
{
  "pattern": "firefox",
  "icase": true,
  "image": "https://raw.githubusercontent.com/rpcfetch/resources/main/assets/app/firefox.png"
}
```

Name must match the regex `^Arch( Linux)?$`:
```json
{
  "pattern": "^Arch( Linux)?$",
  "regex": true,
  "image": "https://raw.githubusercontent.com/rpcfetch/resources/main/assets/os/archlinux.png"
}
```

## Repository structure

In the [assets](./assets/) folder there are folders of applications, operating systems (and Linux distros), window managers: `assets/app`, `assets/os`, `assets/wm`

An example of Firefox would look like this: `assets/app/firefox.png`

## Legal

> **Disclaimer:** The icons and images contained in this repository may be subject to copyright protection, and I want to clarify that I do not claim any ownership rights to them.

Contact the public email of this GitHub organization to request the removal of images.

## Contributing

Feel free to submit pull requests with your desired additions or changes to help this project support the applications you use.

Please refrain from using "sketchy" websites as image URLs and upload them directly to the repo! Please upload your images to the [appropriate folders](#repository-structure).
```diff
- https://cdn0.iconfinder.com/data/icons/flat-round-system/512/archlinux-512.png
+ https://raw.githubusercontent.com/rpcfetch/resources/main/assets/app/firefox.png
```
