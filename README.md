# windows_disk_facts

#### Table of Contents

1. [Description](#description)
1. [Usage](#usage)

## Description

This module adds  the following facts on Windows:

### `$::disks`

The output of the Powershell `Get-Disk` command, but in a more Puppet-friendly format

### `$::drives`

The output of the Powershell `Get-PSDrive -PSProvider 'FileSystem'` command, but in a more Puppet-friendly format + additional drive type information ('fixed' = local hard drive, 'removable' = removable devices like floppy and usb, 'cd-rom' = optical drives)

### `$::partitions`

The output of the Powershell `Get-Partition` command, but in a more Puppet-friendly format

## Usage

```puppet
# Loop over all of the partitions and find the one that is mounted to C:\
$::partitions.each |$partition| {
  if $partition['drive_letter'] == 'C' {
    # Do something here
  }
}

# Get the free size of C:\
notice($::drives['C']['free_bytes'])
```

## Contributors

  - [nicolasvan](https:///github.com/nicolasvan)
  - [natemccurdy](https:///github.com/natemccurdy)
  - [covidium](https:///github.com/covidium)
