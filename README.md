# linux-command
Общая информация о памяти
<code>
df -h
</code>
Место, которое занимают все файлы в директории
<code>
du -sh /tmp
</code>
Посмотреть иноды
<code>
df -i
</code>
==== Состояние жёстких дисков ====
SMART информация о диске
<code>
smartlctl -a /dev/sda
</code>
Информация о софтовом рейд-массиве
<code>
cat /proc/mdstat
</code>
===== Нагрузка на диски, память и процессор =====

Общая информация о том, сколько данных пишется на диск и читается в реальном времени
<code>
iostat
</code>
Информация о том, какие процессы пишут на диск или читают с него
<code>
iotop
</code>

===== Процессор =====

Мониторинги в консоли
<code>
top, htop, btop
</code>

===== Память =====

Информация об ОЗУ
<code>
vmstat, free -m
</code>

Наиболее подробно об ОЗУ
<code>
cat /proc/meminfo
</code>
===== Процессы =====

Вывод всех процессов, запущенных на сервере
<code>
ps aux
</code>
Если в системе systemd, можно использовать
<code>
systemctl status %servicename%
</code>
Подробная информация о процессах
<code>
strace ls
</code>
Информация о конкретном процессе
<code>
strace -p <pid>
</code>
===== Сеть =====

Процессы, которые слушают какие-то сетевые порты на сервере
<code>
netstat -tulpn
</code>
Аналог
<code>
ss -lntu
</code>
==== Сетевые интерфейсы ====

Информация о сетевых интерфейсах
<code>
ip a
</code>
<code>
ifconfig
</code>

Информация о сетевых маршрутах
<code>
netstat -rn
</code>
<code>
ip -r
</code>

Проверка доступности удалённых хостов
<code>
ping 8.8.8.8
</code>

Путь пакета от вашего сервера до промежуточного. Все промежуточные маршрутизаторы.
<code>
traceroute 8.8.8.8
</code>

Трассировка в <<живом>> режиме
<code>
mtr 8.8.8.8
</code>

Различные запросы DNS-серверам.
<code> dig etogeek.dev or dig @8.8.8.8 etogeek.dev (dig <@dns-server dns-name>)</code>
<code>dig -t <record-type> <dns-name></code>
<code>dig -t mx etogeek.dev</code>
<code>nslookup</code>

Запросы к различным эндпоинтам.

<code>curl -Lv etogeek.dev</code>

Проверка доступности удалённого порта
<code>curl -v telnet://127.0.0.1:22</code>

Запрос напрямую к unix-socket
<code>curl --unix-socket /var/run/docker.sock http://images/json</code>

Показывает пакеты, которые бегают через определённые сетевые интерфейсы
<code>tcpdump -i any port 9100 -nn</code>

===== Логи =====

Директория логов /var/log

Проверка логов файла с обновлением в реальном времени, где видно последние 50 строк.
<code>tail -f -n50 /var/log/syslog</code>

Логи попыток входа на сервер или выполнение команд с помощью привилегий.
<code>ls -lah /var/log/auth.log</code>

Сообщения от ядра системы.
<code>ls -lah /var/log/kern.log</code>
<code>dmesg -T</code>

Systemd
<code>journalctl</code>
<code>journalctl -xeu nginx</code>
