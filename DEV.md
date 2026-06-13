# Dev notes

```bash
git clone https://github.com/canh25xp/Linux101.git
cd Linux101
```

## Convert slide

```bash
cd linux101
npm install # Run once
npx marp slide.md
xdg-open slide.html
```

## Watch and Preview

```bash
npx marp slide.md --preview --watch
```

## Server mode

```bash
npx marp --server .
xdg-open http://localhost:8080/slide.md
```
