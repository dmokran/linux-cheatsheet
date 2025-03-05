CGroups v2 only
--- how to tell cgroups version ---
grep cgroup /proc/mounts -> if there's more than one cgroup mount, it's v1, but both versions can be enabled at the same time

pseudo-filesystem (fs type = cgroup2) used by cgroup_v2 is mounted either at:
/sys/fs/cgroup
/sys/fs/cgroup/unified

/sys/fs/cgroup/cgroup.controllers -> enabled controllers on top level
/sys/fs/cgroup/cgroup.cgroup.subtree_control -> allowed controllers for the next level down
/sys/fs/cgroup/<PID>/cgroup.procs -> PIDs that are part of the cgroup

mkdir /sys/fs/cgroup/<xyz> -> create new cgroup with name "xyz"
rmdir /sys/fs/cgroup/<xyz> -> delete cgroup with name "xyz" - may not work if there are processes in it

systemd-cgls -> list current cgroups
