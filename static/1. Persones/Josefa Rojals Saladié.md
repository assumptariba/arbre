 `Nom`::[[Josefa Rojals Saladié]]
`Naixement`::  00/00/1890
`Mort`::  00/00/1965
`Cònjuge`:: [[Josep Samarra Borrull]]
`Pare`::  [[Pedro Rojals Saladié]]
`Mare`::  [[Mariana Saladié Pagés]]
`Fills`::  [[Fernando Samarra Rojals]]
  
 # Referències rellevants
> Data naix. extreta del Padró de [[Tivissa]] de 1920
> Defunció (març 1965), dada extreta del nínxol 628 (sector B, fila 4) del cementiri de Tivissa.
# Anècdotes
> Li deien Pepa, dona de caràcter q gobernava marit i fill. No va deixat casar el seu fill Fernando amb la seva xicota.
Empadronada al [[LLocs/Mas Samarra]] fin el XXXX; a partir d'aquest any està empadronada al Carrer Muro 5; actual carrer Murada 7 (confirmat el canvi de numeració pel dr ACRE i tb pel padró de XXX)
  

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