
```
$ mkdir nuwa && cd nuwa
$ west init -m git@github.com:Ameba-AIoT/nuwa.git
$ west update
$ ln -sf tools/meta_tools/nuwa.py nuwa.py
$ ./nuwa.py setup -g
$ ./nuwa.py build -a <application> -d <device>
```
e.g.:
`$ ./nuwa.py build -a zephyr/samples/hello_world -d rtl872xd_evb`

