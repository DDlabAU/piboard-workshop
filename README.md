#Piboard Workshop i DD Lab
Denne side indeholder ressourcer til brug ved workshop om DD Labs Piboard, der indeholder en Raspberry Pi 2, model B og en Arduino Uno. 

Formålet er at blive bekendt med, hvordan Processing 3 installeres og fungerer sammen med Arduinoen. Piboardet vil i mange tilfælde kunne erstatte den bærbare computer, der bruges i jeres installationer.

**Vigtig info**

Der udvikles rigtig meget på Processing 3 til Raspberry Pi 2 for tiden, så disse informationer bliver muligvis hurtigt forældede og/eller der kommer samrtere måder at gøre det på. Brug derfor de links du finder på denne side, for at holde dig opdateret.

På ældre MacBook computere kan der være issues med at forberede et SD kort med den indbyggede kortlæser. Brug en ekstern kortlæser for at løse problemet.

Standard brugernavn på Raspberry Pi er 'pi' og standard kodeord er 'raspberry'

**De mest relevante links**
- [Processings hjemmeside](https://processing.org)
- [Arduinos hjemmeside](https://www.arduino.cc)
- [Processings Wiki om Processing på Raspberry Pi](https://github.com/processing/processing/wiki/Raspberry-Pi)
- [Hardware, Integration & Other Languages forummet på processing.org](https://forum.processing.org/two/categories/hardware-other-languages). Det er primært dette forum der bruges til at spørge/svare på spørgsmål om Raspberry Pi og Processing.

### Lav et SD-kort med styresystem + Processing 3 til Raspberry Pi 2

- Mulighed 1: Hent et Raspbian-image med Processing 3.0.1 pre-installeret.
- [Raspbian-image med Processing 3.0.1 pre-installeret](http://download.processing.org/processing-3.0.1-linux-raspbian.zip)

Dette er umiddelbart den letteste måde at få Processing til at køre på sin Raspberry Pi 2 og den vi anbefaler.

- Mulighed 2: Hent et Raspbian-image uden Processing (eller installér Processing på en Raspberry Pi du har arbejdet med i forvejen)

Følg vejledninegen for NOOBS eller RASPBIAN på [downloadsiden på raspberrypi.org](https://www.raspberrypi.org/downloads/). NOOBS er Raspberry Pi's 'lette' installer og RASPBIAN er et image.

Kør herefter

```curl https://processing.org/download/install-arm.sh | sudo sh```

fra et terminalvindue for at installere Processing, som beskrevet i [Wikien](https://github.com/processing/processing/wiki/Raspberry-Pi).

- Når du har downloadet dit image med eller uden Processing pre-installeret, så følger du vejledningen for dit styresystem [her](https://www.raspberrypi.org/documentation/installation/installing-images/README.md). Hvis du har valgt NOOBS er vejledningen [her](https://www.raspberrypi.org/documentation/installation/noobs.md).

### Første boot dansk tastatur, terminalvindue og filsystem
Når du har forberedt dit SD kort sætter du det i Raspberry Pi'en, tilslutter skærm, mus og tastatur, netværkskabel og derefter strøm, hvorefter computeren booter. Nu skal der laves diverse justeringer til styresystemet.
- Udvid filsystemet
- Sæt tastatur til dansk
	- Køre ```sudo raspi-config``` fra en kommandolinje
		- Vælg Internationalisation Options
		- Vælg Change Keyboard Layout
		- Vælg Generic 105-key (intl) PC
		- Set keyboard til Other —> Danish
		- Vælg Default for keyboard layout
		- Vælg No compose key
		- No (Control+alt+Backspace)
		- Finish
- Kør ```sudo reboot``` fra en kommandolinje

### Opdatering af Linux
Når computeren har genstartet skal Linux opdateret. Det gøres på følgende måde:
- Kør ```sudo apt-get update``` fra en kommandolinje
- Kør ```sudo apt-get upgrade``` fra en kommandolinje

### Test Processing
Nu er din Raspberry opdateret og det er tid til at teste at alt fungere indtil videre. Åbn Processing og åbn File -> Examples -> Image -> Transparency og kør det.

### Installering af Arduinomiljøet
- Kør ```sudo apt-get install arduino``` fra en kommandolinje
- Start Arduino-miljøet
- Test at Arduinomiljøet virker ved at uploade en sketch på normal vis

###Test forbindelsen mellem Processing og Arduino
- I Processing, åbn File -> Examples -> Libraries -> Serial -> SerialCallResponse eksemplet.
- Nederst i den sketch står Arduinokoden. Kopiér den over i en Arduino sketch og upload den.
- Lav kredsløb med følgende opsætning: To stk. 10k potmetre sat til 5V, hhv. A0 og A1, og ground (se det øverste billede [her](https://www.arduino.cc/en/Tutorial/Potentiometer)).
- Luk Arduinomiljøet og start sketchen i Processing. Du skulle nu kunne styre den lille bold
- Du skal muligvis resette Arduinoen med din Processing sketch åben for at få det til at fungere.