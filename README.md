# DAAG-YOLO 图像数据集

本仓库保存根茎类中药材种苗视觉识别项目中训练使用的图像数据，共 **1,536 张 JPG 图片**，保留原有训练、验证和测试划分。

| 划分 | 图片数量 |
| --- | ---: |
| train | 1,075 |
| val | 231 |
| test | 230 |
| 合计 | 1,536 |

## 文件结构

```text
DAAG-YOLO/
├── images/
│   ├── train/
│   ├── val/
│   └── test/
├── dataset_summary.json
├── manifest.sha256
└── README.md
```

图片总大小为 **1,100,588,948 字节**（约 1.10 GB）。各划分的确切大小见 `dataset_summary.json`。

## 完整性校验

全部 1,536 张图片与源文件进行了 SHA-256 比较，内容一致。`manifest.sha256` 列出每张图片的校验值及相对路径。

在提供 `sha256sum` 的终端中，进入数据集根目录执行：

```bash
sha256sum -c manifest.sha256
```

PowerShell 校验方式：

```powershell
Get-Content -LiteralPath manifest.sha256 | ForEach-Object {
    $parts = $_ -split '  ', 2
    $actual = (Get-FileHash -LiteralPath $parts[1] -Algorithm SHA256).Hash
    if ($actual -ne $parts[0]) { throw "SHA-256 mismatch: $($parts[1])" }
}
```
