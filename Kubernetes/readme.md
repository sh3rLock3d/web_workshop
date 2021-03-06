<div dir="rtl">

# Kubernetes

برای آشنایی با مفهوم kubernetes ابتدا بهتره با container ها آشنایی داشته باشیم.

container ها شکل مجازی از سیستمهای عامل هستند . یک container ممکن برای اجرای microservice کوچک￼
تا یک برنامه بزرگ استفاده شود. در داخل یک container ، همه موارد اجرایی لازم ، کد باینری ، کتابخانه ها و پرونده های پیکربندی وجود دارد.در مقایسه با رویکردهای مجازی سازی سرور یا ماشین ، container ها حاوی تصاویر سیستم عامل نیستند و این باعث میشود که آنها سبک تر و قابل حمل باشند لذا به طور قابل توجهی سربار کمتری دارند. در برنامه های بزرگتر ، چندین container ممکن است به عنوان یک یا چند cluster  مستقر شوند. چنین خوشه هایی ممکن است توسط یک ارکستر container مانند Kubernetes مدیریت شوند.

Kubernetes (که به عنوان k8s یا "kube" نیز شناخته می شود) یک پلت فرم تنظیم متن باز است که بسیاری از
فرایندهای دستی مربوط به دیپلوی ، مدیریت و مقیاس سازی برنامه های کانتینر دار را به طور خودکار انجام می دهد ،


### با kubernetes چه کارهایی میتوان انجام داد؟
با kubernetes شما میتوانید:
 - بین چندین میزبان containers هایتان را تنظیم کنید. 
 - با بهبود بخشیدن استفاده از سخت افزار ، منابعی که برای اجرای برنامههاتان لازم هستند را بهبود ببخشید.
 - deployments و به روز رسانی برنامه ها را کنترل و خودکار کنید. 
 - برای اجرای برنامه های مناسب ، فضای ذخیره سازی را نصب و اضافه کنید. 
اجرای آنها در نظر گرفته اید ، اجرا می شوند.
 
 - با جایگذاری خودکار(auto placement) ، راه اندازی مجدد خودکار(auto restart) ، تکثیر خودکار(auto
replication) و مقیاس گذاری خودکار (auto scaling)، برنامه های خود را بررسی کرده و بهبود ببخشید.


### برخی از اصطلاحات رایج در Kubernetes :


panel control: مجموعه فرآیندهایی است که گره های Kubernetes را کنترل می کنند. تقسیم و تخصیص وظایف در این
بخش صورت میگیرد.


nodes: این ماشین ها درخواستهایی که توسط صفحه کنترل اختصاص داده شده را اجرا میکنند.


:Pod
گروهی از یک یا چند کانتینر که در یک گره مستقر می شوند. همه کانتینرهای موجود در یک pod دارای آدرس IP ، IPC ، نام میزبان و سایر منابع مشترک هستند.pods شبکه و فضای ذخیره سازی را container زیرین خود جدا میکنند.. با این کار می توانید container را به راحتی در خوشه جابجا کنید.



Replication controller: این کنترل می کند که چند نسخه یکسان از یک pod در بخشی از خوشه باید اجرا شود.


service: تعریف کار را از pods جا می کند. پروکسی های سرویس Kubernetes به طور خودکار درخواست خدمات
را به pod مناسب می رسانند - فرقی ندارد که این pod در کجای خوشه است یا جایگزین شده است یا نه.

Kubelet: این سرویس روی گره ها اجرا می شود ، manifest کانتینر را می خواند و از راه اندازی و در حال اجرا
بودن کانتینر تعریف شده اطمینان می


kubectl: ابزار پیکربندی خط فرمان برای kubernetes


برای این‌که بدانید kubernetes چگونه چنین قابلیت‌هایی را فراهم می‌کند، بهتر است درکی از چگونگی طراحی و سازماندهی آن در سطح بالا داشته باشید. kubernetes همانند یک سیستم در لایه‌ها ساخته‌شده که هر لایه بالا، جزییات لایه‌های پایینی را پنهان می‌کند. در پایه، kubernetes ماشین‌های مجازی و فیزیکی مجزا را کنار هم و درون یک کلاستر(خوشه) قرار می‌دهد و برای این کار از یک شبکه اشتراکی برای ارتباط بین هر سرور استفاده می‌کند. این کلاستر یک پلتفرم فیزیکی است که تمام اجزا، قابلیت‌ها و بار کاری آن پیکربندی شده‌اند. 



