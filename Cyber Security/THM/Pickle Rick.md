
## Reading files without cat

```sh
while read line; do echo $line; done < $file
```

```sh
grep . $file
```

```sh
grep -R .
```

search for anything