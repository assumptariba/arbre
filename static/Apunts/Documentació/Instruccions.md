# Persones

## Creació d'una persona
- Les notes es poden crear de moltes maneres. És important que sigui quin sigui el mètode assegurar-se que la nota està dins de la carpeta `/Persones` o el sistema no funcionarà.
- El nom de la nota ha der ser el nom complert de la persona. Per ex: `Assumpta Riba Samarra`

#### Utilització de la plantilla
Cada persona necessita d'una metadata (explicat a continuació). Per facilitar l'insersió d'aquesta hi ha una plantilla ("template" en anglés) que facilita la seva creació. La plantilla també insedeix el codi que permet visualitzar tots els events relacionats amb aquesta persona.

Per inserir la plantilla:
1. Pulsar `Ctrl + P`
2. Buscar "Insert template"
3. Seleccionar `Persona`


## Metadata
Cada nota d'una persona conté una metadata que facilita la visualització de detalls importants a la vegada que s'utilitza per a poder autogenerar el llistat d'Events o l'[[Arbre geneològic]]

La metadata és representada de la següent manera:

`Nom`:: [[Assumpta Riba Samarra]]
`Neixament`:: 1954-05-15
`Mort`:: - 
`Pare`::  [[Josep Maria Riba Codina]]
`Mare`:: [[Virgínia Samarra Ripoll]]
`Fills`:: [[Xavier Vives Riba]], [[Èlia Vives Riba]], [[Iria Vives Riba]]

Són importants les següents consideracions per assegurar-se que el sistema funcioni.
- Utilitzar `::` per separar la propietat del valor
- Utilitzar els `wiklinks` per els noms. És a dir enllaçar utilitizant la sintaxi: "[[Nom de la persona]]"
- Per les dates utilitzar el format `ANY-MES-DIA`
- Separar els `Fills` amb una `,`


## Arbre geneològic

L'[[Arbre geneològic]] es genera automàticament.
Analitza la metadata de cada `Persona`

Per fer-ho s'utilitza els camps de `Pare`, `Mare` únicament.
Els  camp de `Fills` és ignorat ja que per generar les conexió necessaries  hauria de saber els progenitors  de cada fill i pot ser que no coïncideixin amb al cònjugue. És més fàcil que per cada fill es busqui el `Pare` i la `Mare`

- Si una Persona no apareix a l'arbre, assegura't que la nota existeix, està dins de la carpeta `/Persones`i  conté la metadata de `Pare` i `Mare`
