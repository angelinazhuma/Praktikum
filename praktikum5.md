## Praktikum 5
Selles praktikumis tutvustasin Linuxi võimalusterohket failide pääsuõiguste süsteemi. Tutvustasin rohem kasutajate õigustega ja nende turvalisusega.
# 5.1
a) lugemiseks on vaja 
Kataloogile /tmp/kaust: r-x 
Failile /tmp/kaust/minufail.txt: r--
b)kustutamiseks on vaja
Kataloogile /tmp/kaust: r-x 
Failile /tmp/kaust/minufail.txt: rw- 
# 5.2
Skriptifaili käivitamiseks on vaja lisaks käivitamisõigusele ka lugejaõigust (r), selleks et shell suudaks lugeda skripti.
# 5.3 
Igale olevatele gruppile saab esitatada vaikimisi õigusi, et igal kasutajal olid võrdsed õigused failidele, ka liigipääse kontroll ja rohkem turvalisust.
# 5.4
Ma ei tea miks ta ei pääse mind uusfail.txt teksti näha, tegin kõik mida saaksin, aga ikkagi ei saa vaadata, ei tea miks :(
<img width="743" alt="Screenshot 2023-10-25 223409" src="https://github.com/angelinazhuma/Praktikum/assets/145142791/d7978ad2-9cc9-46c2-ba00-7f7ce6eeeee4">
# 5.5
![image](https://github.com/angelinazhuma/Praktikum/assets/145142791/1cde7db8-9815-46a9-988c-f58f617bca46)
Setuid-õigus võimaldab programmil käivituda selle omaniku õigustes, mitte käivitaja omades. 
See on vajalik olukordades, kus kasutajatel on vaja teha teatud toiminguid, mis muidu nõuaksid kõrgemaid õigusi või parooli jagamist.
# 5.6
Jah, setuid kasutamine võib potentsiaalselt vähendada süsteemi turvalisust. 
Setuid on Linuxi omadus, mis võimaldab käivitataval failil käituda omaniku õigustes, mitte käivitaja omades.
# 5.7
Kustutada saavad Peeter ise, superkasutajad(root), ja kõik teised kasutajad, kellel on juurdepääs "/tmp/yhiskaust" kataloogile.
# 5.8
![image](https://github.com/angelinazhuma/Praktikum/assets/145142791/a30c6529-7d30-4ad4-ac6e-7fc0e0ae4b7a)
# 5.9
Mitte keegi ei saa chattr +i-parameetriga faili sisu modifitseerida, isegi omanik. sudo chattr -i testfail-2 ja rm testfail-2
