# opo
ioidef on_button_pressed_a():
    wuKong.stop_all_motor()
    wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 110)
    wuKong.stop_all_motor()
    basic.pause(100)
    wuKong.stop_all_motor()
    basic.show_leds("""
        . . . . .
                # # . # #
                . . . . .
                . # . # .
                . . # . .
    """)
    wuKong.stop_all_motor()
    music.play_melody("B A G F E D C C5 ", 130)
    wuKong.stop_all_motor()
    music.play_melody("C D E F G A B C ", 130)
    wuKong.stop_all_motor()
    wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 80)
input.on_button_pressed(Button.A, on_button_pressed_a)

def on_sound_loud():
    if input.sound_level() == 190:
        wuKong.set_all_motor(200, -200)
        basic.pause(500)
        wuKong.set_all_motor(-200, 200)
        basic.pause(500)
        wuKong.stop_all_motor()
        soundExpression.sad.play()
        basic.show_leds("""
            . # . # .
                        # . . . #
                        . . . . .
                        . # . . #
                        . . . . .
        """)
input.on_sound(DetectedSound.LOUD, on_sound_loud)

def on_button_pressed_b():
    global حركلت
    حركلت = randint(1, 5)
input.on_button_pressed(Button.B, on_button_pressed_b)

def on_logo_pressed():
    pass
input.on_logo_event(TouchButtonEvent.PRESSED, on_logo_pressed)

يمين_او_شمال = 0
حركلت = 0
wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 80)
soundExpression.twinkle.play()
حركلت = 0
basic.show_leds("""
    . . . . .
        # # . # #
        # # . # #
        . . . . .
        . . . . .
""")
wuKong.set_all_motor(100, -100)
basic.pause(1000)
wuKong.set_all_motor(-100, 100)
basic.pause(2000)
wuKong.set_all_motor(100, -100)
basic.pause(1000)
wuKong.stop_all_motor()

def on_forever():
    global يمين_او_شمال
    if يمين_او_شمال == 1:
        wuKong.set_all_motor(50, -50)
        basic.pause(500)
        wuKong.set_all_motor(-50, -50)
        basic.pause(1000)
        wuKong.stop_all_motor()
        يمين_او_شمال = 0
    if يمين_او_شمال == 2:
        wuKong.set_all_motor(-50, 50)
        basic.pause(500)
        wuKong.set_all_motor(-50, -50)
        basic.pause(1000)
        wuKong.stop_all_motor()
        يمين_او_شمال += 1
basic.forever(on_forever)

def on_forever2():
    global حركلت
    if 1 == حركلت:
        wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 50)
        soundExpression.sad.play()
        wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 80)
        حركلت = 0
    if 2 == حركلت:
        wuKong.set_all_motor(100, -100)
        basic.pause(500)
        wuKong.set_all_motor(-100, 100)
        basic.pause(500)
        wuKong.set_all_motor(-100, 100)
        basic.pause(500)
        wuKong.set_all_motor(100, -100)
        basic.pause(500)
        wuKong.stop_all_motor()
        حركلت = 0
    if 3 == حركلت:
        basic.clear_screen()
        music.play_melody("F C5 F A G E G D ", 120)
        basic.show_leds("""
            . # . # .
                        # # . # #
                        . . . . .
                        . . . . .
                        . . . . .
        """)
        wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 128)
        basic.pause(500)
        wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 80)
        حركلت = 0
    if 4 == حركلت:
        soundExpression.mysterious.play_until_done()
        wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 128)
        basic.pause(500)
        wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 80)
        حركلت = 0
    if 5 == حركلت:
        soundExpression.giggle.play_until_done()
        wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 128)
        basic.pause(500)
        wuKong.set_servo_angle(wuKong.ServoTypeList._180, wuKong.ServoList.S0, 80)
        حركلت = 0
basic.forever(on_forever2)

def on_forever3():
    global يمين_او_شمال
    basic.show_leds("""
        . . . . .
                # # . # #
                # # . # #
                . . . . .
                . . . . .
    """)
    basic.pause(5000)
    basic.show_leds("""
        . . . . .
                . . . . .
                # # . # #
                . . . . .
                . . . . .
    """)
    basic.pause(50)
    basic.show_leds("""
        . . . . .
                . . . . .
                . . . . .
                # # . # #
                . . . . .
    """)
    basic.pause(5000)
    يمين_او_شمال = randint(1, 2)
basic.forever(on_forever3)
