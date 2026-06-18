# `git` Good and Bad practices

Bad practices and mistakes to avoid.

## Force push

```sh
git push --force # Don't
git push --force-with-lease # Do
```

Don't do it only a shared branch / projects

## Commit unnecessary files

- Temporary files, Binary files, Build artifacts, ...
- Reproducible non text file:
  - Compiled object / binary files: `main.o`, `app.exe`
  - Generated docs: `main.pdf` &larr; `main.tex`, `slide.pdf` &larr; `slide.md`
  - Generated assets: `intro.gif` &larr; `intro.tape`
- Platform specific, machine specific file:
  - `/usr/lib/jvm/java-21-openjdk-amd64/lib/security/cacerts`: Don't
  - `$JAVA_HOME/lib/security/cacerts`: Do
