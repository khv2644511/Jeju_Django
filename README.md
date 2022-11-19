# Jeju_Django
장고 공부해보기

https://paullab.co.kr/about.html https://jejucodingcamp.notion.site/jejucodingcamp/Jeju-Coding-Basecamp-Home-ff529a96a4e5497eaadd7c5b12b60328


```mkdir mysite

python -m venv venv

source venv/bin/activate

pip install django==3.2

django-admin startproject tutorialdjango .`

python manage.py migrate
```

```
python manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying auth.0012_alter_user_first_name_max_length... OK
  Applying sessions.0001_initial... OK
```

```
python manage.py runserver 8080
```

### ./tutorialdjango/settings.py
```
# Application definition

INSTALLED_APPS = [
    "main",
    "django.contrib.admin",
    "django.contrib.auth",
    "django.contrib.contenttypes",
    "django.contrib.sessions",
    "django.contrib.messages",
    "django.contrib.staticfiles",
]
```


### URL 설계

- 서비스를 어떻게 만들고 싶으신가요?
```
/ -> home
/about
/product
/contact
```
- figma로 설계를 할 수 있습니다.
- 홈페이지 기획자가 UI와 URL을 설계합니다.
- 백엔드 개발자가 URL을 사용할 수도 있습니다.
- 기획자가 URL을 하면 규칙에 잘 맞지 않는 경우가 있습니다.
- ./tutorialdjango/urls.py에서 설정할 수 있습니다.


### ./tutorialdjango/urls.py
```
from django.contrib import admin
from django.urls import path
from main.views import index

urlpatterns = [
    path("admin/", admin.site.urls),
    path("/", index),
]
```

```
from django.contrib import admin
from django.urls import path
from main.views import index, about, product, contact

urlpatterns = [
    path("admin/", admin.site.urls),
    path("", index),
    path("about/", about),
    path("product/", product),
    path("contact/", contact),
]

```

### ./main/views.py

```

from django.shortcuts import render


def index():
    pass


def about():
    pass


def product():
    pass


def contact():
    pass

```

### ./main/views.py
```
from django.shortcuts import render


def index(request):
    return render()


def about(request):
    return render()


def product(request):
    return render()


def contact(request):
    return render()
    
```
- render()가 하는 역할은 django template 파일을 django가 해석하는 역할을 합니다.
- https://docs.djangoproject.com/en/3.2/topics/http/shortcuts/#render


### ./main/views.py

```
from django.shortcuts import render


def index(request):
    return render(request, "index.html")


def about(request):
    return render(request, "about.html")


def product(request):
    return render(request, "product.html")


def contact(request):
    return render(request, "contact.html")
```
- 위 파일을 django의 설정에 있는 템플릿 폴더를 찾습니다.


### 생성한 *.html
```
<h1>Hello product!</h1>
```

### 실행해볼까요?
```
python manage.py runserver 8080
``` 


### 과제
/a -> a 출력 /b -> b 출력 /c -> c 출력

import pandas data = pd.read_html
