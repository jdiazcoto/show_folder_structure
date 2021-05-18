# show_folder_structure
In linux or mac os

QUESTION:
1. 162

Is there any linux command that I can call from a Bash script that will print the directory structure in the form of a tree, e.g.,

folder1
   a.txt
   b.txt
folder2
   folder3


ANSWER:
Is this what you're looking for tree? It should be in most distributions (maybe as an optional install).

~> tree -d /proc/self/
/proc/self/
|-- attr
|-- cwd -> /proc
|-- fd
|   `-- 3 -> /proc/15589/fd
|-- fdinfo
|-- net
|   |-- dev_snmp6
|   |-- netfilter
|   |-- rpc
|   |   |-- auth.rpcsec.context
|   |   |-- auth.rpcsec.init
|   |   |-- auth.unix.gid
|   |   |-- auth.unix.ip
|   |   |-- nfs4.idtoname
|   |   |-- nfs4.nametoid
|   |   |-- nfsd.export
|   |   `-- nfsd.fh
|   `-- stat
|-- root -> /
`-- task
    `-- 15589
        |-- attr
        |-- cwd -> /proc
        |-- fd
        | `-- 3 -> /proc/15589/task/15589/fd
        |-- fdinfo
        `-- root -> /
        
        
ANOTHER ANSWER:
ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'

ANOTHER ANSWER:
This command works to display both folders and files.

find . | sed -e "s/[^-][^\/]*\// |/g" -e "s/|\([^ ]\)/|-\1/"

Example output:

.
 |-trace.pcap
 |-parent
 | |-chdir1
 | | |-file1.txt
 | |-chdir2
 | | |-file2.txt
 | | |-file3.sh
 |-tmp
 | |-json-c-0.11-4.el7_0.x86_64.rpm
