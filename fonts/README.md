# 字型

版型使用 [Noto Sans TC](https://fonts.google.com/noto/specimen/Noto+Sans+TC)（SIL Open Font License）。從 Google Fonts 下載後，把壓縮檔 `static/` 資料夾裡的這兩個檔案放到這裡：

- `NotoSansTC-Regular.ttf`
- `NotoSansTC-Bold.ttf`

字型檔不進版本控制。

字型放在別的地方時，在載入版型之前設定資料夾路徑（結尾要有 `/`）：

```latex
\def\codexfontpath{C:/path/to/Noto_Sans_TC/static/}
```

詳解版型的英文題目框使用 TeX Gyre Termes，TeX Live 已內建，不用另外安裝。
