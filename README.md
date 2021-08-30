# msg2eml

## Convert Outlook .msg files to Microsoft .eml format

Apple Mail can't open `.msg` files.
This program converts it to `.eml` format which can be opened by Apple Mail.

### Installation

Run `bundle install` to install the `ruby-msg` gem.

### Usage

```
./msg2eml FILE
```

Or call `mapitool` directly.

```
mapitool -si FILE > FILE.eml
```

See `mapitool` help for additional options

```
$ mapitool -h
Usage: mapitool [options] [files]

    -o, --output-dir DIR             Put all output files in DIR
    -i, --[no-]individual            Do not combine converted files
    -s, --stdout                     Write all data to stdout
    -f, --filter-path PATH           Only process pst items in PATH
        --enable-pst                 Turn on experimental PST support

    -v, --[no-]verbose               Run verbosely
    -h, --help                       Show this message
```

### Implementation

Bundle install `ruby-msg` gem. The original [aquasink](https://github.com/aquasync/ruby-msg) gem produces the following error.

```
bundler: failed to load command: mapitool (/Users/kjw/.rvm/gems/ruby-2.7.0/bin/mapitool)
Encoding::CompatibilityError: incompatible character encodings: UTF-8 and ASCII-8BIT
```

 We use the fork by `denodster` which [fixes this error](https://github.com/aquasync/ruby-msg/pull/16).