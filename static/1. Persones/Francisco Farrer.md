`Nom`:: [[Francisco Farrer]] 
`Naixement`:: 00/00/1790*
`Mort`::  00/00/0000
`Cònjuge`:: [[Úrsula Vilalta]]
`Pare`::  [[Francisco Farrer*]]
`Mare`::  [[Raimunda Simó]]
`Fills`::  [[Magdalena Farrer Vilalta]] i Rosa, Francisco, Francisca, Josep, Maria i Jaume Farrer Vilalta
  
Magdalena Farrer és la mare de [[Rosa Borrull Farrer]]

- Font 1: Família Farrer Vilalta
- Font 2: arxiuenlinia.ahat/Fons documental/7.67 Gratallops/7.67.1 Parroquial/7.67.1.2.5. Compliments paquals/"Llibreta de combregants de la present parròquia de Gratallops en lo any 1825" 1825-1826 (Pàgina 17 document digitalitzat)
  

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