---
cards-deck: CSS::02IntroCrypto
---


### Ziele der Kryptographie# #card 
- **Vertraulichkeit**: Angreifer kann Inhalt der Nachricht **nicht** lernen
- **Integrität**: Angreifer kann Nachricht **nicht** ändern, ohne das Änderung erkannt wird
- **Authentizität**: Angreifer kann **nicht** behaupten, dass eine Nachricht von Alice kam, die diese nicht gesendet hat
^1730202050451

###  Wesentlicher Baustein Schlüssel: #card 
- **Kurzer** **Schlüssel**: Kryptoverfahren verwenden zufälligen Schlüssel
- **Symmetrische Kryptographie**: Gleicher Schlüssel zum Ver- und Entschlüsseln
- **Asymmetrische** **Kryptografie**:
	- Öffentlicher Schlüssel: z.B. veröffentlicht im Internet
	- Gehimer Schlüssel: Nur einzelnen Nutzern eines Kryptoverfahren bekannt
^1730202050466


### Kerckhoff #card 
- Ein Kryptoverfahren soll sicher bleiben, selbst wenn der Angreifer den Kryptoalgorithmus kennt. Alles öffentlich außer Schlüssel **k**, der zufällig gewählt wurde.
^1730202050475

### Verschlüsselung #card 
![[Pasted image 20241029121933.png]]
^1730202050484

### Kryptographische Annahmen #card 
- Kryptoverfahren nutzen Annahmen, auf denen Sicherheit basiert wäre **Annahme faslch**, wäre Verfahren **nicht mehr sicher**
- ![[Pasted image 20241029122746.png]]
^1730202050495

### Kryptographische Primitive: #card 
- **Definition:** Abstrakte, fundamentale Funktion mit spezifischen Kryptographischen Eigenschaften
- **Beispiele:** Blockschriften, Hash Funktionen, digitale Signaturen, etc
^1730202050504

### Kryptographische Konstruktion #card 
- **Definition:**  Beschreibt, wie kryptographische Primitive instanziiert werden
- **Beispiele**: AES, SHA-"%& 
^1730202050513
