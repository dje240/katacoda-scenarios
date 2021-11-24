Веб-консоль OpenShift предоставляет удобные визуальные инструменты контроля производственного процесса. Однако не все задачи можно оперативно выполнить через неё. В любом случае понадобятся навыки работы с интерфейсом командной строки.

В данном сценарии CLI доступен через терминал и устанавливать отдельный инструмент не нужно.

Если вы уже работаете с кластером OpenShift без CLI, вы можете скачать инструмент для доступа через веб-консоль к интерфейсу CLI в пункте _Command Line Tools_ .

![Command Line Tools](../../assets/introduction/cluster-access-44/02-command-line-tools.png)

Ссылка на подробную информацию о том, где получить инструменты командной строки, также будет показана на начальной странице приветствия, когда вы впервые обращаетесь к кластеру.

Как только вы перейдете к списку загрузок, вам нужно будет загрузить архив для вашей платформы, распаковать бинарный файл установить его.

Чтобы войти в кластер OpenShift, используемый для этого курса, запустите в терминале:

``oc login -u developer -p developer``{{execute}}

Вы увидите следующий вывод терминала:

```
Authentication required for https://openshift:6443 (openshift)
Login successful.

Так как созданных проектов ещё нет, создаем первый при помощи команды:

    oc new-project <projectname>
```
Далее задаём пространство имён (namespace):

``oc new-project myproject``{{execute}}

Следующей командой можно вывести доступные нам проекты:

``oc get projects``{{execute}}

Проверить пользователя, под которым мы сейчас "залогинились" можно командой:

``oc whoami``{{execute}}

Также в целях безопасности важно проверить имя нашего текущего сервера:

``oc whoami --show-server``{{execute}}

Аутентификация при момощи внешнего провайдера требует дополнительных действий.

При использовании команды ``oc login`` командная строка возвращает следующую ошибку:

```
Login failed (401 Unauthorized)
You must obtain an API token by visiting
  https://api.starter-us-east-1.openshift.com/oauth/token/request
```

You would visit the link given, logging in first via the separate authentication service if necessary. You will then be redirected to a page which will give details of the login command to use. This will include an access token to authenticate you for the session.

Even in the case where user authentication is managed by the OpenShift cluster and user credentials are accepted, you can opt to instead use an access token. You can retrieve the command to run by manually entering the ``/oauth/token/request`` path against the URL for the cluster access endpoint.

If you are already logged into the web console, you can also retrieve the details of the login command and access token by accessing the _Copy Login Command_ menu option under your login name.

 ![Request Access Token](../../assets/introduction/cluster-access-44/02-login-access-token.png)

Whichever mechanism you use to login from the command line using ``oc login``, the login will periodically expire and you will need to login again. The expiration period is typically 24 hours.
