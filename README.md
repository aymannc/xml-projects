# xml-projects

### 1-Quelle est la riviere la plus longue au monde?
```
concat(/mondial/river[length = max(/mondial/river/length) ] /name,' ' ,max(/mondial/river/length))
```
### 2-par quels pays passe t-il (riviere)
```
//country[@car_code=/mondial/river[length = max(/mondial/river/length) ] /located/@country]/name
```
### 3-Quels sont les pays limitroplus de l'allemange
```
/mondial/country[@car_code=(//country[name="Germany"]/border/@country)]/name
```
### 4-Quelle est la superficie de la Turquie en Europe
```
(/mondial/country[@car_code='TR']/encompassed[@continent="europe"]/@percentage) * 0.01* (/mondial/country[name='Turkey']/@area)
```
### 5-Combien de juifs en Afrique
```
sum(
for $x in //country[encompassed[@continent='africa'] and religion="Jewish"]
return  $x/religion[child::text()='Jewish']/@percentage *0.01* $x/population[last()] 
)
```
### 6-Quels sont les pays qui bordent l'ocean atlantique
```
//country[@car_code=(//sea[name="Atlantic Ocean"]/located/@country)]/name
```
### 7-Quelle est la superficies totale du globale?
```
sum(//sea/area)+sum(//continent/area)
```
### (ratio mer/terre)
```
sum(//continent/area) div (sum(//sea/area)+sum(//continent/area)) 
sum(//sea/area) div (sum(//sea/area)+sum(//continent/area))
```
### 8-Quel est le plus grand lac au monde
```
concat(//lake[area=max(//lake/area)]/name, ' ' ,max(//lake/area))
```

