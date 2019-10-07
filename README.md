# build-quasar-framework-app
How to build a Quasar Framework App

> Na pasta do app: 

quasar build

quasar build -m cordova -T android


> entre na pasta bin da jdk do java e gera uma genkey. ps: alias = nome do app/projeto

**cd C:\Program Files\Java\jdk1.8.0_161\bin:**

 keytool -genkey -v -alias <alias> -keyalg RSA -keysize 2048 -validity 20000 (Se não tiver certificado)

> Assina o app-release-unsigned que se encontra na raiz do projeto com a .keystore gerada no passo anterios.

> Obs: para o mesmo projeto, não há necessidade de criar novos certificados.

**cd C:\Program Files\Java\jdk1.8.0_161\bin :**
  
  jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore <endereço de .keystore> <endereço de app-release-unsigned.apk> <nome do app>

> gerar .apk efinitiva

**cd C:\Users\User\AppData\Local\Android\Sdk\build-tools\27.0.3:**

  zipalign -v 4 <endereço de app-release-unsigned.apk> <nome do app>.apk
  
