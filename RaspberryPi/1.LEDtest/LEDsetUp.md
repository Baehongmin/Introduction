1. �Ұ�
����� ������ GPIO Ŀ���͸� ���� LED ��ġ�� ���� ����
2. ���
���������
����
LED ��� (�Ķ���,������,���) ���ΰ���
�극�庸��
3.���
1) LED�� �Ѻ���

import RPi.GPIO as GPIO	//����������� GPIO �� ��� ���� RPi.GPIO ����� ������
GPIO.setmode(GPIO.BCM)	//����������� GPIO �� �̸� �ο� ����� BCM ������� ����
GPIO.setup(18, GPIO.OUT)//18�� ���� out������ ����
GPIO.output(18, True)	//LED ON
GPIO.output(18, False)	//LED OFF

File: led_blink.py

import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BCM)
GPIO.setup(18, GPIO.OUT)

while (True):
        GPIO.output(18, True)
        time.sleep(0.5)
        GPIO.output(18, False)
        time.sleep(0.5)

 sudo python led_blink.py�� ����Ͽ� ������ ����ϸ� �����ϴ� LED�� �� �� �ִ�.

2) LED��⸦ �����غ���

 File: led_brightness.py

import RPi.GPIO as GPIO

led_pin = 18
GPIO.setmode(GPIO.BCM)
GPIO.setup(led_pin, GPIO.OUT)

pwm_led = GPIO.PWM(led_pin, 500)
pwm_led.start(100)

while True:
        duty_s = raw_input("Enter Brightness (0 to 100):")
        duty = int(duty_s)
        pwm_led.ChangeDutyCycle(duty)

 sudo python led_Brightness.py�� ����Ͽ� ������ ����ϸ� ���� 0-100������ ���ڸ� �Է��ϰ� ��� ��ȭ�� ������ �� �ִ�.
