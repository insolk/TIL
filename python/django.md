- ## Django 기본 구조

  > SoC(Seperation of concerns(responsibility)) - 관심사의 분리
  >
  > [Django’s Structure Link](https://djangobook.com/mdj2-django-structure/)

  ### MVC, MTV Pattern

  - MVC (ex - Spring Framework)
    - Model - DB연동
    - View - 화면(UI)
    - Controller - 중재자, 로직 포함
  - MTV (ex - Django Framework)
    - Model - DB연동
    - Template - 화면(UI)
    - View - 중재자, 로직 포함

  - 모듈간의 독립성, 느슨한 결합(Loose Coupling) 가능

  

  #### URLCONF

  - URL 요청에 맞게 작업할 수 있게 설정해 놓은 설정값
  - `urls.py`

  #### View

  - 요청에 따라 작업을 수행해주는 중재자 역할
  - 요청에 따른 함수가 적혀있는 로직 정의
  - `views.py`

  #### Model

  - 데이터베이스를 통해 데이터 주고 받음
  - `models.py`

  #### Template

  - HTML 응답 소스를 통해 화면에 출력해주는 역할
  - html, css, js

  

  ### ORM(Object Relational Mapping)

  > 객체를 RDB의 Table로 매핑

  - Mapping Rule
    - Model Class <-> Table
    - Object <-> Row(Record)
    - Variable <-> Column

  ## Django 프로젝트 생성

  >  `django-admin startproject mydjango . `

  => django/conf/project_template 구성으로 생성 됨 

  

  [Django template](https://github.com/django/django/tree/master/django/conf/project_template)

  - manage.py : 웹사이트 관리를 도와주는 역할을 하는 파일
  - settings.py : 웹사이트 설정이 있는 파일 
  - urls.py : urlresolver가 사용하는 요청 패턴(URL규칙) 목록을 포함하고 있는 파일
  - wsgi.py : Web Server Gateway Interface이며 Python의 표준 Gateway Interface 입니다.
  - asgi.py : Asynchronous Server Gateway Interface WSGI와 비슷한 구조를 가지며, 비동기 통신을 지원한다.

  

  ## Django url Process

  - http://localhost:8000으로 접속
    - 1. mydjango_pri/urls.py
      2. blog/urls.py : URL Mapping
         - path('', views.post_list, name='post_list'),
      3. blog/views.py/post_list() : View

  

  ## Template engine

  - block 태그를 통해 상속 가능

  - comment 태그를 통해 주석 가능

    - 서버사이드이기 때문에 html주석과 다르게 클라이언트에서 주석이 보이진 않음

      ```html
      {% comment %}}
              django 주석
      {% endcomment %}
      ```

  - csrf_token 태그를 통해 csrf 공격 방지 가능

    - POST를 통해 사용

  - for ... empty 태그

    - for 정상적으로 순회 후 마지막에 empty문 수행

  

  ## Django query set 명령어 연습

  ```python
  (base) C:\mypython\django_fw>python manage.py shell
  Python 3.8.5 (default, Sep  3 2020, 21:29:08) [MSC v.1916 64 bit (AMD64)]
  Type 'copyright', 'credits' or 'license' for more information
  IPython 7.19.0 -- An enhanced Interactive Python. Type '?' for help.
  
  In [1]: from blog.models import Post
  
  In [2]: Post.objects.all()
  Out[2]: <QuerySet [<Post: 첫번째글>, <Post: 두번째글>]>
  
  In [3]: from django.contrib.auth.models import User
  
  In [4]: User.objects.all()
  Out[4]: <QuerySet [<User: admin>]>
  
  In [5]: User.objects.get(username='admin')
  Out[5]: <User: admin>
  
  In [6]: me = User.objects.get(username='admin')
  
  In [7]: me
  Out[7]: <User: admin>
  
  In [8]: type(me)
  Out[8]: django.contrib.auth.models.User
  
  In [9]: me.id
  Out[9]: 1
  
  In [10]: me.username
  Out[10]: 'admin'
  
  In [11]: me.email
  Out[11]: 'admin@aa.com'
  
  In [12]: me.password
  Out[12]: 'pbkdf2_sha256$216000$bYruaE4pjpaC$ZuOJ6bsxXvAjwQ/gR9VhNGUf1wRyvf7MiAMMC0UlBKU='
  
  In [14]: Post.objects.create(author=me, title='Sample title', text='Sample text')
  Out[14]: <Post: Sample title>
  
  In [15]: Post.objects.all()
  Out[15]: <QuerySet [<Post: 첫번째글>, <Post: 두번째글>, <Post: Sample title>]>
  
  In [16]: Post.objects.filter(author=me)
  Out[16]: <QuerySet [<Post: 첫번째글>, <Post: 두번째글>, <Post: Sample title>]>
  
  In [17]: Post.objects.filter(title__contains='title')
  Out[17]: <QuerySet [<Post: Sample title>]>
  
  In [18]: mypost = Post.objects.filter(title__contains='title')
  
  In [19]: mypost
  Out[19]: <QuerySet [<Post: Sample title>]>
  
  In [20]: type(mypost)
  Out[20]: django.db.models.query.QuerySet
  
  In [21]: for val in mypost:
      ...:     print(val)
      ...: 
  Sample title
  
  In [22]: myposts = Post.objects.filter(title__contains='글')
  
  In [23]: myposts
  Out[23]: <QuerySet [<Post: 첫번째글>, <Post: 두번째글>]>
  
  In [24]: type(myposts)
  Out[24]: django.db.models.query.QuerySet
  
  In [25]: for post in myposts:
      ...:     print(type(post), post.id)
      ...: 
  <class 'blog.models.Post'> 1
  <class 'blog.models.Post'> 2
  
  In [26]: from django.utils import timezone
  
  In [27]: timezone.now()
  Out[27]: datetime.datetime(2021, 1, 12, 8, 19, 50, 749674, tzinfo=<UTC>)
  
  In [28]: Post.objects.filter(published_date__lte=timezone.now())
  Out[28]: <QuerySet [<Post: 두번째글>]>
  
  In [29]: post3 = Post.objects.get(title="Sample title")
  
  In [30]: type(post3)
  Out[30]: blog.models.Post
  
  In [31]: post3.id
  Out[31]: 3
  
  In [32]: post3.text
  Out[32]: 'Sample text'
  
  In [33]: post3.published_date
  
  In [34]: post3.publish()
  
  In [35]: post3.published_date
  Out[35]: datetime.datetime(2021, 1, 12, 8, 25, 16, 76181, tzinfo=<UTC>)
  
  In [36]: Post.objects.filter(published_date__lte=timezone.now())
  Out[36]: <QuerySet [<Post: 두번째글>, <Post: Sample title>]>
  
  In [37]: Post.objects.order_by('created_date')
  Out[37]: <QuerySet [<Post: 첫번째글>, <Post: 두번째글>, <Post: Sample title>]>
  
  In [38]: Post.objects.order_by('-created_date')
  Out[38]: <QuerySet [<Post: Sample title>, <Post: 두번째글>, <Post: 첫번째글>]>
  
  In [39]: Post.objects.filter(published_date__lte = timezone.now()).order_by('published_date')
  Out[39]: <QuerySet [<Post: 두번째글>, <Post: Sample title>]>
  
  In [40]: Post.objects.filter(published_date__lte = timezone.now()).order_by('-published_date')
  Out[40]: <QuerySet [<Post: Sample title>, <Post: 두번째글>]>
  
  In [41]: from django.shortcuts import get_object_or_404
  
  In [42]: get_object_or_404(Post,pk=1)
  Out[42]: <Post: 첫번째글>
  
  In [43]: post1 = get_object_or_404(Post,pk=1)
  
  In [44]: type(post1)
  Out[44]: blog.models.Post
  
  In [45]: post1.title
  Out[45]: '첫번째글'
  
  In [46]: post1.text
  Out[46]: '첫번째글의 내용입니다.'
  
  In [47]: post1.created_date
  Out[47]: datetime.datetime(2021, 1, 12, 6, 22, 30, tzinfo=<UTC>)
  
  In [48]: delpost = Post.objects.get(title='Sample title')
  
  In [49]: delpost
  Out[49]: <Post: Sample title>
  
  In [50]: delpost.delete()
  Out[50]: (1, {'blog.Post': 1})
  
  In [51]: Post.objects.all()
  Out[51]: <QuerySet [<Post: 첫번째글>, <Post: 두번째글>]>
  ```

  