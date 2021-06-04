```dataviewjs

let pages = dv.pages('"1. Persones"')
let mermaid = ""

let addRow = (row)=>{
 mermaid = mermaid +  "\n" + row
}

let addRel = (from, to,type)=>{
	if(type=="unio")
		 mermaid = mermaid +  "\n" + from + " --- " + to
	else
		mermaid = mermaid +  "\n" + from + " --> " + to
}

let getNewNode=(name)=>{
	return {children:[]}

}

addRow("```mermaid")
addRow("graph LR;")

let nodes = []

let addNodeRel=(fromId, fromName, toId,toName, type)=>{

	if(!nodes[fromId])
		nodes[fromId]=getNewNode()
	if(!nodes[toId])
		nodes[toId]=getNewNode()
	
	if(!nodes[fromId].children.includes(toId))
		nodes[fromId].children.push(toId)
		
	if(!nodes[fromId].children.includes(toId))
		nodes[fromId].children.push(toId)
		
	if(!nodes[fromId].name)
		nodes[fromId].name = fromName
		
	if(!nodes[toId].name)
		nodes[toId].name = toName
		
	nodes[fromId].type = type
}

let normalize = (str)=>{
	return str.normalize("NFD").replace(/[\u0300-\u036f]/g, "").replace(/\s/g, '')
}

const unioName = "fa:fa-heart"

for(let p of pages)
{
	
	let nom = p.nom?p.nom.path:"Sense nom"
	
	let nomId = normalize(nom)
	console.log(nomId)
	if(nomId=="AssumptaRibaSamarra")
		console.log(p)
	let pare = p.pare?p.pare.path:"Desconegut"
	let pareId = normalize(pare)
	let mare = p.mare?p.mare.path:"Desconeguda"
	let mareId = normalize(mare)
	let unioId = pareId+mareId
	
	if(p.pare)
		addNodeRel(pareId,pare, unioId,unioName, "unio")
	if(p.mare)
		addNodeRel(mareId,mare, unioId,unioName, "unio")
	if(p.pare || p.mare)
		addNodeRel(unioId,unioName, nomId, nom)
}

for (let n in nodes){
	addRow(n+"("+nodes[n].name+")")
	addRow("class "+n+" internal-link;")
	
}

for (let n in nodes){
	for(let c of nodes[n].children){
		addRel(n,c,nodes[n].type)
	} 
}

addRow("```")
 
dv.paragraph(mermaid)
//console.log(mermaid)

```

