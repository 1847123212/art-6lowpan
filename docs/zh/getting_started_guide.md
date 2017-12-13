# ART-6LoWPAN ����ָ��

---

## 1����ʶӲ��

[![board_pin](https://raw.githubusercontent.com/ART-6LoWPAN/art-6lowpan/master/docs/zh/images/board_pin.jpg)](https://github.com/ART-6LoWPAN/art-6lowpan)

### 1.1 ����ӿ�

#### 1.1.1 ��Դ�� USB

���������ͨ�� Micro-USB �� **5V** ��Դ���硣ʹ�� Micro-USB �ӵ�����ʱ�������������һ�����ڡ����Ӹô��ں󣬿���ͨ�� shell �����й��߽��н�����Ҳ���Բ鿴ʵʱ����־��Ϣ��

> �����Ҫ�� STM32 �� USB ֱ����������ӣ����Խ����� `R8` �� `R9` �Ƴ����� `R10` �� `R7` λ�ú��� 0 ŷķ���輴�ɡ�

#### 1.1.2 ����

- RESET��Ӳ����λ����
- KEY���û��Զ��尴�������磺�� `RAW_RADIO_TEST` ����ģʽ�£����´˰��������Զ�������Ƶ���ݣ�

#### 1.1.3 ���Խӿ�

STM32 �� SWD �ĵ��Խӿ�λ����ͼ���½ǣ���Ҫ�������ʱ����������������Ӽ��ɡ�

#### 1.1.4 ͨ�Žӿ�

|�ӿ�|����|��ע|
|:-:|:-:|:-:|
|I2C|1·||
|USART|2·||
|CAN|1·||
|SPI|1·||

#### 1.1.5 �����ӿ�

- AD ���� 2·
- ��ͨ IO 2·

### 1.2 ָʾ��

- POWER����Դָʾ��
- LED1���û��Զ���ָʾ��1���̼�����Ϊϵͳ����ָʾ��ʹ��
- LED2���û��Զ���ָʾ��2������ `SI446X_TRANS_LED_ENABLE` �󣬽���Ϊ��Ƶ���� **����** ָʾ��
- LED3���û��Զ���ָʾ��3������ `SI446X_TRANS_LED_ENABLE` �󣬽���Ϊ��Ƶ���� **����** ָʾ��

## 2���̼�����

### 2.1 Eclipse + GCC

�������Ϥ Eclipse + GCC ����������

### 2.2 Eclipse + IAR

�� `firmware/app/eclipse/iar` �µ� `.cproject` �������滻�� `firmware/app` �������������ط����� Eclipse + GCC һ�¡�

### 2.3 IAR & Keil

#### 2.3.1 ׼�� RT-Thread �� ENV ����

**ENV** �� RT-Thread �ṩһ�����á���������Ŀ�Ĺ��ߣ����Ĺ��ܷǳ�ǿ�������˽���鿴 [�ٷ�˵���ĵ�](https://www.rt-thread.org/document/site/zh/5chapters/01-chapter_env_manual/)����������ֻ���������� IDE ���̵����ɡ�

[��������̵�ַ](https://pan.baidu.com/s/1qX8R2nq#list/path=%2FART-6LoWPAN%2Ftools&parentPath=%2F) ������ `env_released_0.x.x.zip` ��Ȼ���ѹ����

#### 2.3.2 ���� IAR/Keil ����

�����Լ�ϵͳ�����(32bit or 64bit)����� `console_64.exe` �� `console_32.exe` ��ע�⣺ĳЩɱ����������󱨣����Ի�������μ��ɣ����ٽ��뵽 ART-6LoWPAN �Ĺ̼�Դ���Ŀ¼������ͼ

![enter_source_root](https://raw.githubusercontent.com/ART-6LoWPAN/art-6lowpan/master/docs/zh/images/env_enter_source_code_root_folder.png)

�������Ҫ���ɵĹ���Ϊ IAR����ʱ��Ҫ���޸�Դ���Ŀ¼�£� `rtconfig.py` �ļ������ģ�`EXEC_PATH` ��Ӧ�� IAR ��ʵ�ʰ�װ·����Keil Ҳ��ͬ�����޸���ɺ󱣴档

��ʱ�� ENV �����У������Լ�ʵ�ʵ� IDE��ѡ���������������е�һ���������룬������������Ҫ�� IDE ���̡�

```
scons --target=iar
scons --target=keil5
```

���ɺ�Ĺ����ļ���Ϊ `project.*` ��˫���򿪺󣬼���ִ�й̼����롣

## 3���̼�����

### 3.1 IAP ����

������������Ѿ����� bootloader ���� app ����ô����ͨ�� IAP ��ʽ��������������

- �����������������
- �� SecureCRT ���� XShell ������� YModem ���ܵ��ն˹���
- ���� `update` ���bootloader �к� app �о����ԣ�
- ��ʾ��Ҫ���� `Y` ����ȷ��
- ͨ�� YModem ���ʹ����µ� app �̼�
- �˺󣬿����彫���Զ���ɸ���

![iap](https://raw.githubusercontent.com/ART-6LoWPAN/art-6lowpan/master/docs/zh/images/iap.gif)

### 3.2 J-link �ű�һ������

һ�����ؽű�λ�� [tools/download_bin](https://github.com/ART-6LoWPAN/art-6lowpan/tree/master/tools/download_bin) ��

- ��������� SWD �ӿ��� J-Link ����
- �����ļ����� `readme.txt`  ��Ҫ���޸Ĵ�����Ӧ�ù̼���Ϊ `application.bin` 
- ˫�� `������д.bat` ���������д

���ַ�ʽ���㣬�ٶ�Ҳ�죬���ֻ����Ƽ�ʹ�� IAP ��ʽ���ء�

### 3.3 ʹ�� IDE �Դ���������

Eclipse + GCC ���� ����Ϥ Eclipse + GCC �����������ĵ���IAR �� Keil ���ೣ�� IDE ���ﲻ�ٽ��ܡ�

## 4���������⼰�������

- 1��ͨ�� J-Link ���ع̼�������ʾʧ�ܣ���Ƶģ���ڽ���Ƶ�������ݷ���ʱ�����ʵ���Ƶ�źſ��ܻ���ŵ������ߡ����¸�λ��������֤��Ƶģ�鲻����ʱ�������ؼ��ɡ�
