envsubst is a command-line utility in Linux that substitutes the values of environment variables in a given shell format string. It searches for patterns of the form `$VARIABLE` or `${VARIABLE}` in the input string and replaces them with the corresponding values of the environment variables.

To substitute environment variables in a file named confidential.txt:

```
// confidential.txt
${USERNAME}
${PASSWORD}

```

```
$ export USERNAME=auguto
$ export PASSWORD=secretpassword
$ envsubst < confidential.txt > confidential_new.txt
```


```
// confidential_new.txt
auguto
secretpassword
```
