-	###设置config文件###

```javascript
#个人工作账号
#邮箱地址:chao.guo@alibaba-inc.com
host gitlab.alibaba-inc.com
    hostname gitlab.alibaba-inc.com
    Port 65095
    User 显庆
    IdentityFile /Users/randolph/.ssh/id_rsa
#  我的github账号
#email:deserteagle249@gmail.com
host github.com
    hostname github.com
    Port 22
    User randolph
    IdentityFil /Users/randolph/.ssh/private
```

-	修改config定义

```javascript
1.取消global
git config --global --unset user.name
git config --global --unset user.email

2.设置每个项目repo的自己的user.email
git config  user.email "xxxx@xx.com"
git config  user.name "randolph"

```
