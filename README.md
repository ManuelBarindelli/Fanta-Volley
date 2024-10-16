import random

class Giocatore:
    def __init__(self, nome, ruolo):
        self.nome = nome
        self.ruolo = ruolo

    def __str__(self):
        return f"{self.nome} ({self.ruolo})"


class Squadra:
    def __init__(self, nome):
        self.nome = nome
        self.giocatori = []

    def aggiungi_giocatore(self, giocatore):
        self.giocatori.append(giocatore)

    def __str__(self):
        return f"{self.nome} - Giocatori: {', '.join([giocatore.nome for giocatore in self.giocatori])}"


class Partita:
    def __init__(self, squadra1, squadra2):
        self.squadra1 = squadra1
        self.squadra2 = squadra2

    def gioca_partita(self):
        # Visualizza i giocatori delle due squadre
        print(f"\nGiocatori di {self.squadra1.nome}:")
        for giocatore in self.squadra1.giocatori:
            print(giocatore)

        print(f"\nGiocatori di {self.squadra2.nome}:")
        for giocatore in self.squadra2.giocatori:
            print(giocatore)

        # Calcola punteggio casuale per ogni squadra
        punteggio_squadra1 = random.randint(0, 5)
        punteggio_squadra2 = random.randint(0, 5)

        print(f"\nPunteggio finale {self.squadra1.nome}: {punteggio_squadra1}")
        print(f"Punteggio finale {self.squadra2.nome}: {punteggio_squadra2}")

        # Determina il vincitore
        if punteggio_squadra1 > punteggio_squadra2:
            print(f"\n{self.squadra1.nome} ha vinto!")
        elif punteggio_squadra1 < punteggio_squadra2:
            print(f"\n{self.squadra2.nome} ha vinto!")
        else:
            print("\nLa partita è finita in pareggio.")


# Creazione delle squadre
squadra1 = Squadra("Squadra A")
squadra2 = Squadra("Squadra B")

# Aggiunta di 9 giocatori a Squadra A
for i in range(1, 10):
    squadra1.aggiungi_giocatore(Giocatore(f"Giocatore A{i}", "Giocatore"))

# Aggiunta di 8 giocatori a Squadra B
for i in range(1, 9):
    squadra2.aggiungi_giocatore(Giocatore(f"Giocatore B{i}", "Giocatore"))

# Creazione e gestione della partita
partita = Partita(squadra1, squadra2)
partita.gioca_partita()