اکوسیستم kubernetes به هر ماشین درون کلاستر یک نقش می‌دهد. یک سرور (و گاهی گروه کوچکی از آن‌ها) به‌عنوان سرور ارشد انتخاب می‌شود. این سرور به‌عنوان یک دروازه و مغز کلاستر شناخته می‌شود و سلامتی دیگر سرورها را بررسی می‌کند، یک API به کاربران و کلاینت‌ها (مشتری‌‌ها) نشان می‌دهد، وظایف را به بهترین حالت تقسیم می‌کند و ارتباط بین سایر اجزا را هماهنگ می‌کند. سرور ارشد نقطه اتصال هر کلاستر است و مسئول بیشتر ویژگی‌هایی است که kubernetes در یک محیط متمرکز فراهم می‌کند.

ماشین‌های درون کلاستر به‌عنوان سرور گره (Node) شناخته می‌شوند: سرورها مسئول پذیرش و اجرای بار کاری هستند که از منابع محلی و خارجی استفاده می‌کنند. با کمک مدیریت، انعطاف‌پذیری و انزوا، kubernetes اپلیکیشن‌ها و سرویس‌ها را در کانتینر اجرا می‌کند. پس لازم است هر گره با یک مجری کانتینر (Runtime) مجهز شود، مانند داکر یا rkt. هر گره دستورات کاری خود را از سرور ارشد دریافت می‌کند و بر اساس آن کانتینرها را می‌سازد، از بین می‌برد و قوانین شبکه‌ای را تنظیم می‌کند تا ترافیک به بهترین نحو مسیریابی شود.

همان‌طور که در بالا گفته شد، اپلیکیشن‌ها و سرویس‌ها در کلاستر با یک کانتینر اجرا می‌شوند واجزای پایینی مطمئن می‌شوند که وضعیت اپلیکیشن مطابق با وضعیت کلاستر است. کاربران توسط سرور API اصلی با کلاستر ارتباط برقرار می‌کنند و این کار به‌صورت مستقیم یا با کمک کلاینت‌ها‌ و کتابخانه‌ها‌ انجام می‌شود. برای شروع کار یک اپلیکیشن یا سرویس، یک طرح در JSON یا YALM تعریف می‌شود و مشخص می‌شود که چه چیزی باید ایجاد و چگونه مدیریت شود. سپس سرور ارشد با توجه به زیرساخت و وضعیت سیستم، نحوه اجرا را مشخص می‌کند. این گروه از اپلیکیشن‌هایی که توسط کاربر تعریف شده‌اند، بر اساس برنامه‌های خاصی اجرا می‌شوند که در لایه آخر kubernetes ارائه‌شده است. 

