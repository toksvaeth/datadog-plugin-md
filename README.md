This is a plugin for [Datadog](http://docs.datadoghq.com/guides/agent_checks/)
that checks the status of Linux software RAID Multiple Device
[md](http://linux.die.net/man/4/md)(4) arrays and returns a variety of gauges.

The information is inelegantly parsed from `/proc/mdstat` and sent to datadog
as various gauges.

## Gauges

 * `md_device.disk.total` The total number of disks that are supposed to be
   active in the array.
 * `md_device_disk.active` The total number of disks that are active in the
   array.  i.e. non-failed and non-spare.  Disks that are considered recovering
   will be included in this count.
 * `md_device.disk.spare` The total number of spare disks in the array.
 * `md_device.disk.failed` The total number of failed disks in the array.
 * `md_device.disk.up` The total number of fully functioning disks in the
   array.  i.e. non-failed, non-spare and non-recovering.
 * `md_device.recovery.complete` The percentage of recovery completed.  Will
   return 100% for arrays that are not in recovery status.
 * `md_device.recovery.speed_bytes` The speed of recovery.  Will return 0 for
   arrays that are not in recovery status.
