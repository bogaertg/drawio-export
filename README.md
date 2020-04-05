# Draw.io Export

![dockerhub build](https://img.shields.io/docker/cloud/build/rlespinasse/drawio-export?style=for-the-badge)

Export Draw.io diagrams using command line / docker

## Installation

```bash
docker pull rlespinasse/drawio-export
```

## Usage

```bash
$ cd directory-with-drawio-files
$ docker run -it --privileged -v $(pwd):/data rlespinasse/drawio-export
prepare './export' folder
cleanup './export' folder content
export page 1 > ./file1.drawio -> ./export/file1-Page-1.pdf
export page 2 > ./file1.drawio -> ./export/file1-Page-2.pdf
```

You can override default configuration

* `DRAWIO_EXPORT_FILEEXT`: extention of exported files (default `pdf`)
* `DRAWIO_EXPORT_CLI_OPTIONS`: draw.io cli options to export (default `--crop`)
* `DRAWIO_EXPORT_FOLDER`: folder of exported files, with tree preservation (default `export`)

For example, export draw.io diagrams as PNG with transparent background

```bash
$ cd directory-with-drawio-files
$ docker run -it --privileged -v $(pwd):/data -e DRAWIO_EXPORT_FILEEXT=png -e DRAWIO_EXPORT_FILEEXT="-t -b 1" -e DRAWIO_EXPORT_FOLDER=images rlespinasse/drawio-export
prepare './images' folder
cleanup './images' folder content
export page 1 > ./file1.drawio -> ./export/file1-Page-1.png
export page 2 > ./file1.drawio -> ./export/file1-Page-2.png
```

You can print the available options with

```bash
docker run -it --privileged rlespinasse/drawio-export --help
```

## Contributing

Pull requests are welcome.
For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.
