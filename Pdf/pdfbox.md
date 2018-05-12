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

java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180418170820.pdf  -outputPrefix 21_BML_NK세포활성도_검사
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180509113150.pdf  -outputPrefix 25_BML_유전체검사
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180418170859.pdf  -outputPrefix 26_골대사검사
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180418170342.pdf  -outputPrefix 27_수면검사
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180418170251.pdf  -outputPrefix 30_녹십자_중금속검사 
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180419152715.pdf  -outputPrefix 31_녹십자_활성산소검사
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180418170337.pdf  -outputPrefix 32_메디젠_유전자검사
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180418165844.pdf  -outputPrefix 28_녹십자_알레르기검사
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180418170208.pdf  -outputPrefix 29_녹십자_알레르기검사

java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180509113417.pdf  -outputPrefix 212_BML_NK세포활성도_검사
java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180508172803.pdf  -outputPrefix 213_BML_NK세포활성도_검사

### Report View (jspdf)

    https://brunch.co.kr/@ourlove/60


### PDFSplit

Usage: java -jar pdfbox-app-x.y.z.jar PDFSplit [OPTIONS] <PDF file>

```
java -jar pdfbox-app-2.0.8.jar PDFSplit -startPage 1 -endPage 12 -outputPrefix OUT IH20180326075759.pdf 
```

