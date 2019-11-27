	   ___ _     _                 __    __  ___     ___ _       _            
	  / __\ |__ (_)_ __   ___     / /   /__\/   \   / __\ |_   _| |_ ___ _ __ 
	 / /  | '_ \| | '_ \ / _ \   / /   /_\ / /\ /  / _\ | | | | | __/ _ \ '__|
	/ /___| | | | | |_) | (_) | / /___//__/ /_//  / /   | | |_| | ||  __/ |   
	\____/|_| |_|_| .__/ \___/  \____/\__/___,'   \/    |_|\__,_|\__\___|_|   
	              |_|                 reverse engineerte Anleitung by benks v1.0
              
Auch im Netz gefundene Namen "Chippo LED" "Chipo LED Wash" "Litecraft LED Chipo RGB" "Litecraft Chipo LED 49x 1W/3W LED"
 
 

# Inhalt
	1) Wie dieses Manual zu lesen ist
	2) Syntax diese Manuals
	3) Aufbau des Menüs
	4) HowTo's


# 1) Wie dieses Manual zu lesen ist
Der Fluter hat 3 Tasten und ein Display
	links (enter)
	mitte (down)
	rechts (up)

## Skizze:
	  ___________________                                                                        
	 /                   \
	|   o o o o o o o o   |
	|  o o o o o o o o o  |
	|   o o o o o o o o   |
	|  o o o o o o o o o  |
	|   o o o o o o o o   |
	 \___________________/
	 _||_______||_______||_
	|                      |
	|      ( Hello )       |
	| o Enter o Down o Up  |
	|______________________|
	

Der Chipo LED-Fluter hat ein Baum-Menü in dem man mit den drei Tasten navigiert und Einstellungen verändert. Es wird immer ein Menüpunkt bzw. ein Wert im Display angezeigt.
Nach dem Anschalten befindet man sich im Stammmenü "Hello".
Wie das Menü aufgebaut ist und mit welchen Tasten man sich in dem Menü bewegt und Werte verändert ist unten unter 3) systematisch aufgeschrieben.
Wie die zu lesen ist und welche Taste bei welchem Zeichen zu drücken ist, kommt jetzt:

# 2) Syntax dieses Manuals

	wOrT 			steht für einen Menüpunkt z.B. "Hello", "PGset" oder "boost"
	. 				steht für einen Menüpunkt in Kurzschreibweise
	...				steht für mehrere Menüpunkte
	|				Trenner zwischen einzelnen Menüpunkten
	.|.|. 			Mehrere einzelne Menüpunkte zwischen denen mit "up" und "down" gewählt werden kann
	1|...|255		steht für eine Range von möglichen Werten von 1 bis 255
	:				steht für Enter kurz gedrück um den aktuell angezeigten Menüpunkt zu öffnen
	::				steht für Enter lang gedrück um den aktuell angezeigten Menüpunkt zu öffnen (Sicherheitsmodus)
	<				steht für Enter kurz gedrückt für zurück (raus aus Menü)
	<<				steht für Enter lang gedrückt für zurück (raus aus Menü) (Sicherheitsmodus)
	:(.|.|.<)		Untermenü, das mit : (Enter kurz gedrückt) geöffnet und mit < (Enter lang gedrückt) geschlossen wird
	::(.|.|.<<)		Untermenü, das mit : geöffnet und mit << geschlossen wird
	>				steht für Enter kurz gedrückt zum Speichern und Weiter im Menü
	(...>)(B)		Wert speichern und weiter zum Menüpunkt B z.B. beim Einstellen von Datum und Uhrzeiten
	???				Steht für eine Erklärung eines Menüpunkts in diesem Howto, der bisher unklar ist


