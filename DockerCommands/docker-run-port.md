## docker container run -d -p 80:80 httpd

- docker container run -d -p 80:80 httpd -> komutunu çalıştırırsak, httpd registry'sindeki default uygulamayı "80:80" portundan çağırırız. "-d" komutu sayesinde container'ı detach ederiz yani arkaplanda çalıştırırız. Yani loglarını/çıktılarını kendi shell'imizde görmeyiz ama container arkada çalışmaya devam eder: