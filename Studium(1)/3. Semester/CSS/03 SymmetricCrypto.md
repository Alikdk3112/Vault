
#### Symmetrisch Kryptographie: #card 
- Es gibt nur **einen** Schlüssel für alle Algorithmen

#### Funktionale Definition #card 
- Beschreibt Input/Output-Verhalten der Algorithmen
- **Algorithmen** (Gen,Enc,Dec)
- ![[Pasted image 20241029124832.png]]
- **Korrektheit** :![[Pasted image 20241029125054.png]]
- **Effizienz:** Verschlüsselung und Entschlüsselung sind effizient (>1GB/s )

#### Sicherheitsspiel (IND-CPA) #card 
- Sicherheit = **Spiel** zwischen **Angreifer** und **Challenger**
- Schützt gegen Angreifer, die nur Zugang zu **Verschlüsselungen** haben, aber in der Praxis haben Angreifer oft mehr Möglichkeiten
- ![[Pasted image 20241029125912.png]]

#### Was bedeutet "Effizient" #card 
- *Effizient*, wenn Laufzeit **Polynomiell** 
- *Nicht* *Effizient*, wenn Laufzeit **Exponentiell**

#### Chosen Ciphertext Angriff  (IND-CCA-Sicherheit) #card 
- Angreifer hat auch Zugang zu **Entschlüsselung** von (bestimmten) Chiffretexten
- wie IND-CPA, Angreifer kann aber Orakel Chiffretext sende, dieser kann alle Chiffretexte entschlüsseln außer c*
- **Sicherheit:** **IND-CCA** sicher, falls alle **effizienten** Angreifer des Sicherheitsspiel maximal mit Wahrscheinlichkeit ca 1/2 ist.

#### One-Time-Pad #card 
- ![[Pasted image 20241029143934.png]]
- Unsicher bei Wiederverwendung des gleichen Schlüssels

#### Nachteile One-Time-Pad #card 
- ![[Pasted image 20241029144812.png]]

#### Blockchiffren #card 
- ![[Pasted image 20241029144958.png]]
