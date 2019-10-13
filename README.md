# akasztofa

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).








Akasztófa
Készítette: Kocsor Levente Ferenc

A játék elérhető ezen a linken:

A forráskód pedig itt található:
Játékleírás:

A kitalálandó szót a szóban szereplő betűk számával megegyező számú és elrendezésű vízszintes vonal reprezentálja. A találgató játékos javasol egy betűt, mely ha szerepel a kitalálandó szóban, a betű helyének megfelelő vonalakra ráírásra kerül. Amennyiben a betű nem szerepel a kitalálandó szóban, úgy egy stilizált akasztófa egy része kerül lerajzolásra. 

A játék akkor ér véget, ha az akasztófa (és a benne lévő emberalak) teljes egészében megformálásra kerül, vagy kérdező az összes betűt kitalálja


Játékmenet:

A site megnyitásakor ez a felület jelenik meg, ahol lehetőségünk van a játék megkezdéséhez.

Az ezt követő felületen zajlik a tényleges játék, ahol a rendelkezésünkre álló betűk segítségével kell meghatározni a kirandomizált szavunkat.



A már használt betűk áthúzásra kerülnek a jobb követhetőség érdekében és a felhasználóbarátabb játékélményért.

Ha a rajz teljes mértékben kiteljesedik, az-az az embert „felakasztjuk” akkor a játék véget ért.

A játékban bármikor lehetőségünk van új kitalálandó szó kéréséhez az „Új Játék” opcióval, ahol egy véletlenszerű szó kerűl kiválasztásra a programunkban meghatározottakból
Program: 

A játék Vue.js használatával lett elkészítve, amely egy open-source JavaScript keretrendszer, tökéletes felhasználói felületek illetve egy oldalas alkalmazások elkészítésére.

A program célja a Vue környezet megismerése volt, valamint annak gyakorlása. A legtöbb idő a dolgok utánajárásával telt. Miután pár példaprogramot elkészítettem, egyszerűbb volt belefogni a tényleges beadandóba.

A legnehezebb a grafikus rész a megoldása volt, ami végül elég statikusra sikerült.
Adatbázis híján a kitalálandó szavak „bele lettek égetve” a programba.


Programmagyarázat:

A karakterünk ábrázolását statikusan meghatározott pontok segítségével ábrázoljuk:

A játszható betűk, valamint a szavak a program kódba vannak „beleégetve”, az alábbi módon: 


Nagyobb szabású játéknál célszerűbb kisebb, nem olyan komplex adatbázis segítségét használni, de itt nem éreztem szükségét, mivel a programcélja, a fejlesztőkörnyezet megismerése, gyakorlása volt.
Metódusok:

initialize() : Lényegében ez szolgál az új játék elkezdéséhez (előző játékmenet lenullázásához) és a véletlenűl választott szavunk beállításához.

GetVeletlenSzo(): A fent taglalt metódus hívja meg ezt. A programunkban meghatározott szavakból választ véletlenül, majd azzal tér vissza meghívásakor.


trybetu(betu): Ez a metódus egy betűt vár bemenetnek és eldönti, hogy az szerepel e a játékban kitalálandó szóban. Ez a „játékunk lelke”.
getStrikethroughClass(betu): A bemenetként kapott betűről eldönti,hogy volt e használva-e már. Ha igen, akkor arra ráilleszti a diagonal-strike stílust, az-az áthúzza a grafikus felületen.
