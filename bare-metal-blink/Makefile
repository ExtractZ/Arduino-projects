MCU    = atmega328p
F_CPU  = 16000000UL
PORT   = /dev/cu.usbmodem11301

CFLAGS = -mmcu=$(MCU) -DF_CPU=$(F_CPU) -Os -Wall -std=gnu99

main.elf: main.c
	avr-gcc $(CFLAGS) -o $@ $<

main.hex: main.elf
	avr-objcopy -O ihex -R .eeprom $< $@

flash: main.hex
	avrdude -p m328p -c arduino -P $(PORT) -b 115200 -U flash:w:$<

clean:
	rm -f *.elf *.hex