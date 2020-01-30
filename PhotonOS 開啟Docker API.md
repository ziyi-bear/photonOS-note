# PhotonOS 開啟Docker API

## 連線到PhotonOS客戶端
預設帳號root 密碼changeme 進去會強制修改
## 修改Docker設定檔案
> cd /usr/lib/systemd/system  
> nano docker.service  
## 設定檔案內有一行更改為
> ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock -H > tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock
## 套用Docker服務設定
> systemctl daemon-reload  
## 啟動Docker服務
> systemctl enable docker  
> systemctl start docker  

# 使防火牆設定在重啟後依然存活
> iptables -A INPUT -p tcp --dport 2375 -j ACCEPT  
> iptables -A INPUT -p tcp --dport 2376 -j ACCEPT  
> iptables-save > /etc/systemd/scripts/ip4save  
> systemctl restart iptables  

參考來源：https://github.com/vmware/photon/issues/691
