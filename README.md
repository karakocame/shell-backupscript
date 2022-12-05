function menu(){
	clear
	echo "|----------------------------------------------|"
	echo "| Haupmenu:                                    |"
	echo "|                                              |"
	echo "|      Backup erstellen       B                |"
	echo "|      Inhalt eines Backups   L                |"
	echo "|      Backup zurück spielen  R                |"
	echo "|      Backup löschen         D                |"
	echo "|      Programm beenden       X                |"
	echo "|                                              |"
	read -p "| Eingabe: " EINGABE
}


function compress(){
	clear
	echo "|----------------------------------------------|"
	echo "| Kompressionsmethode:                         |"
	echo "|                                              |"
	echo "|      ZIP                    z                |"
	echo "|      BZIP2                  j                |"
	echo "|      XZ                     J                |"
	echo "|                                              |"
	read -p "| Eingabe:" COMPRESS
}

function wheretwoBackup(){
	clear
	echo "|----------------------------------------------|"
	echo "| Wo soll das Backup gespeichert werden        |"
	echo "|                                              |"
	read -p "| Eingabe" WHERETWOBACKUP
}

function whattwoBackup(){
	clear
	echo "|----------------------------------------------|"
	echo "| Wohin soll das Backup gespeichert werden     |"
	echo "|                                              |"
	read -p "| Eingabe: " WHATTWOBACKUP
}

function backup(){
	YESNO=0
	until [ $YESNO = 1 ]
	do
		compress
		echo "|Sind Sie sicher das Sie die Option ${COMPRESS}         |"
		echo "|benutzen wollen ?                            |"
		read -p "| (0: nein | 1: ja) " YESNO
	done
	wheretwoBackup
	whattwoBackup
	echo "tar cfz $WHERETWOBACKUP $WHATTWOBACKUP"
	sleep 5
}

function unbackup(){
	
echo "UNBACKUP"
}

function listbackup(){
	echo "LISTBACKUP"
}

function deletebackup(){
	echo "DELETEBACKUP"
}

while :
do
	menu
	case $EINGABE in
		b|B)
			backup
			;;
		r|R)
			unbackup
			;;
		l|L)
			listbackup
			;;
		d|D)
			deletebackup
			;;
		*)
			echo "Auf Wiedersehen"
			exit 1
	esac
	sleep 2
done

exit 0
