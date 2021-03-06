# vmbackup

Backup scripts for virtual machines run by libvirt, using the "live disk backup with active blockcommit" method:

http://wiki.libvirt.org/page/Live-disk-backup-with-active-blockcommit

The backup script assumes a machine named *vm* is stored in a file named *vm.qcow2*. This is hardcoded but could be modified as the backup method itself doesn't rely on the VM being stored as a *qcow2* file.

The backup script also assumes that the guest agent is installed in all VM. This is hardcoded but could be modified.

## Dependencies

  - libvirt, virsh,... for VM management
  - cfget for config file parsing

## Installation

    cp vmbackup vmbackuprotate /usr/local/sbin/
    cp etc/vmbackup.conf /etc/
    cp etc/cron.daily/vmbackup /etc/cron.daily/

## Usage

#### vmbackup

vmbackup can be used to backup a single VM.

      Usage : vmbackup <vm dirpath> <vm name> <backup filepath>
          vm dirpath:      path to directory where VM file is stored
          vm name:         name of VM to backup
          backup filepath: path of backup file to create
          Note: VM file is assumed to be dirpath/name.qcow2

#### vmbackuprotate

vmbackuprotate backs up several VM and rotates backups.

       Usage : vmbackuprotate <config file path>
           config file path: path to configuration file'

Its parameters are passed in vmbackup.conf, which should be self-explanatory.

## Documentation

For more information, see [this thread](https://www.redhat.com/archives/libvirt-users/2015-September/msg00037.html) from the libvirt users mailing list.

And of course, the [libvirt wiki](http://wiki.libvirt.org/).