![enter image description here](https://www.redhat.com/cms/managed-files/kubernetes_diagram-v3-770x717_0.svg)

 #### اجزای Master :

یک سرور ارشد حکم هسته کنترلی در کلاستر‌ها را دارد و نقطه ارتباطی میان کاربران و مدیران است. اجزای سرور ارشد با یکدیگر کار می‌کنند تا درخواست کاربر را پذیرش کنند، بهترین زمان‌بندی را برای بار کاری کانتینرها تعیین کرده، وضعیت شبکه‌سازی کلاستر را تنظیم و مسئولیت مدیریت، مقیاس‌بندی و سلامتی را بر عهده داشته باشند. این اجزا می‌توانند در یک ماشین مجزا نصب شوند یا در چند سرور به‌صورت توزیع‌شده قرار گیرند. در ادامه نگاهی به هر یک از اجزایی که با سرور ارشد پیوند خورده‌اند، خواهیم داشت.


#### etcd:

یکی از اجزای اصلی که kubernetes برای عملکردها به آن نیاز دارد، یک مخزن پیکربندی عمومی است. Etcd که توسط یک تیم در CoreOS توسعه‌یافته، یک مخزن از Key-valueها است که می‌تواند در محدوده گره‌ها پیکربندی شود. kubernetes از Etcd استفاده می‌کند تا پیکربندی‌های داده را که هر نود در کلاستر می‌تواند به آن دسترسی پیدا کند، ذخیره کند. این کار می‌تواند برای اکتشاف سرویس‌ها استفاده شود یا می‌تواند به پیکربندی اجزا یا پیکربندی مجدد آن‌ها بر اساس اطلاعات به‌روز شده کمک کند. همچنین برای حفظ وضعیت کلاستر با ویژگی‌هایی مانند انتخاب رهبر کاربرد دارد. 

همانند بیشتر اجزای دیگر در صفحه کنترلی، Etcd می‌تواند روی یک سرور ارشد پیکربندی شود یا بین تعدادی از ماشین‌ها توزیع شود. تنها چیزی که نیاز است دسترسی به شبکه برای ماشین‌های kubernetes است.


 #### Kube-Apiserver:


این سرویس، مدیر کنترلر یک سرویس مهم است که وظایف زیادی بر عهده دارد. این سرویس بار کار چرخه زندگی و کنترلرهایی را که از وضعیت تنظیم‌شده برای کلاستر خارج شده‌اند، مدیریت می‌کند و وظایف روزانه را انجام می‌دهد. جزییات این عملیات‌ها در Etcd نوشته‌شده، جایی‌که مدیر کنترلر تغییرات را از طریق سرور API مشاهده می‌کند. زمانی‌که تغییر مشاهده شد، کنترلر اطلاعات جدید را می‌خواند و رویه‌های مناسب را پیاده می‌کند. این مورد می‌تواند شامل گسترش یا کوچک کردن مقیاس اپلیکیشن، تنظیم نقطه پایانی یا موارد دیگر باشد.

#### kube-scheduler:

این سرویس پردازشی است که بار کاری را در زمان مشخص به یک نود مشخص واگذار می‌کند. این سرویس نیازهای عملیاتی بارکاری را می‌خواند، محیط زیرساخت فعلی را تحلیل می‌کند و کار را به نود یا نودهای مناسب می‌سپارد.

 
زمان‌بند (Scheduler)، مسئول دنبال کردن ظرفیت‌های موجود در هر میزبان است تا مطمئن شود بار کاری در زمان خود، از منابع زیادی استفاده نمی‌کند. زمان‌بند باید مجموع ظرفیت‌ها و همچنین منابع تخصیص داده‌شده به هر سرور را بداند. 

#### اجزای Node :

#### Container Runtime:


این اولین قسمتی است که هر گره باید آن را داشته باشد. به‌طورمعمول، این نیاز با نصب داکر برطرف می‌شود، اما جایگزین‌هایی مانند rkt و run نیز وجود دارند. مجری کانتینر مسئول شروع و مدیریت کانتینر است. هر واحد کاری در کلاستر در سطح پایه قرار دارد و به‌عنوان یک یا چند کانتینر پیاده‌سازی شده که باید توسعه پیدا کند. مجری کانتینر در هر گره بخشی است که در نهایت کانتینرها را با توجه به تعریف‌های قبلی، اجرا می‌کند.

#### kubelet:

نقطه ارتباطی هر گره با گروه کلاستر از طریق یک سرویس کوچک به نام Kubelet انجام می‌شود. این سرویس وظیفه انتقال اطلاعات به سرویس صفحه کنترلی را برعهده دارد و همچنین با مخزن etcd در تعامل است تا پیکربندی‌ها را بخواند و valueهای جدید بنویسد. Kubelet با اجزای ارشد ارتباط برقرار می‌کند تا در کلاستر به رسمیت شناخته شود و دستورات را دریافت کند. همچنین مجری کانتینر را کنترل می‌کند تا کانتینر اجرا یا در صورت نیاز از بین برود.



#### kube-proxy:
 برای مدیریت این‌که سرویس‌ها باید برای اجزای دیگر موجود باشند، یک سرویس پروکسی به نام Kube Proxy در هر سرور گره اجرا می‌شود. این پردازش، درخواست‌ها را به کانتینر درست ارسال می‌کند، می‌تواند تعادل بار برقرار کند و مطمئن شود که محیط شبکه‌ای قابل پیش‌بینی و ‌دسترسی است.



## نحوه‌‌ی راه‌اندازی یک برنامه با kubernetes

در این قسمت با توضیحاتی که از بخش قبل خواندیم، یک برنامه ساده وب به زبان go را با کمک kubernetes اجرا می‌کنیم. 
#### نصب ابزارهای لازم :



#### Kubctel:
 یک رابط command line براي اجراي دستورات است که در خوشه هاي Kubernetes پردازش می شود. با استفاده از kubectl می توانید برنامه ها را deploy کنید ، منابع خوشه را بررسی و مدیریت کنید ، log مربوط را مشاهده کنید و غیره.
1. دانلود آخرین ورژن با دستور:
<div dir="ltr">

```
 curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/
￼       kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
 
```
</div>

(براي نصب یک ورژن خاص عبارت داخل پرانتز را ورژن مورد نظر جایگذاري کنید.)


2. تبدیل به فایل قابل اجرا:
<div dir="ltr">

```

chmod +x ./kubectl

```

</div>

3.قرار دادن در PATH:

<div dir="ltr">

```

￼￼sudo mv ./kubectl /usr/local/bin/kubectl
```

</div>

4.  چاپ ورژن:
در این مرحله مطمئن میشوید که فایل نصب شده‌است.

<div dir="ltr">

```

￼￼kubectl version --client
```

</div>




#### Minikube:
محیط خوشه فیزیکی Kubernetes را در محیط شما ایجاد و پیاده سازي می کند.



1. به روزرسانی و آپدیت سیستم :


<div dir="ltr">

```

￼￼kubectl version --client
```

</div>


2.بررسی پشتیابی لینوکس فعلی از مجازي سازي :

<div dir="ltr">

```

￼￼kubectl version --client
```

</div>


3. نصب virtual box hypervisor:

<div dir="ltr">

```

￼￼kubectl version --client
```

</div>

4. نصب minikube


<div dir="ltr">

```

 wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
</div>

<div dir="ltr">

```
￼cp minikube-linux-amd64 /usr/local/bin/minikube
```
</div>

<div dir="ltr">

```
chmod 755 /usr/local/bin/minikube
```
</div>

5. بررسی ورژن:
<div dir="ltr">

```
￼minikube version
```

</div>


### ساخت cluster :


اکنون میتوانیم با دستور minikube start و minikube status یک cluster بر روي ماشین مجازي بسازیم:
<div dir="ltr">

```
minikube start
```

</div>

خروجی این دستور به این شکل خواهد بود:


![enter image description here](https://s17.picofile.com/file/8417725592/minikube.png)






<div dir="ltr">

```
minikube status
```

</div>

خروجی:


<div dir="ltr">

```
host: Running
kubelet: Running
apiserver: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100
```

</div>

با دستور زیر اطلاعات خوشه را می توان دید:


<div dir="ltr">

```
kubectl cluster-info
```

</div>

خروجی:
<div dir="ltr">

```
Kubernetes master is running at https://192.168.99.100:8443
KubeDNS is running at https://192.168.99.100:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
```

</div>



همانطور که در بالا می بینیم ، ما با cluster خود ارتباط داریم و همچنین می توانیم اجزاي Kubernetes را به همراه سرور API نصب کنیم. همچنین می توانید با دستورminikube ssh به ماشین مجازي minikube متصل شوید تا ببینید
چه فرآیندهایی در گره اجرا می شوند.


اکنون می توانیم لیستی از گره هاي موجود را در خوشه بررسی کنیم:



<div dir="ltr">

```
￼kubectl get nodes
```

</div>

خروجی:
<div dir="ltr">

```
minikube   Ready    master   3m41s   v1.19.4
```

</div>


می توان این node را براي مدیریت بهتر label بزنیم :







<div dir="ltr">

```
kubectl label nodes minikube type=backend
```

</div>

خروجی:

<div dir="ltr">

```
NAME     STATUS ROLES  AGE   VERSION  LABELS
minikube Ready  master 6m36s v1.14.3
beta.kubernetes.io/arch=amd64,beta.kubernetes.io/os=linux,kubernetes.io/arch=amd64,kubernetes.io/hostname=minikube,kubernetes.io/os=linux,node-role.kubernetes.io/master=,type=backend
```

</div>


اکنون cluster ما آماده‌ی دیپلوی کردن برنامه است. برنامه به زبان go است و روی پورت 3000 اجرا میشود. برای اینکه برنامه در cluster اجرا شود باید آن را در یک container جمع کنید. سپس یک docker image از container ساخته و برای Docker registr ارسال کنید.
پس از آن شما باید تعیین کنید که کدام image بر روی گره‌ی kubernetes نصب شود.

برای مثال dokerfile ما برای پروژه go به شکل زیر خواهد بود:



<div dir="ltr">

```
## We specify the base image we need for our ## go application
FROM golang:1.12.0-alpine3.9
## We create an /app directory within our
## image that will hold our application source ## files
RUN mkdir /app
## We copy everything in the root directory ## into our /app directory
ADD . /app
## We specify that we now wish to execute ## any further commands inside our /app ## directory
WORKDIR /app
## we run go build to compile the binary ## executable of our Go program
RUN go build -o server .
## Our start command which kicks off ## our newly created binary executable CMD ["/app/server"]
```

</div>


 پس از نصب داکر با دستور ساده اي از داکر dockerfile را build میکنیم:


<div dir="ltr">

```
 build -t hw1-go-app .
 ```

</div>

میتوان با دستور docker images لیست image هاي ساخته شده را دید:



<div dir="ltr">

```
docker images
```

</div>


خروجی:

<div dir="ltr">

```
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
hw1-go-app   latest    c2ecf2881703   43 hours ago   355MB
```

</div>

در خط اول image ما دیده می شود. بنابراین اگر دستور docker run را بر روي پورتی که سرور go ران میشود را اجرا کنیم ( پورت 3000 ) سرور مان فعال می شود:





<div dir="ltr">

```
docker run -p 3000:3000 -it hw1-go-app
```

</div>


خروجی:

<div dir="ltr">

```
Starting server at port 3000
....
```

</div>


هم چنین می توانید لیست container هایی که در بک گراند اجرا میشوند را ببینید :





<div dir="ltr">

```
Docker ps -a
```

</div>




## : ایجاد Deployment Controller

در این مرحله باید یک Deployment Controller ساخته شود. وقتی Deployment Controller ساخته شود در kubernetes اربابان ) masters ( اطلاعاتی شامل اینکه کدام گره باید pod یا گروهی از pod ها را بسازد ارسال می کند. )در بخش قبل گفتیم که podها بیانگر اتصال یک یا چند container در یک گره هستند( .
 
Deployment Controller ها در kubernetes از دو راه زیر ایجاد میشوند:

-  دستور kubectl run 
نوشتن YAML فایل ( این روش توصیه می شود)

ما از روش دوم استفاده می‌کنیم:



ابتدا برای سرور go یک فایل deployment ایجاد میکنیم: 


<div dir="ltr">

 ```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hw1-go-deployment
  labels:
    app: hw1-go-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hw1-go-app
  template:
    metadata:
      labels:
        app: hw1-go-app
    spec:
      nodeSelector:
        type: backend
      containers:
        - name: hw1-go-app
          image: hw1-go-app:v.01
          ports:
            - containerPort: 3000
```
</div>



توضیحاتی در مورد فایل :
خط اول ورژن kubernetes را نشان می دهد.

-Kind بیانگر نوع object است (pod, deployment , …) 

-بخش template که تمام دستوراتی که در pod اجرا میشود را نشان میدهد.

-بخش spec که حاوی اطلاعات دقیق از pod هاست مانند اسم container است.


سپس با کمک دستور  kubectl create ،  Deployment Controller را می سازیم:







<div dir="ltr">

```
 kubectl create -f hw1-go-deployment.yaml
```

</div>

خروجی:


<div dir="ltr">

```
deployment.apps/hw1-go-deployment.yaml created
```

</div>






اکنون با کمک دستور kubectl get pods میتوانیم pod ای که ساختیم را مشاهده کنیم:

<div dir="ltr">

```
kubectl get pods
```

</div>



خروجی:

<div dir="ltr">

```
NAME                                  READY   STATUS         RESTARTS   AGE
hw1-go-deployment-586ff56c7f-m7vzs    1/1     ErrImagePull        0          42m
```

</div>


می بینیم که pod ما ساخته شده است 
اما اگر این دستور را سه بار دیگر اجرا کنیم می بینیم که وضعیت (status) این pod به حالتهای ImagePullBackOff تغییر میکند که علت آن این است که pod نمی تواند image را دانلود کند برای همین باید image را برای ماشین مجازی که minikube از آن استفاده میکند  available کنیم. 





برای انتقال Docker  به محتوای minikube دستور زیر را در CL وارد می کنیم:


<div dir="ltr">

```
eval $(minikube docker-env)
```

</div>

سپس image را build می کنیم:



<div dir="ltr">

```
 docker build -f Dockerfile -t hw1-go-app:v.01 .
```

</div>


 اگر دوباره وضعیت pod را بررسی کنیم می بینیم که به حالت running تغییر پیدا کرده است:



<div dir="ltr">

```
NAME                                  READY   STATUS         RESTARTS   AGE
hw1-go-deployment-586ff56c7f-m7vzs    1/1     Running        0          42m
```

</div>






در نهایت می بینیم که pod ما کار می کند پس می توانیم چک کنیم که سرور مان پاسخ می‌دهد یا خیر. با اجرای دستور زیر که شماره port آن همان port ای ست که در فایل deployment بود و و از pod name ( در شکل قبل) استفاده کردیم:


<div dir="ltr">

```
kubectl port-forward hw1-go-deployment-8fb7b586f-npq97 3000:3000
```

</div>


خروجی:

<div dir="ltr">

```
Starting server at port 3000
....
```

</div>

سرور مان اکنون در پورت 3000 قابل دسترسی است.


نکته :
 برای غیر فعال کردن Minikube Docker host دستور زیرا را در shell فعلی وارد کنید:
 
  

<div dir="ltr">

```
eval $(minikube docker-env -u)

```

</div>
</div>
