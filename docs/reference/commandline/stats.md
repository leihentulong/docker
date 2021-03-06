<!--[metadata]>
+++
title = "stats"
description = "The stats command description and usage"
keywords = ["container, resource, statistics"]
[menu.main]
parent = "smn_cli"
+++
<![end-metadata]-->

# stats

```markdown
Usage:  docker stats [OPTIONS] [CONTAINER...]

Display a live stream of container(s) resource usage statistics

Options:
  -a, --all         Show all containers (default shows just running)
      --help        Print usage
      --no-stream   Disable streaming stats and only pull the first result
```

The `docker stats` command returns a live data stream for running containers. To limit data to one or more specific containers, specify a list of container names or ids separated by a space. You can specify a stopped container but stopped containers do not return any data.

If you want more detailed information about a container's resource usage, use the `/containers/(id)/stats` API endpoint. 

## Examples

Running `docker stats` on all running containers against a Linux daemon.

    $ docker stats
    CONTAINER           CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O
    1285939c1fd3        0.07%               796 KiB / 64 MiB        1.21%               788 B / 648 B       3.568 MB / 512 KB
    9c76f7834ae2        0.07%               2.746 MiB / 64 MiB      4.29%               1.266 KB / 648 B    12.4 MB / 0 B
    d1ea048f04e4        0.03%               4.583 MiB / 64 MiB      6.30%               2.854 KB / 648 B    27.7 MB / 0 B

Running `docker stats` on multiple containers by name and id against a Linux daemon.

    $ docker stats fervent_panini 5acfcb1b4fd1
    CONTAINER           CPU %               MEM USAGE/LIMIT     MEM %               NET I/O
    5acfcb1b4fd1        0.00%               115.2 MiB/1.045 GiB   11.03%              1.422 kB/648 B
    fervent_panini      0.02%               11.08 MiB/1.045 GiB   1.06%               648 B/648 B

Running `docker stats` on all running containers against a Windows daemon.

    PS E:\> docker stats
    CONTAINER           CPU %               PRIV WORKING SET    NET I/O             BLOCK I/O
    09d3bb5b1604        6.61%               38.21 MiB           17.1 kB / 7.73 kB   10.7 MB / 3.57 MB
    9db7aa4d986d        9.19%               38.26 MiB           15.2 kB / 7.65 kB   10.6 MB / 3.3 MB
    3f214c61ad1d        0.00%               28.64 MiB           64 kB / 6.84 kB     4.42 MB / 6.93 MB

Running `docker stats` on multiple containers by name and id against a Windows daemon.

    PS E:\> docker ps -a
    CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
    3f214c61ad1d        nanoserver          "cmd"               2 minutes ago       Up 2 minutes                            big_minsky
    9db7aa4d986d        windowsservercore   "cmd"               2 minutes ago       Up 2 minutes                            mad_wilson
    09d3bb5b1604        windowsservercore   "cmd"               2 minutes ago       Up 2 minutes                            affectionate_easley
   
    PS E:\> docker stats 3f214c61ad1d mad_wilson
    CONTAINER           CPU %               PRIV WORKING SET    NET I/O             BLOCK I/O
    3f214c61ad1d        0.00%               46.25 MiB           76.3 kB / 7.92 kB   10.3 MB / 14.7 MB
    mad_wilson          9.59%               40.09 MiB           27.6 kB / 8.81 kB   17 MB / 20.1 MB	