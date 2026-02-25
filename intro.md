## generative modeling

i modelli generativi non imparano direttamente la distribuzione dei dati (immagini/testo) da generare

piuttosto imparano una funzione che mappa una distribuzione nota (gaussiana) nella distribuzione dei dati da generare

- ha senso, le NN sono strumenti deterministici, non possono realizzare un sampling stocastico direttamente
  - se ad una rete do lo stesso input, mi esce sempre fuori lo stesso output
- faccio il sampling dalla distribuzione nota (latent space) con un PRNG, e vedo cosa mi esce applicando il learned mapping

Interessante anche il concetto di encoding e di embedding

- cio che recupero dalla distribuzione nota, è un vettore di dimensioni piccole (da 64 a 1024 elementi tipicamente)
- parto da uno spazio con una dimensionalità comunque alta (latent space)
- i vettori di questo spazio codificano e comprimono l'informazione del dato da generare
- vettori simili (vicini) nel latent space, producono risultati simili
- la rete quando impara il mapping associa a dati simili embedding simili nel latent space

**NB**: in generale, making an embedding means making an encoding = latent representation of the information you're working with

- it's natural that through learning the model maps similar information to similar embeddings
- it's the simplest possible solution of the problem you're trying to solve

Interessante anche il concetto di traiettoria e interpolazione nel latent space

- dati due punti nel latent space, il mapping mi produce, ad esempio, due immagini di gatti diversi
- se considero tutti i punti in mezzo, il mapping mi produce una smooth transition da un'immagine all'altra
- se consideriamo adesso una caratteristica dei gatti come il colore del pelo
  - io basta che esplori direzioni nel latent space fino a che non trovo quella che mi cambia il colore del pelo
