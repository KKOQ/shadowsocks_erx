# shadowsocks for EdgeRouter X

## ������ʾ
���°��ss-libevʹ��rc4-md5�ȼ���Э�����ʾû���㹻���������ɸ����������ֵ����������ʧ�ܣ��������޷�ʹ�������ؾɰ�: 

[ss-erx-v1.0.tar.gz](https://github.com/izerosoul/shadowsocks_erx/releases/download/v1.0/ss-erx-v1.0.tar.gz) 

���Ҫʹ�����°��֧�ֵ�chacha20-ietf-poly1305�ȼ���Э��Ϳ����������°�:

[ss-erx-v1.1.tar.gz](https://github.com/izerosoul/shadowsocks_erx/releases/download/v1.1/ss-erx-v1.1.tar.gz)

## ��װ
1. ����shadowsocks_erx-master.zip����ѹ
2. ��winscp�ѽ�ѹ�������ļ�copy��/tmpĿ¼
3. ����·��CLI������沢��½��Ȼ��ִ��: 
	> cd /tmp
	> sudo bash install.sh
4. ������ʾ����shadowsocks������Ϣ��һ��ֻ��Ҫ�����������ַ���˿ڡ����룬����ѡ�����ֱ�ӻس�ʹ��Ĭ��ѡ�

## ע��
* �����������Զ�������ͨ��ipset�Թ���IP���а�����������IP���ᷭǽ���ʣ�ֻ�й�����������shadowsocksͨ����ǽ
* ֻ�ܶ�TCP������ǽ
* ������վDNS��shadowsocks��������תʹ��TCP����8.8.8.8����ֹ��Ⱦ����������ʹ�ù���DNS����������Ӱ��CDN����
* 1080�˿ڿ�����Ϊsocks5��ǽ����ʹ��
* �ļ������/configĿ¼����Ϊ���Ŀ¼�������õ�ʱ��ᱻһ�𱸷ݣ�����ϵͳ����Ҳ����ɾ��
* shadowsocks-libev�汾:v3.1.0, chinadns�汾:v1.3.2(�޸İ�)��pdnsd�汾:v1.2.9
* EdgeRouter X EdgeOS v1.8.5,v1.9.0����ͨ��

* �������ͣshadowsocks������sudo /etc/init.d/shadowsocks stop

* ��������������sudo /etc/init.d/shadowsocks start

* ����sudo crontab -e�������ļ�ĩβ����������ݣ��Ϳ���ʵ��ÿ��5���Ӽ��ss״̬��������ܷ�ǽ���Զ���������

  > */5 * * * * sh /config/shadowsocks/bin/ss-monitor.sh 

### PT�����û���ע��

������ж��������ػ����������������ػ�����SS������������£�
ss�����ű�/etc/init.d/shadowsocks����������һ��:

> #BYPASS_RANGE=192.168.123.0/24 

ȥ��ע��(ɾ��#��)��������Ϳ�����Ч��Ȼ��192.168.123.0/24���������ζ�������ssͨ���ˣ�ͬʱҲ�޷���ǽ�ˣ�192.168.123.0/24Ҳ���Ի��ɵ���IP�����������Ρ�

## DNS��������
chinadns    ������������һ������DNS��һ������DNS 
dnsmasq  ->    chinadns    (����IP)->    pdnsd   -> ss-server -> dns-server:ok 

?			   			(����IP)->    114.114.114.114:ok 

chinadns���ߺܾ�û�и��¹��ˣ������м���bug���ᵼ����Щͬʱ�й��ڹ���CDN�����������������IP��������ʹ�õ�chinadns���޸������bug���Ż��˲�������µĽ����ٶȡ�
ss��ǽ����Ŀǰ�����׳�����ľ���DNS����Ⱦ������ļ��θ��¼����������DNS����Ŀǰ�汾�������ұȽ������ˡ