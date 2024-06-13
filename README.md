# Other-MailServer

```
郵箱伺服器
```

## 目錄

- [Other-MailServer](#other-mailserver)
  - [目錄](#目錄)
  - [參考資料](#參考資料)
- [用法](#用法)

## 參考資料

[Docker Mailserver(後端郵件伺服器)](https://github.com/open222333/Other-Note/blob/main/03_%E4%BC%BA%E6%9C%8D%E5%99%A8%E6%9C%8D%E5%8B%99/MailServer(%E9%83%B5%E7%AE%B1%E4%BC%BA%E6%9C%8D%E5%99%A8)/Docker%20Mailserver(%E9%83%B5%E4%BB%B6%E4%BC%BA%E6%9C%8D%E5%99%A8).md)

[RainLoop(Web 郵件客戶端)](https://github.com/open222333/Other-Note/blob/main/03_%E4%BC%BA%E6%9C%8D%E5%99%A8%E6%9C%8D%E5%8B%99/MailServer(%E9%83%B5%E7%AE%B1%E4%BC%BA%E6%9C%8D%E5%99%A8)/RainLoop(Web%20%E9%83%B5%E4%BB%B6%E5%AE%A2%E6%88%B6%E7%AB%AF).md)

[Poste.io(郵件伺服器管理工具)](https://github.com/open222333/Other-Note/blob/main/03_%E4%BC%BA%E6%9C%8D%E5%99%A8%E6%9C%8D%E5%8B%99/MailServer(%E9%83%B5%E7%AE%B1%E4%BC%BA%E6%9C%8D%E5%99%A8)/Poste.io(%E9%83%B5%E4%BB%B6%E4%BC%BA%E6%9C%8D%E5%99%A8%E7%AE%A1%E7%90%86%E5%B7%A5%E5%85%B7).md)

# 用法

```bash
git clone https://github.com/open222333/Other-MailServer.git mail_server
cd mail_server
```

```bash
domain_name="yourdomain.com"
cp .env.sample .env
cp conf/admin.example.com.conf conf/nginx/admin.$domain_name.conf
cp conf/mail.example.com.conf conf/nginx/mail.$domain_name.conf
cp conf/postfix-main.cf.bak conf/docker-mailserver/postfix-main.cf
sed -i "s/example.com/$domain_name/g" .env
sed -i "s/example.com/$domain_name/g" conf/docker-mailserver/postfix-main.cf
sed -i "s/example.com/$domain_name/g" conf/nginx/admin.$domain_name.conf
sed -i "s/example.com/$domain_name/g" conf/nginx/mail.$domain_name.conf
```

```bash
cp -r /etc/letsencrypt/live/$domain_name conf/ssl
```

```bash
docker-compose up -d
```
