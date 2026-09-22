# Adattatore locale Bambu Lab

L'adattatore locale Bambu consente a Converged di interagire con una stampante
Bambu Lab tramite la sua interfaccia di rete locale. Si connette all'endpoint
MQTT-over-TLS della stampante, esegue l'autenticazione con il codice di accesso
LAN e indirizza il dispositivo tramite il numero di serie. Il controllo della
stampa e la telemetria restano sulla rete locale; Bambu Cloud non fa parte di
questo percorso.

L'adattatore pubblica comandi per mettere in pausa, riprendere, arrestare, JSON
grezzo e G-code. Si sottoscrive ai report del dispositivo e inoltra tramite
callback lo stato più recente, le informazioni sulla stampante, gli errori e i
dati di telemetria della stampa. I chiamanti possono anche richiedere uno
snapshot JSON quando necessitano dello stato corrente in modo sincrono.

La connessione predefinita accetta il certificato autofirmato comunemente
presentato dalle stampanti in modalità LAN. L'API di connessione estesa accetta
un certificato CA quando è richiesta la verifica del certificato.
