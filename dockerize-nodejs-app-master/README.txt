Ana dizinde docker file adında bir dosyanın olması gerekmektedir.
sonrasında dosya içerisindekiler bu şekilde olmalı ve projenin dockerda ayağa kalkması çalışması için de isminin docker olması gerekmektedir.

FROM node:10 --ben bu projedenode.js kullanacağım ve versiyonu 10 olacak dedik
WORKDIR /home/node/app benim çalışacağım imagein klasör yapısı burası olacak demek
COPY rest-api /home/node/app --restapi içerisindekilerin tümünü buraya aktarmak için yazıyoruz bu kısmı copy buradan geliyor
RUN npm install --node modules olabilsin ki proje çalışsın bu yüzden yazılıyor
CMD npm run start --projenin çalışması için gereken kod
EXPOSE 3000 --hangi port üzerinden çalışacağının bilgisi

ana dizine geliyoruz docker üzerinde çalışabilmesi için docker build --tag node-rest-api . ismini verdik
docker images diyerek docker üzerinde olan projeleri görebiliriz bizim projemizde node-rest-api olarak var olacak
şimdi docker image'i oluştu bunu nasıl çalıştırabiliriz port tanımlayarak--> docker run -p 3000:3000 node-rest-api 
ilk port kendi isteğimizde göre ikincisi expose'da yazdığımız 3000 olmalı 

FROM node:10
WORKDIR /home/node/app
COPY rest-api /home/node/app
RUN npm install
CMD npm run start
EXPOSE 3000