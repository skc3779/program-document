## PDF 관련자료

### PDFBox 사이트

https://pdfbox.apache.org

C:\Tools\PdfBox 폴더참고

### python에서 pdfbox 사용하기

https://github.com/lebedov/python-pdfbox

### PDFBox 한글문서

http://www.w3ii.com/ko/pdfbox/pdfbox_overview.html

### PDFDebugger 

https://pdfbox.apache.org/1.8/commandline.html#pdfdebugger

Usage: java -jar pdfbox-app-x.y.z.jar PDFDebugger [inputfile]
코멘트 창에서 아래의 명령을 사용한다.

java -jar pdfbox-app-2.0.8.jar PDFDebugger chapter5.pdf
java -jar pdfbox-app-2.0.8.jar PDFDebugger 20180503_계명대_원본.pdf
java -jar pdfbox-app-2.0.8.jar PDFDebugger 20180503_계명대_수정.pdf

### PDF의 압축을 풀어준다.

java -jar pdfbox-app-2.0.8.jar WriteDecodedDoc charactor1.pdf charactor1.out.doc

### PDFToImage를 이미지로 변환한다.

java -jar pdfbox-app-2.0.8.jar PDFToImage -imageType png charactor1.pdf  -outputPrefix out

### Report View (jspdf)

    https://brunch.co.kr/@ourlove/60


### PDFSplit

Usage: java -jar pdfbox-app-x.y.z.jar PDFSplit [OPTIONS] <PDF file>

```
java -jar pdfbox-app-2.0.8.jar PDFSplit -startPage 1 -endPage 12 -outputPrefix OUT IH20180326075759.pdf 
```