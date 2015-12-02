1. 소개
라즈베리 파이의 GPIO 커넥터를 통해 LED 장치를 제어 보쟈
2. 재료
라즈베리파이
저항
LED 녹색 (파랑색,빨강색,흰색) 전부가능
브레드보드
3.방법
1) LED를 켜보자

import RPi.GPIO as GPIO	//라즈베리파이의 GPIO 핀 제어를 위해 RPi.GPIO 모듈을 가져옴
GPIO.setmode(GPIO.BCM)	//라즈베리파이의 GPIO 핀 이름 부여 방식을 BCM 방식으로 설정
GPIO.setup(18, GPIO.OUT)//18번 핀을 out핀으로 설정
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

 sudo python led_blink.py를 사용하여 파일을 사용하면 점멸하는 LED를 볼 수 있다.

2) LED밝기를 조절해보자

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

 sudo python led_Brightness.py를 사용하여 파일을 사용하면 값을 0-100까지의 숫자를 입력하고 밝기 변화를 관찰할 수 있다.
