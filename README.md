VMF Tools
=============

Programmatically modify VMF files.

# Rules

Currently the following is implemented:

- [**Christmas lights**](docs/christmas_lights.md) - add lights to ropes in your map

# Usage

The tool can be ran in two ways: as part of the map compilation, or manually.

## As part of compilation

This is the most user friendly way once you've set it up, as it works more or less transparently.

1. Download [vmf-tools.exe](bin/vmf-tools.exe)
2. Go to your Hammer compilation settings (<kbd>F9</kbd>) and enable advanced mode if not already set.
3. For each mode you want to compile in, do the following:
    1. &#8203;<details><summary>[Optional] Copy the configuration configuration</summary>![](docs/imgs/setup_comp1.png)</details>
    2. &#8203;<details><summary>Add a new command, pick the <code>vmf-tools.exe</code> as executable</summary>![](docs/imgs/setup_comp2.png)</details>
    2. &#8203;<details><summary>Enter `$path\$file.$ext $path\$file-processed.$ext` as parameters</summary>![](docs/imgs/setup_comp3.png)</details>
    3. &#8203;<details><summary>Make sure the new command is the top-most command and is enabled</summary>![](docs/imgs/setup_comp4.png)</details>
    4. &#8203;<details><summary>In all other commands, replace <code>$path\\$file</code> with <code>$path\\$file-processed</code></summary>![](docs/imgs/setup_comp5.png)</details>

Done. Whenever you compile the map it will now automatically be processed.

## Manually

Run the tool manually, specifying the VMF as the first argument and the output as the second argument (`vmf-tools.exe path\to\map.vmf path\to\processed.vmf`).

# Configuration

The configuration usually happens through Hammer by using custom keyvalues. The specifics of how this works can be found on each rule's README.

For more advanced configuration a configuration file is needed. This is simple a `.js` file that contains `module.exports = { rules: { /* config goes here */ } }`, with the configuration as specified in each rule's README.

If you want to use a configuration file you must tell the tool about it. This is done by going to `Map > Map properties...` in Hammer and adding a keyvalue of `vmft_config` with the value being the path to the config file. You may also give the path to the file as the third argument if you run the tool manually.

If the configuration file is specified as a map property *and* as the third argument when running the tool, then the one specified as a map property will be used.
