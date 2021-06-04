`Nom`::  [[Carmen Ripoll Castellnou]]
`Naixement`::  21/09/1910
`Mort`:: 
`Cònjuge`:: soltera
`Pare`::   [[Josep Ripoll Cardona]]
`Mare`::   [[Virgínia Castellnou Figueres]]
`Fills`::  
  
El seu promès, de la lleva del biberó, va desaparèixer durant la guerra i ella sempre va somniar amb el seu retorn. Mor d'Alzheimer al Pere Mata de Reus, acompanyada de la seva neboda, la Montserrat Ripoll Mauri. La Carmen havia deixat la seva casa de Tivissa als nebots que, reunits a Torredembarra dp de la seva mort, decideixen q la casa ha de ser per a la Montserrat Ripoll.
  

```dataviewjs
//Codi per llistar tots els events on aquesta pàgina esta enllaçada

let pages = dv.pages('"Events"')

let createDate=(data)=>{
 let str = ""+data //otherwise does not cast to string
 let s = str.split("/")

 if(s.length!=3)
 {
  console.log("invalid date")
  return {year:0, month:0, day:0, sort:"0"}
 }
 
 let d=parseInt(s[0])
 let m=parseInt(s[1])
 let y=parseInt(s[2])
  
 
 let sort=s[2]+s[1]+s[0]
 console.log(sort)
 return {year:y, month:m, day:d, sort:sort} 
}
let printDate=(idate)=>{
 
 
 if(idate.day){
  let date = new Date(idate.year+"-"+idate.month+"-"+idate.day)
  return date.toLocaleString('ca-es', { dateStyle: 'long' })
 }
  
 if(idate.month){
  let date = new Date(idate.year+"-"+idate.month+"-01")
  return  date.toLocaleString('ca-es', { month: 'long', year: 'numeric' });
 }
  
 if(idate.year)
 {
  let date = new Date(idate.year+"-01-01")
  return  date.toLocaleString('ca-es', { year: 'numeric' });
 }
 
 return "Data invalida"
}


let filtered = pages.filter((page)=>{

 for(let o of page.file.outlinks)
 {
  if (o.path == this.currentFilePath)
   return true
 }
 
 return false
})

for(let p of filtered)
{
 p.idate = createDate(p.data)
}
 

dv.table(["Data", "Event"], filtered
    .sort(b => b.idate.sort)
    .map(b => [printDate(b.idate),b.file.link]))
```