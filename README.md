# Galaxy 2.0 Library Exporter

A tool to export your local GOG Galaxy 2.0 Library into a single `.xlsx` file.

## Why?

A friend of mine and I have an agreement that we choose each others game to play through next.
So each of us composed a single `.xlsx` file with our entire gaming library so it would be easier for us to decide upon the others fate.
But keeping this file up2date is tedious. That is why I created this little thingamajig.

## What?

It is just a little python script (or compiled executable) that extracts your owned games from the local GOG Galaxy 2.0 database and composes a single `.xlsx` file out of it.
The games are sorted into sheets which represent the corresponding platform.

## How?

Either clone the repo, create the virtual environment and run the `main.py` script:
```sh
git clone https://github.com/Rall3n/galaxy-library-exporter

pipenv install

pipenv run python main.py "path/to/galaxy-2.0.db"
```
or download the executable from the latest release and run this one:
```sh
galaxy-library-exporter.exe "path/to/galaxy-2.0.db"
```

> Executable has only been tested with Windows devices.

### Options (because there have to be some)

Currently the script only generates a single `.xlsx` file. The default columns are the title of the games, and a little achievement statistic (`achieved / total`). The title column will be filterable. The `generic` platform will be ignored.

#### Output

The `--output` (`-o`) argument changes the name of the to be created file. Default is `galaxy-library`.

> This argument does not require a file extension.

```sh
# Will create a `my-library.xlsx` file
galaxy-library-exporter.exe "path/to/galaxy-2.0.db" --output 'my-library'
```

#### Tags

With the `--tags` (`-t`) argument you can either include all your currently applied tags on the games, or a selection of tags. The column will be filterable.

```sh
galaxy-library-exporter.exe "path/to/galaxy-2.0.db" --tags

# or 

galaxy-library-exporter.exe "path/to/galaxy-2.0.db" --tags "Played" "Unplayed"
```

#### Platforms

By default, all platforms will be included in the file except for the `generic` platform. If you want to only export specific platforms, you can do that with the `--platforms` (`-p`) option. The values have to be the platform IDs from the [official platform list](https://github.com/gogcom/galaxy-integrations-python-api/blob/master/PLATFORM_IDs.md).

> The `generic` platform will be completely ignored.

```sh
galaxy-library-exporter.exe "path/to/galaxy-2.0.db" --platforms "steam" "uplay"
```
