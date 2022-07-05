# Шпаргалка для установки Git на сервер

## Инициализация гит на сервере
```
git init
git remote add origin url_репозитория
git fetch origin
```

Чтобы изменить ссылку на репозиторий
```
git remote set-url origin https://git-repo/new-repository.git
```
## Пользователь и доступы

Просмотр параметров
```
git config --list
```
Изменение параметров пользователя при загрузке
```
git config user.name "John Doe"
git config user.email johndoe@example.com
```
### SSH ключ
Лучше всего генерировать на сервере SSH ключ и добавить его [в свой лк Git](https://github.com/settings/keys). Более подробная инструкция по SSH-ключам [тут](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
Для доступа по SSH ключу ссылка на репо должна выглядеть следующим образом:

git@github.com:CedroAgency/immunohealth.git

![SSH repo link](images/24/git_ssh.png)

### HTTPS + access token
Если хостинг слишком простой и генерация ключа недоступна, можно воспользоваться старым методом

Для этого необходимо получить [access token](https://github.com/settings/tokens) и получить HTTPS ссылку на репозиторий вида 

https://github.com/CedroAgency/project.git

![HTTPS repo link](images/24/git_https.png)

Теперь необходимо изменить ссылку на удаленный репозиторий на сервере
```
git remote set-url origin https://GIT_USER_NAME:ACCESS_TOKEN@github.com/CedroAgency/project.git
```

## Первый коммит
```
git reset --mixed origin/main
git add измененные файлы
git commit -m "комментарий к коммиту"
git push -u origin main
```

## Залив в production

Использовать только для **ПОЛНОЙ** замены production на main на боевом сервере. 

```
git fetch --all
git reset --hard origin/main
git pull origin main
```