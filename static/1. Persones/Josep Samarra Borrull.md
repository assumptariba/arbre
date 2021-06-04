`Nom`:: [[Josep Samarra Borrull]]
`Naixement`:: 14/06/1894
`Mort`:: 18/02/1969
`Cònjuge`::
`Pare`:: [[Josep Samarra Micola]]
`Mare`:: [[Rosa Borrull Farrer]]
`Fills`:: [[Fernando Samarra Rojals]]



```dataviewjs
//Codi per llistar tots els events on aquesta pàgina esta enllaçada

let pages = dv.pages('"Events"')


let filtered = pages.filter((page)=>{

	for(let o of page.file.outlinks)
	{
	 if (o.path == this.currentFilePath)
	 	return true
	}
	
	return false
})

let getFileName=(path)=>{
	return path.replace(/^.*[\\\/]/, '').split(".")[0]
}

for(let p of filtered)
{
	if(!p.Data){
		p.catDate="Data desconeguda"
		break
	}
	
	
	
	let date = new Date(p.Data.ts)
	
	if (isNaN(date.getTime()))
	{
		p.catDate="Data invalida"
		break
	}
	
	
	p.catDate=date.toLocaleString('ca-es', { dateStyle: 'long' });
}
	
if(filtered.length==0){
	dv.paragraph("No s'ha trobat cap `Event` que contingui referències a [["+getFileName(this.currentFilePath)+"]]. Un cop creats apareixieran aquí")
}
else{
	dv.table(["Data", "Event"], filtered
    .sort(b => b.Data)
    .map(b => [b.catDate,b.file.link]))
}


```
```