
---
To create service where it points to the created pods by deployment you just need to **--expose**

> kubectl expose deployment mydeployment --port=80
>
> kubect get services
>
> OR
>
> kubectl get svc
>
> kubectl describe service mydeployment  #service will show you pods created and attached with the service
>
<pre>
<img width="329" height="100" alt="image" src="https://github.com/user-attachments/assets/178be7ef-4779-4aa7-a89a-121a50b89e7e" />
<img width="629" height="300" alt="image" src="https://github.com/user-attachments/assets/d247a5da-c079-4524-9f64-ecce677472ec" />
</pre>

> curl 172.20.49.222:80
<img width="640" height="200" alt="image" src="https://github.com/user-attachments/assets/a762bea6-573b-40e0-9fbb-eebc49bbcb14" />
