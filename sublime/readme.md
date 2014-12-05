# Sublime 기능

사이트 : http://www.sublimetext.com/

## 패키지 설치

메뉴 View > Show Console 을 선택해서 Console 창을 열고 아래의 명령어를 입력하고 엔터

Sublime Text 2

```cmd
import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print('Please restart Sublime Text to finish installation')
```

Sublime Text 3

```cmd
import urllib.request,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

패키지 명령

메뉴 Tools > Command Palette 를 선택 하거나 `shift+command+p` 를 사용하여 실행한다.

* Install Pacakge : 패키지를 설치하는 명령
* List Package : 설치된 패키지 목록을 보여준다.
* Remove Pacakage :  패키지를 삭제한다.


### 참고블로그

http://opentutorials.org/module/406/3629
