# Traefik

[traefik.io](https://doc.traefik.io/)

## 介紹

- 容易與docker/docker-swarm/k8s 直接整合的load banalcer
- 使用label方式, 動態掛載(新增或移除)其他服務的docker container


### 使用traefik的好處

- 可以自動發現服務(service discovery), 減少管理
- 整合letsencrypt, 可以快速申請ssl certificate

### traefik label


#### traefik provider

traefik定義好一套抽象的



### traefik怎麼透過label讓request可以被route到對應的服務

<img src="https://doc.traefik.io/traefik/assets/img/providers/docker.png" width="700" />

### traefik中的元件

#### router

#### orchestrator


## 參考資料

- [新一代LB - Traefik](https://peihsinsu.gitbooks.io/docker-note-book/content/xin-yi-dai-lb-traefik.html)
