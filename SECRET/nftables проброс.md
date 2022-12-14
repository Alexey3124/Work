# Проброс портов
+ Заходим в конфигурационный файл /etc/nftables.conf
+ Дальше в самом низу файла прописываем следующее:

      table inet nat {

            chain prerouting {

                  type nat hook prerouting priority -100;

                  ip addr <внешний ip адрес> <tcp/udp> dport <внешний порт> dnat to <адрес сервера>:<порт сервера>

            }

            chain postrouting {
 
                  type nat hook postrouting priority 100;
  
                  ip daddr <адрес сервера> masquerade

            }

      }
