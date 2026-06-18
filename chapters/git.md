# Version control with `git`

## Prerequisite

Since `git` is such a popular if not the most well known **version control** system,
I will presumed that you know at least these `git` basic commands:

- `git init`
- `git clone`
- `git add`
- `git commit`
- `git pull`
- `git push`

This course will provide some common tasks and workflows that you might need to use in your day to day life.

## Overture

```sh
git help --all | awk '/^   [a-z0-9-]+/ {count++} END {print count}'
# 196
```

```sh
git help --all | awk '
/^Main Porcelain Commands/ {section="Porcelain"}
/^Ancillary Commands/ {section="Ancillary"}
/^   [a-z0-9-]+/ {count[section]++}
END {
  for (s in count) print s ":", count[s]
}'

# Porcelain: 45
# Ancillary: 151
```

As of today (2026-01-18),
`git` has total of $196$ subcommands ($45$ Porcelain and $151$ Ancillary)

<!-- Porcelain: main commands-->
<!-- Ancillary: supporting commands-->

- Porcelain: `init`, `add`, `commit`, `pull`, `push`, ...
- Ancillary: `config`, `reflog`, `blame`, `prune`, ...

Just the main commands alone would take me all days to teach about it.
So my best advise is, just play around with it, clone some code, commit some files, revert some changes, ...

## Resources and References

- [So You Think You Know Git - FOSDEM 2024](https://www.youtube.com/watch?v=aolI_Rz0ZqY)
- [So You Think You Know Git Part 2 - DevWorld 2024](https://www.youtube.com/watch?v=Md44rcw13k4)
- [Git Internal](https://www.youtube.com/watch?v=Ala6PHlYjmw)
- [Oh shit git](https://ohshitgit.com/)
