# 在vercel部署django示例

## 部署所需文件

1、 requirements.txt
2、 vercel_build.sh
3、 vercel.json
3、 修改wsgi.py

## 修改wsgi.py

需要在wsgi.py文件里添加app变量

```
application = get_wsgi_application()

# 添加这一句
app = application
```

## 修改setttings.py

添加收集静态文件的配置

```
STATICFILES_DIRS = [BASE_DIR/'static',]
STATIC_ROOT = BASE_DIR/'staticfiles'
```

如果不使用数据库，需要去掉默认的sqlite配置

```
DATABASES = {
    # 'default': {
    #     'ENGINE': 'django.db.backends.sqlite3',
    #     'NAME': BASE_DIR / 'db.sqlite3',
    # }
}
```

如果需要使用云数据库，需要修改上面的配置，然后执行下面命令

```
python manage.py makemigrations
python manage.py migrate
```

## vercel部署截图

配置截图

![](screenshot/config.png)

部署成功截图

![](screenshot/success.png)


## 参考资料

- https://dev.to/ksharma20/how-to-deploy-a-django-web-app-on-vercel-for-free-4fhe
