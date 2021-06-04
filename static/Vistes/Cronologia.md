Llistat cronològic de tots els events
```dataviewjs
//Codi per llistar tots els events on aquesta pàgina esta enllaçada

let pages = dv.pages('"Events"')




for(let p of pages)
{
	if(!p.data){
		p.catDate="Data desconeguda"
		break
	}
	
	
	
	let date = new Date(p.data.ts)
	
	if (isNaN(date.getTime()))
	{
		p.catDate="Data invalida"
		break
	}
	
	
	p.catDate=date.toLocaleString('ca-es', { dateStyle: 'long' });
}
	

dv.table(["Data", "Event"], pages
    .sort(b => b.data)
    .map(b => [b.catDate,b.file.link]))

```