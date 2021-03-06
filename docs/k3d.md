# K3D Kurulumu

## K3S (Lightweight Kubernetes) 

K3S, 2019 yılında açık kaynak olarak rancher tarafından piyasaya sürüldü. K3S, 100mb’ın altında bir binary dosyası olarak tasarlanmıştır. Ayrıca sertifikalı bir Kubernetes aracıdır ve cross platform çalışabilme özelliğine sahiptir.
K3S hafifliği sayesinde çok düşük sistemlerde bile kubernetes cluster’ı kurabilmemize olanak sağlıyor. K3S önerilen sistem gereksinimleri aşagıdadır.;      
- Linux 3.10   
- 512 MB RAM (sunucu)   
- 75 MB RAM (node)    
- 200 MB disk alanı    

## Linux Kurulum:

### Gereksinimler:  

- Windows, Linux veya MacOS ortamı
- Docker
- Kubectl
- K3D

### 1.1 - Docker Kurulumu   
Docker kurulumunu hızlı bir şekilde yapmak için rancher tarafından hazırlanan script’i kullanabilirsiniz veya bu adresten docker kurulumunu uygun ortamınıza göre yapabilirsiniz.   
```bash
$ curl https://releases.rancher.com/install-docker/19.03.sh | sh
```

### 1.2 - Kubectl Kurulumu    
Kubernetes API ile haberleşmek için Kubectl kurmamız gerekiyor, bunuda aşağıdaki adımları takip ederek kolaylıkla yapabilirsiniz.
```bash
$ curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
```
```
$ chmod +x ./kubectl
```
```
$ sudo mv ./kubectl /usr/local/bin/kubectl
```

Tüm bu işlemlerden sonra aşağıdaki komut ile kubectl versiyon kontrolünü yapabilirsiniz.

```
kubectl version
```

### 1.3 - K3D Kurulumu

K3D kurulumu basit, yapmanız gereken terminale aşağıdaki komutu girmek.

```
$ wget -q -O - https://raw.githubusercontent.com/rancher/k3d/main/install.sh | bash
```
Kodunu girdikten sonra terminalden şu çıktıyı aldıysanız kurulumunuz başarılı olmuştur. 
```
k3d installed into /usr/local/bin/k3d
run 'k3d --help' to see what you can do with it
```
Versiyon kontrolü için bu komutu girin:
```
$ k3d --verison
```

## K3D Komutları


### Cluster Komutları:


### 'k3d cluster' komutu ile:
- 'k3d cluster create [cluster name]' ile yeni bir cluster oluşturulabilir.
- 'k3d cluster delete [cluster name]' ile cluster silebilirsiniz.    
  Cluster ismi yerine -a parametresi ile toplu seçim yapabilirsiniz.
- 'k3d cluster list' ile clusterlarınızı listeleyebilirsiniz.
- 'k3d cluster start [cluster name]' ile clusterlarınızı başlatabilirisniz. '-a' parametresi burada da geçerli.
- 'k3d cluster stop [cluster name]' ile clusterlarınızı durdurabilirsiniz. '-a' parametresi kullanımı geçerlidir.

### 'k3d node' komutu ile:
- 'k3d node create [node name]' ile node oluşturabilirsiniz.
- 'k3d node delete [node name]' ile node silebilirsiniz. '-a' parametresi geçerlidir.
- 'k3d node list' ile nodelarınızı listeleyebilirsiniz.
- 'k3d node start [node name]' ile nodelarınızı başlatabilirsiniz. '-a' parametresi geçerlidir.
- 'k3d node stop [node name]' ile nodelarınızı durdurabilirsiniz. '-a' parametresi geçerlidir.
