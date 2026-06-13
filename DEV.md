# Dev notes

```bash
git clone https://github.com/canh25xp/Linux101.git
cd Linux101
```

## Convert slide

```bash
npm install # Run once
npx marp linux101/main.md
xdg-open linux101/main.html
```

## Watch and Preview

```bash
npx marp linux101/main.md --preview --watch
```

## Server mode

```bash
npx marp --server linux101
xdg-open http://localhost:8080/main.md
```
