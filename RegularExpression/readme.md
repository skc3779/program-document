#### 자바 정규식
> http://egloos.zum.com/js7309/v/11117112

```
메타문자
.      -  문자를 찾음
\s     -  공백 문자 찾기
\S     -  공백 문자가 아닌것 찾기  [^\\s]
\S+    -  여러 공백 문자가 아닌 것 찾기
\d     -  모든 숫자 찾기
          String test = "12345A".replaceAll("\\d", "");  // A
          String test = "12345A".replaceAll("[0-9]", ""); // A
\D     -  숫자가 아닌것 찾기
          String test = "12345A".replaceAll("\\d", "");  // 12345
          String test = "12345A".replaceAll("[^0-9]", ""); // 12345
\w     -  모든 문자 와 숫자 찾기 
          String test = "12345A".replaceAll(\\w, "");  // 
          String test = "12345A".replaceAll("[a-zA-Z_0-9]", ""); // 
\w     -  모든 문자 와 숫자  외에 것을  찾기 
          String test = "12345A$".replaceAll(\\W, "");  // $ 
          String test = "12345A".replaceAll("[^a-zA-Z_0-9]", ""); // $ 
\b     -  첫글자  ex) \\b(\\w) : 모든 단어의 첫 글자
```