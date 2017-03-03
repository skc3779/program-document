## tensorflow

### install mac

```bash
sudo easy_install pip
sudo pip install --upgrade virtualenv
```

virtualenv 환경을 만들기

```bash
virtualenv --system-site-packages ~/tensorflow

```

아래와 같이 tensorflow 폴더에 파일이 생성됨

```bash
(tensorflow) SeoKangChunui-iMac:tensorflow seokangchun$
.
├── bin
├── include
├── lib
└── pip-selfcheck.json
```

virsualenv 활성화

```bash
source ~/tensorflow/bin/activate #bash 사용 시
```

tensorflow 설치

```bash
sudo pip install --upgrade https://storage.googleapis.com/tensorflow/mac/tensorflow-0.9.0-py2-none-any.whl
```

최신버전을 설치하고 싶으면 아래와 같이 설치하면 됩니다.
> 현시점의 최신버전 @2016-12-04
> https://tensorflow.blog/

```bash
# Mac OS X, GPU enabled, Python 2.7:
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/gpu/tensorflow_gpu-0.12.0rc0-py2-none-any.whl
# Mac OS X, GPU enabled, Python 3.4 or 3.5:
$ export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/mac/gpu/tensorflow_gpu-0.12.0rc0-py3-none-any.whl

sudo pip install --upgrade $TF_BINARY_URL
```

### tensorboard

tensorboard 실행하기

```bash
tensorboard --logdir=/Users/seokangchun/tensorflow/logs # logdir 경로를 잡아준다.
```
접속 : http://localhost:6006/
문서 : https://www.tensorflow.org/versions/master/how_tos/graph_viz/index.html

```bash
```

```bash
```


```bash
```


```bash
```


```bash
```