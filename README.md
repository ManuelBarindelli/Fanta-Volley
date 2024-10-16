import random

class Giocatore:
    def __init__(self, nome, ruolo):
        self.nome = nome
        self.ruolo = ruolo
        self.voto = 0  # Voto iniziale del giocatore

    def assegna_voto_automatico(self):
        # Assegna un voto casuale tra 5.0 e 8.0
        self.voto = round(random.uniform(5.0, 8.0), 1)


class Squadra:
    def __init__(self, nome):
        self.nome = nome
        self.giocatori = []

    def aggiungi_giocatore(self, giocatore):
        self.giocatori.append(giocatore)

    def calcola_punteggio(self):
        punteggio_totale = sum([giocatore.voto for giocatore in self.giocatori])
        return punteggio_totale

    def assegna_voti_giocatori(self):
        for giocatore in self.giocatori:
            giocatore.assegna_voto_automatico()


class Partita:
    def __init__(self, squadra1, squadra2):
        self.squadra1 = squadra1
        self.squadra2 = squadra2

    def gioca_partita(self):
        # Assegna voti automatici ai giocatori delle due squadre
        self.squadra1.assegna_voti_giocatori()
        self.squadra2.assegna_voti_giocatori()

        # Calcola i punteggi totali delle squadre
        punteggio_squadra1 = self.squadra1.calcola_punteggio()
        punteggio_squadra2 = self.squadra2.calcola_punteggio()

        print(f"Punteggio {self.squadra1.nome}: {punteggio_squadra1}")
        print(f"Punteggio {self.squadra2.nome}: {punteggio_squadra2}")

        # Determina il vincitore
        if punteggio_squadra1 > punteggio_squadra2:
            print(f"{self.squadra1.nome} ha vinto!")
        elif punteggio_squadra1 < punteggio_squadra2:
            print(f"{self.squadra2.nome} ha vinto!")
        else:
            print("La partita è finita in pareggio.")


# Creazione delle squadre
squadra1 = Squadra("Squadra A")
squadra2 = Squadra("Squadra B")

# Aggiunta di giocatori a Squadra A
squadra1.aggiungi_giocatore(Giocatore("Giocatore A1", "Attaccante"))
squadra1.aggiungi_giocatore(Giocatore("Giocatore A2", "Centrocampista"))
squadra1.aggiungi_giocatore(Giocatore("Giocatore A3", "Difensore"))

# Aggiunta di giocatori a Squadra B
squadra2.aggiungi_giocatore(Giocatore("Giocatore B1", "Attaccante"))
squadra2.aggiungi_giocatore(Giocatore("Giocatore B2", "Centrocampista"))
squadra2.aggiungi_giocatore(Giocatore("Giocatore B3", "Difensore"))

# Creazione e gestione della partita
partita = Partita(squadra1, squadra2)
partita.gioca_partita()
