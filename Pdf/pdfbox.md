## PDF 관련자료

### PDFBox 사이트

https://pdfbox.apache.org

C:\Tools\PdfBox 폴더참고

### python에서 pdfbox 사용하기

https://github.com/lebedov/python-pdfbox

### PDFBox 한글문서

http://www.w3ii.com/ko/pdfbox/pdfbox_overview.html

### PDFBox 이슈
https://issues.apache.org/jira/projects/PDFBOX/issues/PDFBOX-45?filter=allopenissues

### PDFDebugger 

https://pdfbox.apache.org/1.8/commandline.html#pdfdebugger

Usage: java -jar pdfbox-app-x.y.z.jar PDFDebugger [inputfile]
코멘트 창에서 아래의 명령을 사용한다.

java -jar pdfbox-app-2.0.8.jar PDFDebugger chapter5.pdf
java -jar pdfbox-app-2.0.8.jar PDFDebugger 20180503_계명대_원본.pdf
java -jar pdfbox-app-2.0.8.jar PDFDebugger 20180503_계명대_수정.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFDebugger PDF_테스트_맑은고딕.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFDebugger IH20180522084555.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFDebugger IH20180521162828_녹십자알레르기검사지.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFDebugger HY견고딕_IH20180523162435.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFDebugger 돋움_40193_12637.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFDebugger 돋움체_IH20180523162228.pdf


java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar ExtractText IH20180521162828.pdf

### PDF의 압축을 풀어준다.

java -jar pdfbox-app-2.0.8.jar WriteDecodedDoc charactor1.pdf charactor1.out.doc

### PDFToImage를 이미지로 변환한다.

java -jar pdfbox-app-2.0.8.jar PDFToImage -imageType png charactor1.pdf  -outputPrefix out

java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180612111013.pdf -outputPrefix 24_BML_알레르기검사


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

java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png IH20180418170546.pdf  -outputPrefix 33_바이오에이지_생체나이

java -jar c:/tools/pdfbox/pdfbox-app-2.0.8.jar PDFToImage -imageType png 160921_검진결과지_수정.pdf  -outputPrefix 160921_검진결과지

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180518162651.pdf  -outputPrefix 34_인바디1

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180518162651.pdf  -outputPrefix 34_인바디1

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180408181311.pdf  -outputPrefix 14_체성분 분석결과2

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180408181311.pdf  -outputPrefix 14_체성분 분석결과2

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180408181311.pdf  -outputPrefix 14_체성분 분석결과2

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType jpg NK검사보고서_설명.pdf -outputPrefix 21_NK활성도

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType jpg IH20180618172658.pdf -outputPrefix 28_동맥경화1

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType jpg IH20180618172742.pdf -outputPrefix 28_동맥경화2

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType jpg IH20180702091856.pdf -outputPrefix 17.1_체성분결과

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType jpg IH20180626190439.pdf -outputPrefix 30_중금속결과13

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180530170619_직무스트레스검사_3.pdf -outputPrefix 직무스트레스검사
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180601152014_혈중중금속_report.pdf -outputPrefix 혈중중금속

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180618151248.pdf -outputPrefix IH20180618151248

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180618151301.pdf -outputPrefix 22_BML_골다공증검사

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180508181315.pdf -outputPrefix 12_자율신경0601

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFToImage -imageType png IH20180703164844.pdf -outputPrefix 17_항상화력

### Report View (jspdf)
    https://brunch.co.kr/@ourlove/60

### PDFSplit

Usage: java -jar pdfbox-app-x.y.z.jar PDFSplit [OPTIONS] <PDF file>

```
java -jar pdfbox-app-2.0.8.jar PDFSplit -startPage 1 -endPage 12 -outputPrefix OUT IH20180326075759.pdf 

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 1 -endPage 1 -outputPrefix OUT 원본.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 1 -endPage 1 -outputPrefix IH20180602_01_1 IH20180602_01.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 2 -endPage 2 -outputPrefix IH20180602_01_2 IH20180602_01.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 3 -endPage 3 -outputPrefix IH20180602_01_3 IH20180602_01.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 4 -endPage 4 -outputPrefix IH20180602_01_4 IH20180602_01.pdf


java -jar c:/inbody/bin/pdfbox-app-2.1.0.jar PDFSplit -startPage 1 -endPage 1 -outputPrefix IH20180602_01_1 IH20180602_01.pdf
java -jar c:/inbody/bin/pdfbox-app-2.1.0.jar PDFSplit -startPage 2 -endPage 2 -outputPrefix IH20180602_01_2 IH20180602_01.pdf
java -jar c:/inbody/bin/pdfbox-app-2.1.0.jar PDFSplit -startPage 3 -endPage 3 -outputPrefix IH20180602_01_3 IH20180602_01.pdf
java -jar c:/inbody/bin/pdfbox-app-2.1.0.jar PDFSplit -startPage 4 -endPage 4 -outputPrefix IH20180602_01_4 IH20180602_01.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 156 -endPage 167 -outputPrefix IH20180620093116_1 IH20180620093116.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 168 -endPage 179 -outputPrefix IH20180620093116_2 IH20180620093116.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 12 -endPage 22 -outputPrefix IH20180620093116_3 IH20180620093116.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFMerger  IH20180620093116_1-1.pdf IH20180620093116_2-1.pdf IH20180620093116_3-1.pdf IH20180620093116_A.pdf


java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 135 -endPage 145 -outputPrefix IH20180627143417_1 IH20180627143417.pdf

-- 김윤천

IH20180627154851.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 2 -endPage 2 -outputPrefix IH20180627154851_1 IH20180627154851.pdf
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFSplit -startPage 1 -endPage 27 -outputPrefix ad746ab1bf7b4c05baf656905304a5e5_1 ad746ab1bf7b4c05baf656905304a5e5.pdf


```

### PDFMerger

```
java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFMerger  OUT-1.pdf OUT2-1.pdf all.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFMerger  IH20180504152539.pdf IH20180504152558.pdf IH20180604152558.pdf

java -jar c:/tools/pdfbox/pdfbox-app-2.1.0.jar PDFMerger  IH20180518162651.pdf IH20180518162657.pdf IH20180518162702.pdf IH20180518162702ALL.pdf

```

### 메디에이지 텔로미어 계정

https://www.cloudike.kr/

mediagetelomere@gmail.com / mediage12#$
복구메일 주소 : skc3779@mediage.co.kr

### 웹하드 만들기

https://mediage.cloudike.kr

관리
skc3779@mediage.co.kr
mediage12#$

차움병원
sungh000@mediage.co.kr
sungh12#$
