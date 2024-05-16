## Reflection On Hello Minikube

1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?

Ketika saya mencoba melakukan pengecekan *log* sebelum dan setelah ter*expose* sebagai *service* terdapat perbedaan pada isi log. Jika saya mengecek isi *log* sebelum ter*expose* maka isinya hanya log terkait started http dan udp server pada port 8080. Lalu ketika saya mengecek *log* setelah aplikasi ter*expose* maka terdapat berbagai history terkait http request get. Menurut saya, ini muncul ketika saya membuka aplikasi karena setiap saya melakukan *refresh* pada web ketika membuka aplikasi tersebut maka *log* terkait http request get nya bertambah. Berikut lampiran percobaannya: <br>

![before expose](before.png) <br>
![after expose](after.png) <br>
![after expose & refresh](refresheffect.png) <br>

2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created? <br>

Opsi `-n` pada perintah `kubectl` digunakan untuk menentukan namespace tertentu pada *cluster* Kubernetes. Pada Kubernetes, *namespace* digunakan untuk memisahkan objek dalam kluster agar sumber daya lebih terorganisir dan terisolasi. Jika menggunakan opsi `-n kube-system`, perintah kubectl get hanya akan menampilkan objek yang berada di dalam namespace kube-system. Alasan output tidak menampilkan pods/services secara eksplisit adalah sumber daya tersebut kemungkinan besar dibuat pada *namespace* lain. <br>

 

