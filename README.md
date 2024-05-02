# Kamailio



## Mục lục

1.  [Install Kamailio](https://git.k8s.vn/dhieu23nd/kamailio/-/blob/main/setup.md)
2.  [Config Log](https://git.k8s.vn/dhieu23nd/kamailio/-/blob/main/config_log.md)
3. [Kamailio](https://git.k8s.vn/dhieu23nd/kamailio/-/blob/main/README.md#Kamailio)
4. [Wiki](https://git.k8s.vn/dhieu23nd/kamailio/-/blob/main/README.md#Wiki)
5. [kamailio.cfg](https://git.k8s.vn/dhieu23nd/kamailio/-/blob/main/kamailio.cfg)
6. [Load Balancer](https://git.k8s.vn/dhieu23nd/kamailio/-/blob/main/README.md#LOAD-BANLANCER)

### Wiki

- [ ] [Core Cookbook](https://www.kamailio.org/wikidocs/cookbooks/5.7.x/core/#request_route)
- [ ] [Kamailio Modules](https://www.kamailio.org/docs/modules/stable/)
- [ ] [Kamailio Database tables](https://kamailio.org/docs/db-tables/kamailio-db-5.7.x.html)
- [ ] [RTP PROXY](https://computingforgeeks.com/how-to-install-rtpproxy-from-source-on-ubuntu-linux/)
- [ ] [RTP ENGINE](https://gist.github.com/altanai/61b2b0cf430aa817a5d78d93bd2c3842)
- [ ] [LOAD BALANCE](http://www.kamailio.org/events/2013-KamailioWorld/23-Daniel-Constantin.Mierla-Load-Balancing-Load-Balancers.pdf)
- [] [Intergration with Asterisk](https://www.kamailio.org/wiki/tutorials/asterisk/kamailio-4.0.x-asterisk-11.0.0-astdb)

### Kamailio

- Là một máy chủ SIP (Session Initiation Protocol) mã nguồn mở và mạnh mẽ. Nó được phát triển để xây dựng và quản lý các ứng dụng truyền thông IP như các dịch vụ VoIP (Voice over IP), video chat và truyền thông thời gian thực khác.
- Nó có thể là: 
  - SIP proxy server
  - SIP registrar server
  - SIP location server
  - SIP application server
  - SIP dispatcher server
  - SIP Websocket server
- Ưu điểm:
  - Khả năng mở rộng
  - Định tuyến linh hoạt
  - Bảo mật
  - Tương thích cao
  - Linh hoạt, khả năng tùy biến cao
- Cấu hình trong file kamailio.cfg
- Sử dụng MariaDB hoặc MySQL làm backend(default)
### LOAD BALANCER

- Các địa chỉ định tuyến được lưu trong file [dispatcher.list](https://github.com/HieuAnh87/kamailio/blob/master/dispatcher.list)
- Chỉnh sửa trong file cấu hình [kamailio.cfg](https://github.com/HieuAnh87/kamailio/-/blob/main/kamailio.cfg) (path: /etc/kamailio/kamailio.cfg)
- Config giống như [file mẫu](https://github.com/HieuAnh87/kamailio/-/blob/main/kamailio.cfg#L1190)