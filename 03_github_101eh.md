```bash
docker run -it alpine '/bin/sh'
apk add git

git config --global user.email "ben@tomblins.com"
git config --global user.name "btomblin"
git config --global credential.helper cache

git config --global user.email "aaa+1@tomblins.com"
git config --global user.name "aaa-dev-1"
git config --global credential.helper cache

git config --global user.email "aaa+2@tomblins.com"
git config --global user.name "aaa-dev-2"
git config --global credential.helper cache

git clone https://github.com/btomblin/dept-appname.git
```