`Nom`::  [[Úrsula Vilalta]]
`Naixement`::  00/00/0000
`Mort`::  00/00/0000
`Cònjuge`::
`Pare`::  
`Mare`::  
`Fills`:: [[Magdalena Farrer Vilalta]] 
  
De Gratallops. Mor entre 1831 i 1837. Esposa de Francisco Farrer de Gratallops. Font: bateig Rosa Farrer Vilalta

# Referències rellevants
# Anècdotes
# Altres dades
Ursula Vilalta, apareix documentada (arxiuenlinia.ahat) per primera vegada nl els Llibres Parroquials de Gratallops, en el Llibre de Compliment pasqual:

>  Matrícula dels combregants del 1924:
 >> En el domicili dels FArre del c/ Major hi viuen: Raymunda, vídua, Francisco i Ursula, cònjuges; i els seus fills, Jaume,  Rosa, Francisco i Francisco (p.17 digital)
 
> Matrícula dels combregants del 1925:
	>> En el domicili dels FErre del c/ Major hi viuen: Raymunda, vídua, Francisco i Ursula, cònjuges; i els seus fills, Jaume, Joseph, Rosa, Francisco i Francisca (p.18 digital)


> Matrícula de 1930:
>> En la matrícula de 1830 hi apareix , per primera vegada, amb nom i cognom: Úrsula Vilalta (també hi apareix per primera vegada, la seva filla Magdalena). Esposa de Francisco Farrer, domiciliats al c/ Major de Gratallops, on viuen amb els seus filla Francisco, Francisca, Magdalena i Rosa (p.8 digital)

> Matrícula de 1937:
	> > Ursula Vilalta ja és morta. Al domicili del c/ Major hi viuen: Francisco Farrer, vidu, i els seus fills Francisco, Magdalena, Maria, Jaume i Joseph (p.8 digital)

> Matrícula de 1939:
	> >  Al domicili dels Farrer del c/ Major hi viuen: Francisco Farrer, vidu, i els seus fills Francisco, Magdalena, Maria i Jaume (p.7 digital)

> Matrícula de 1853 


A PARTIR DEL 1853 HI HA UN SALT TEMPORAL FINS EL 1862

> Matrícula de 1862
> > Al domicili dels Farrer i Ros del c/Major hi viuen: Jaume (germà de Magdalena Farrer) i Teresa Ros, cònjuges i els seus fills Jaume, Joseph, Carme i Pere (p.14 digital)

# Dubtes/Hipòtesis
> Magdalena Farrer va néixer entre 1825 i 1830.
  

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