# 3) Aufbau des Menüs 
  	Hello								Stammmenü
	| AVxxx:(A001|...|A412)<<			???
	| balanc::							Systemweite Helligkeit für die drei Farben (überschreibt Werte des Programms)
		(								Wenn der fluter vorher per Laptop (DMX) gesteuert wurde, sind die werte 	wahrscheinlich alle auf 0 und das programm bleibt unsichtbar
	 	Rblnc:(0|...|255<)				Helligkeit für rot
		|Gblnc:(0|...|255<)				Helligkeit für grün
		|Bblnc:(0|...|255<)				Helligkeit für blau
		|enable:(on|off<)
		<<)
	| boost:(on|off<)					???
	| R_H:(000|???<)					???
	| G_H:(000|???<)					???
	| B_H:(000|???<)					???
	| L_H:(000|???<)					???
	| Signal:(RS232|dmx<)				???
	| bright:(0|...|255<)				Displayhelligkeit einstellen
	| DSPFli:(Oben|Kopfüber<)			Display flippen falls Fluter Kopfüber betrieben. (Tastenbelegung ändert sich 	dadurch nicht)
	| DmxDL:(0|...998|unl<)				???
	| time::							Datum Uhrzeit Wochentag einstellen
		(
	 	YEAR:(2005|...|2099<)			Jahr
		|M/D:((0|..|12>(1|..|31<)		Monat und Tag einstellen
		|H:M:((0|...|24>)(0|...|59<)	Stunden und Minuten einstellen
		<<)
	| Fact :(oFF|Set<)					???
	| Prev								???
	| test::							Funktionen des Fluters durchtesten
		(
	 	red:(<)							rote LED
		|green:(<)						grüne LED
		|blue:(<)						blaue LED
		|ctc:(<)						???
		|all:(<)						alles testen
		|shutt:(<)						shutter testen
		|dimer:(<)						dimmer testen
		<) 	
	| tempe:(000°C|032°F<)				???
	| mastr:(oFF|oN<)					Master an/aus (Wenn das Gerät nicht tut was man will, auf off und 	wieder on setzen!)
	| slavID:(0|...|29<)				Slave ID Setzen
	| sched.:(oFF|oN<)					Schedule an/aus
	| PGrun:(off|1|...|5<)				Wählen welches Program sofort und nach Neustart ablaufen soll
	| PGset::							Die 5 Programme einrichten
		(
	  	ProG.:(1|...|5<)				Das zu programmierende Program auswählen und in den folgenden 	Menüpunkten einstellen
		| Scene:(0|...|10<)				Die Szene des eben gewählten Programms auswählen und in den folgenden 	Menüpunkten einstellen
		| Fixt.:(all|odd|even|master|Slv001|...|Slv29<)	???
		| Shutt:(000|...|255<)			Stroboskopgeschwindigkeit (Dauer, dass lampe aus ist)
											000...003=immer aus
											004...006 immer an
											007 stroboskop ab etwa 007
		| Dimer:(0|...|255<)			Alle drei Farben Dimmen (von 0 dunkel bis 255 hell)
		| R=255:(0|...|255<)			Intensität Rot
		| G=176:(0|...|255<)			Intensität Grün
		| B=124:(0|...|255<)			Intensität Blau
		| MAC:(0|...|255<)				Wechsel zwischen den Farben in unterschiedlichen Geschwindigkeiten und 	Random, was bei einer passiert ist irgendwie nicht reproduzierbar
										000...007 	passiert nix
										008		langsamer farbwechsel maximal 2 farben an 	r>r+g>g>g+b>b>b+r...
										009		in etwa langsam 3 farben 	r>rg>rgb>bg>rgb>rb>rbg>r>rg>g>gb>rgb>rb>rgb>rb>...
										bei höheren schnellerer wechsel
										es wird scheinbar erst umgeschaltet wenn der 
										blauf zu ende ist als z.B. 009 komplett durchgelaufen ist
		| tm_H:(00|...|23<)				Dauer der Szene incl. fade: Stunden
		| tm_m:(00|...|59<)				Dauer der Szene incl. fade: Minuten
		| tm_S:(00|...|59<)				Dauer der Szene incl. fade: Sekunden
		| Fd_H:(00|...|59<)				Dauer des Fade-In: Stunden
		| Fd_m:(00|...|59<)				Dauer des Fade-In: Minuten
		| Fd_S:(00|...|59<)				Dauer des Fade-In: Sekunden
		| SCrun*:(oFF|on<)				Szene im Ablauf des Programmes der Szene abspielen (on) oder auslassen 	(off) (Hier alle nicht verwendeten Szenen auf off setzen!)
		<<)
	| SchEDl*:							36 programmierbare Events programmieren, die zu bestimmter 	Uhrzeit/Wochentag ein Programm starten und beenden
		(
	  	event:(1|...|36)				Event wählen, das in den Folgenden Menüpunkten eingestellt wird
	 	|Prog.:(0|...|5<)				Programm wählen, das gestartet wird
	 	|day:(mon|tue|wed|thu|fri|sat|sun|all<)	Wochentag wählen
	 	|start:((00|...|24>)(00|..|59<)	Startuhrzeit 
	 	|end:((00|...|24>)(00|..|59<)	Enduhrzeit
	 	|enable:(oFF|on<)				Event aktivieren/deaktivieren
	 	<)
	| [UHRZEIT]							Uhrzeit wird angezeigt
	
	

# 4) Howtos

## Farb-Verlauf programmieren und starten ohne angeschlossenem Rechner/DMX
Man kann fünf verschiedene Programme (z.B. ein Farbverlauf von Grün zu Rot zu Blau und wieder zu grün usw.) programmieren, die abgespielt werden können.
Ein Programm setzt sich aus einzelnen "Szenen" (scenes) zusammen, die nacheinander für eine bestimme Dauer und einer bestimmten Übergangsdauer in Endlosschleife abgespielt werden, wenn sie gestartet werden.
Eine Szene definiert die Intensität der drei Farben die Dauer, die Fade-Dauer und mehr Eigenschaften (z.B. Blinkgeschwindigkeit)

	Vorher:
		Falls der Fluter zuvor per DMX betrieben wurde, sind die Farben wahrscheinlich runtergeregelt (alles auf 000) und das Gerät auf "slave" gestellt. Daher:
		* unter "balanc" Grundhelligkeit des Geräts der drei Farben hochstellen auf 255
		* und unter "mastr" Master auf "on" setzen

	Programmieren:
		* im Menü PGset unter
		* Prog: eines der fünf Programme auswählen, das nun programmiert (und damit überschrieben) wird
		* Scen - erste szene wählen
		* Dimmung, Farben, etc. Dauer (incl. Fade-In) und Fade-In-Dauer einstellen
		* Szene unter SCrun (scene run) mit "on" aktivieren
		* Scen - zweite Szene Wählen, einstellen, aktivieren usw.
		* alle nicht benötigten scenes unter SCrun auf "off" schalten
		* menü verlassen
	
	Starten:
		* PGrun im Hauptmenü öffnen
		* unter "scene" die eben programmierte Szene wählen
		* Fertig
		
		Wenn nach dem Abschalten/Steckerziehen wieder neu Strom fließt, startet das gewählte Programm automatisch

## Zeitprogrammierung
	Mit SchEDL man kann 36 Events anlegen Wochentage, Uhrzeiten etc, welches der 5 Programme starten soll. Events kann man aus und anschalten
	Schedule kann unter "sched" auch insgesamt ab- und angeschaltet werden.
	Uhrzeit und Datum muss gesetzt sein.
	Trotz einschalten und setzen der Uhrzeit wurden die Events nicht gestartet. Es muss noch irgendwo ein Menüpunkt geben der scheduling ermöglicht.
