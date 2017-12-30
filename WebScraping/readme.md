## 웹스크래핑 관련 자료

### Python CSV 라이브러리

 CSV File Reading and Writing
 https://docs.python.org/3.4/library/csv.html

#### how to add unicode in truetype0font on pdfbox 2.0.0?

https://stackoverflow.com/questions/39485920/how-to-add-unicode-in-truetype0font-on-pdfbox-2-0-0

### Python PDF parser and analyzer

https://pypi.python.org/pypi/pdfminer3k

### PDF문서내에 있는 font 추출하기

https://m.blog.naver.com/PostView.nhn?blogId=sekterra&logNo=150117769978&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F

### PDF 파일의 텍스트 복사 한글 등의 문자 깨짐
http://thinking1.tistory.com/436


### 오픈리파인

메타웹이라는 회사에서 2009년에 시작한 오픈소스 프로젝트임 

[사이트]:http://openrefine.org
[참고문서]:https://github.com/OpenRefine/OpenRefine

### NLTK 자연어 툴킷

http://www.nltk.org/install.html

Mining English and Korean text with Python
https://www.lucypark.kr/courses/2015-ba/text-mining.html


### requests 라이브러리

복잡한 HTTP 요청과 쿠키, 헤더를 잘 처리해 줌.

http://www.python-requests.org

$> pip install requests

### 셀레니움으로 파이썬에서 자바스크립트 실행

https://pypi.python.org/pypi/selenium


### 팬텀JS 사이트 10장

팬텀 JS는 완전한 브라우저이고 파이썬 라이브러리가 아니므로  pip같은
패키지 관리자로는 설치할 수 없고 직접 내려바당서 설치해야 한다.
http://phantomjs.org/download.html


이슈) 윈도우 콘솔에서 console.log로 출력된 경우 유니코드 문자열이 깨저 보임
phantomjs.exe --output-encoding=utf8 --script-encoding=utf8 url2src.js URL download.html


### 이미지 처리 라이브러리 11장

필로 Pillow, 테서랙트 Tesseract

#### 필로

http://pillow.readthedocs.org

#### 테서랙트

https://github.com/tesseract-ocr/tesseract/wiki

테서랙트는 OCR라이브러리로 OCR과 머신러닝으로 유명한 구글의 투자를 받고 가장 정확한 최고의
오픈 소스 OCR시스템으로 인정받고 있음.

테서렉트 데이터 파일

https://github.com/tesseract-ocr/tesseract/wiki/Data-Files


#### 설치하기

###### MacOS

Homebrew

```
brew install tesseract

install location
/usr/local/Cellar/tesseract/3.05.01

```
.bash_profile 에 환경변수 추가.

#### 트레이닝 방법

https://github.com/tesseract-ocr/tesseract/wiki/TrainingTesseract


#### tesseract command line 인식 테스트 해보기

http://swlock.blogspot.kr/2016/08/tesseract-command-line.html


#### 블로그 자료

http://wookiist.tistory.com/9


### ABBYY 위 TESSERACT 보가 인식율 좋으나 상용.


### Pandas 

https://pandas.pydata.org/

참고서적 파이썬 라이브러리를 활용한 데이터 분석(한빛미디어 2013)
