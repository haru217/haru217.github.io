# ShortFlow Blog (Hugo + GitHub Pages)

## 1) Prereqs
- Create a GitHub repo named: `<USERNAME>.github.io`
- In the repo settings:
  - Pages → Source: **GitHub Actions**

## 2) Update baseURL
Edit `hugo.yaml`:
- `baseURL: "https://<GITHUB_USERNAME>.github.io/"`

## 3) Push
```bash
git add -A
git commit -m "init ShortFlow blog"
git branch -M main
git remote add origin https://github.com/<USERNAME>/<USERNAME>.github.io.git
git push -u origin main
```

The workflow `.github/workflows/hugo.yml` will build + deploy.

## Local preview (Windows)
Hugo exe path (winget install):
`C:\Users\senta\AppData\Local\Microsoft\WinGet\Packages\Hugo.Hugo.Extended_Microsoft.Winget.Source_8wekyb3d8bbwe\hugo.exe`

```powershell
$hugo='C:\Users\senta\AppData\Local\Microsoft\WinGet\Packages\Hugo.Hugo.Extended_Microsoft.Winget.Source_8wekyb3d8bbwe\hugo.exe'
cd .\blog\shortflow-blog
& $hugo server
```
