# OcrMyPDf 使用方法
    引言：
        OCRmyPDF 是一个用于将扫描的 PDF 文件转换为可搜索和可编辑格式的工具。
    它使用 Tesseract OCR 引擎来识别文本并将其嵌入到原始文档中，
    从而创建带有文本层的 PDF。这使得用户可以复制、查找或编辑 PDF 中的内容，

适用场景:
- 扫描的 PDF 文件需要转换为可搜索和可编辑格式。
- 需要将纸质文档转换为电子格式以便于存档或共享。
- 低质量或模糊的 PDF(图像分辨率低、文字模糊，但仍有可识别的文字内容。)
- 非拉丁语系文字的 PDF(包含中文、日文、阿拉伯文等非拉丁语系文字的扫描件。)
- 需要优化或压缩的 PDF 文件，以提高可读性和文件大小。






## 不通过系统安装

### 不同系统安装指令
```bash
Debian, Ubuntu  Debian 和 Ubuntu 

apt install ocrmypdf

Windows Subsystem for Linux
适用于 Linux 的 Windows 子系统

apt install ocrmypdf

Fedora  软呢帽

dnf install ocrmypdf tesseract-osd

macOS (Homebrew)  macOS（自制软件）

brew install ocrmypdf

macOS (MacPorts)  macOS （MacPorts）

port install ocrmypdf

LinuxBrew  LinuxBrew 软件

brew install ocrmypdf

FreeBSD  FreeBSD 软件

pkg install textproc/py-ocrmypdf

Snap (snapcraft packaging)
Snap （snapcraft 包装）

snap install ocrmypdf

```

### 安装其他语言包
OCRmyPDF 使用 Tesseract 进行 OCR，并依赖于其适用于所有语言的语言包。在大多数平台上，English 默认与 Tesseract 一起安装，但并非总是如此。


安装语言包后，您可以将其与 ocrmypdf -l <language> 一起使用，例如 ocrmypdf -l spa。对于多语言文档，您可以指定所有预期的语言，例如，ocrmypdf -l eng+fra 用于英语和法语。除非指定了其他语言，否则默认使用英语。


```bash
apt install tesseract-ocr-chi-sim
```

#### Platform install steps(平台安装步骤)
##### Debian and Ubuntu (apt) 以这个为例
[其他平台参考官方教程](https://ocrmypdf.readthedocs.io/en/latest/languages.html)

```bash
# Display a list of all Tesseract language packs
apt-cache search tesseract-ocr

# Install Chinese Simplified language pack
apt-get install tesseract-ocr-chi-sim
```

原文: You can then pass the -l LANG argument to OCRmyPDF to give a hint as to what languages it should search for. Multiple languages can be requested using either -l eng+fra (English and French) or -l eng -l fra.

译文: 然后，您可以将 -l LANG 参数传递给 OCRmyPDF，以提示它应该搜索哪些语言。可以使用 -l eng+fra （英语和法语） 或 -l eng -l fra.
## 常用命令
```bash
# 基础OCR（保留原图，添加文本层）
ocrmypdf input.pdf output.pdf

# 指定中文+优化压缩
ocrmypdf -l chi_sim --optimize 3 input.pdf output.pdf

# 处理低质量扫描件（自动纠斜+降噪）
ocrmypdf --deskew --clean input.pdf output.pdf
```