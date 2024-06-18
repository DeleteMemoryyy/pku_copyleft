# PKU Copyleft

A tool for downloading theses from Peking University's copyright protection system.

Modified from the original [`PKU Copyleft`](https://github.com/mingcenwei/pku_copyleft) repository.

This software is free and belongs to the public domain. The author provides no warranties or guarantees. Users must assume all responsibilities for using this software; any consequences resulting from its use are borne by the users.

## Dependency Installation

- Required dependencies: [`fish`](https://github.com/fish-shell/fish-shell) (version >= `3.0.0`), [`curl`](https://github.com/curl/curl), [`jq`](https://github.com/stedolan/jq), [`pup`](https://github.com/ericchiang/pup), [`img2pdf`](https://github.com/josch/img2pdf).
- Optional dependencies: [`parallel`](https://www.gnu.org/software/parallel/) (to enhance download speed), [`ocrmypdf`](https://github.com/ocrmypdf/OCRmyPDF) (for OCR on downloaded PDFs; limited support for Chinese).

### Arch Linux

```shell
sudo pacman --sync --refresh --sysupgrade && sudo pacman --sync fish curl jq img2pdf parallel
```

[`pup`](https://aur.archlinux.org/packages/pup) (or [`pup-git`](https://aur.archlinux.org/packages/pup-git), [`pup-bin`](https://aur.archlinux.org/packages/pup-bin)), [`ocrmypdf`](https://aur.archlinux.org/packages/ocrmypdf) need to be installed from [AUR](https://aur.archlinux.org/).

### Ubuntu

```shell
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt update && sudo apt install fish curl jq img2pdf parallel ocrmypdf
```

[`pup`](https://github.com/ericchiang/pup) needs to be installed manually.


### Termux

```shell
apt update && apt install fish curl jq pup parallel
```

[`img2pdf`](https://github.com/josch/img2pdf) and [`ocrmypdf`](https://github.com/ocrmypdf/OCRmyPDF) needs to be installed manually.

### macOS

Install with [Homebrew](https://brew.sh/)：

```shell
brew install fish curl jq pup parallel ocrmypdf
```

[`img2pdf`](https://github.com/josch/img2pdf) needs to be installed manually.

## Usage

1. Connect to Peking University's campus network or use the [Peking University VPN](https://its.pku.edu.cn/service_1_vpn.jsp).
2. Go to the [Peking University Thesis Database](https://thesis.lib.pku.edu.cn/), and search for the thesis you want.
3. Click on the title of the thesis in the search results, go to the "View Thesis Information" page, and click "View Full Text" at the top right corner.
4. A page with a URL like "https://drm.lib.pku.edu.cn/pdfindex.jsp?fid=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" will pop up, where you can view the thesis. Note down the `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx` part after `fid=` in the URL.
5. In your browser, press `F12` (or `Ctrl` + `Shift` + `I` on Windows, `Option` + `Command` + `I` on MacOS) to open Developer Tools, select the _Storage_ tab, choose _Cookies_, and find the row with _Name_ as `JSESSIONID`. Note down the value `YYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY` in the _Value_ column.
6. Open a command line tool, navigate to the folder where `pku_copyleft.fish` is located, and run the following command to download the thesis PDF to that folder.

```shell
./pku_copyleft.fish -c 'YYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY' -f 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
```

## Free Software

This software is free and belongs to the public domain. See [`Unlicense.txt`](./Unlicense.txt) for details.