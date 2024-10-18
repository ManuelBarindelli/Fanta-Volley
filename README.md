<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Partita tra Squadre</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .team {
            margin-bottom: 20px;
        }
        .team h3 {
            margin-bottom: 10px;
        }
        .team ul {
            list-style-type: none;
            padding: 0;
        }
        .team li {
            margin: 5px 0;
        }
        .result {
            font-weight: bold;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Partita tra Squadre</h1>

    <div class="team" id="teamA">
        <h3>Giocatori di Squadra A</h3>
        <ul id="teamAList"></ul>
    </div>

    <div class="team" id="teamB">
        <h3>Giocatori di Squadra B</h3>
        <ul id="teamBList"></ul>
    </div>

    <button onclick="giocaPartita()">Gioca Partita</button>

    <div class="result" id="result"></div>

    <script>
        const ruoli = ["Palleggiatore", "Centrale", "Schiacciatore", "Libero", "Opposto"];
        
        function creaGiocatori(squadra, numeroGiocatori) {
            const giocatori = [];
            for (let i = 1; i <= numeroGiocatori; i++) {
                const ruolo = ruoli[Math.floor(Math.random() * ruoli.length)];
                giocatori.push(`Giocatore ${squadra}${i} (${ruolo})`);
            }
            return giocatori;
        }

        function mostraGiocatori(idSquadra, giocatori) {
            const ul = document.getElementById(idSquadra);
            ul.innerHTML = '';
            giocatori.forEach(giocatore => {
                const li = document.createElement('li');
                li.textContent = giocatore;
                ul.appendChild(li);
            });
        }

        function giocaPartita() {
            const giocatoriA = creaGiocatori('A', 9);
            const giocatoriB = creaGiocatori('B', 8);

            mostraGiocatori('teamAList', giocatoriA);
            mostraGiocatori('teamBList', giocatoriB);

            // Calcola il punteggio: la squadra vincitrice ottiene sempre 25 punti
            let punteggioSquadraA, punteggioSquadraB;
            const punteggioPerdente = Math.floor(Math.random() * 25); // Punteggio casuale per la squadra perdente

            if (punteggioPerdente % 2 === 0) {
                punteggioSquadraA = 25;
                punteggioSquadraB = punteggioPerdente;
            } else {
                punteggioSquadraA = punteggioPerdente;
                punteggioSquadraB = 25;
            }

            let risultato = `Punteggio finale Squadra A: ${punteggioSquadraA}<br>`;
            risultato += `Punteggio finale Squadra B: ${punteggioSquadraB}<br>`;

            if (punteggioSquadraA > punteggioSquadraB) {
                risultato += "<br>Squadra A ha vinto!";
            } else if (punteggioSquadraA < punteggioSquadraB) {
                risultato += "<br>Squadra B ha vinto!";
            } else {
                risultato += "<br>La partita è finita in pareggio.";
            }

            document.getElementById('result').innerHTML = risultato;
        }
    </script>
</body>
</html>
