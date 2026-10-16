# Kötelék – 2 fős coop (és 2v2 verseny) ügyességi játék a böngészőben

Két játékos, egy energiakötél. Ha túl messze kerültök egymástól, elszakad, és a pálya elölről indul.
48 pálya, 6 világ (kötelék → gépezet → veszély → fejtörő → kihívás → mesteri), kb. 2–3 óra két embernek. Minden pálya egy ötlet köré épül, és versenyre van tervezve – a tervet a `PALYATERV.md` írja le.
Világonként 8 élet van: ha elfogy, a világ elölről indul (a főmenüben kikapcsolható: „Végtelen élet”).

A játék egyetlen fájl (`index.html`) + a három zene (`zene_menu.mp3`, `zene_jatek.mp3`, `zene_verseny.mp3`), nem kell hozzá saját szerver: a két gép közvetlenül,
böngészőből kapcsolódik egymáshoz (WebRTC, PeerJS). GitHub Pages csak a fájlt szolgálja ki.

## Feltöltés GitHubra (kb. 3 perc)

1. GitHubon **New repository** → név pl. `kotelek` → Public → Create.
2. **Add file → Upload files** → húzd be az `index.html`-t és a három `zene_*.mp3` fájlt → Commit changes.
3. A repo **Settings → Pages** menüjében: *Source: Deploy from a branch*, *Branch: main* / *(root)* → Save.
4. 1–2 perc múlva él a játék itt: `https://<felhasználóneved>.github.io/kotelek/`
   (a Pages oldalon kiírja a pontos címet).

Ha később módosítod az `index.html`-t, csak töltsd fel újra ugyanoda. Ha a zenefájlok hiányoznak, a játék akkor is megy – ilyenkor a beépített, generált zene szól.

## Így játsszatok

### Ketten (páros játék)

1. Mindketten nyissátok meg a linket (asztali böngésző, Chrome/Edge/Firefox).
2. Az egyikőtök: **Szoba létrehozása** → kap egy 4 betűs kódot → elküldi a másiknak.
3. A másik: **Csatlakozás kóddal** → beírja → Mehet.
4. A szoba gazdája látja, hogy a társa csatlakozott, és elindítja (akár a pályaválasztóból is).

- A főmenüben adj meg egy nevet és válassz arcot – ezt látják a többiek a lobbyban és a figurád fölött.
- Mozgás: **WASD**, **nyilak** vagy **kontroller** (bal kar / D-pad; egy gépen az első kontroller a kék, a második a narancs; a Start gomb a szünet). **R**: pálya gyors újrakezdése (gazda). A főmenü ❓ Súgója minden pályaelemet elmagyaráz; az új elemek első találkozáskor a pályán is kapnak egy rövid tippet.
- **Esc** (a szoba gazdájánál): szünet, pálya újra, pálya átugrása, főmenü.
- A célmezőre **mindkettőtöknek** rá kell állnia, miután minden kristályt összeszedtetek.
- **A kötelet elvágja** a tüske, az őrjárat és a lézer – mindig ugyanazon az oldalon legyetek, és együtt menjetek át.
- A kötél nem húzza magával a másikat: aki lemarad, annál elszakad.
- Zene és hangeffektek a főmenüben (és a szünet menüben) külön hangerővel állíthatók vagy némíthatók – a beállítás megmarad a böngészőben. Három zene van: menü, páros játék, verseny/kupa – a játék magától vált köztük átúszással. A zene az első kattintás után indul (böngésző-szabály).
- A legjobb idők a gazda gépén mentődnek (böngésző tároló), a pályaválasztóban látszanak a csillagok.

### Heti kihívás

A főmenü **📅 Heti kihívás** sora: minden héten ugyanaz az 5 pálya mindenkinek (a hét sorszámából számolódik, szerver nélkül), egymás után, összidőre. Életek nincsenek, de minden újrakezdés számít. Egy gépen vagy szobából (ketten) indítható; a végén a 🟩🟨🟥 eredménysor egy gombbal másolható Discordra, a heti legjobb időtök a böngészőben megmarad.

### Négyen (2v2 verseny)

1. A gazda szobát nyit, a másik három ugyanazzal a kóddal csatlakozik.
2. A lobbyban mindenki látja a két csapatot, és a saját nevénél lévő gombbal átülhet a másikba (ha tele van, helyet cserél az ottanival). A gazda bárkit átültethet.
3. A gazda a szobában beállítja a verseny hosszát (5 / 10 / 20 / mind a 48 pálya) és a pálya-tiltást, majd indít. **Pálya-tiltás:** indítás után a két csapat felváltva kitilt 1–1 (vagy 2–2) pályát a készletből – bárki kattinthat a saját csapata nevében, 25 mp után véletlen pálya esik ki. A maradék pályákon megy a verseny.
4. Mindkét páros ugyanazt a pályát futja egyszerre, a saját példányán – az ellenfelet áttetsző szellemként látjátok.
   Aki előbb ér be (mindkét tag a célon, minden kristállyal), pontot kap. **Életek nincsenek**: ha elhaltok, csak ti kezditek elölről a pályát, az ellenfél közben halad.
5. A verseny végén az összesített pontszám dönt; az eredmény egy gombbal másolható Discordra.

### Kupa (Discord-bajnokság, 2 / 4 / 8 / 16 csapat)

A főmenü **🏆 Kupa** pontja a szervezőnek való:

1. Kiválasztod a csapatok számát (2, 4, 8 vagy 16 – alapból 8), beírod a kupa nevét és a csapatneveket (soronként egy; a sorrend adja a párokat, a 🎲 Sorsolás keveri) → **Kupa létrehozása**. Alapból: nyolcaddöntő 2, negyed- és elődöntő 3 nyert pályáig, a döntő 5-ig, van bronzmeccs, és minden körnek saját, nehezedő pályakészlete van (a tanulópályák nélkül) – a beosztás a `PALYATERV.md` végén. A ⚙ Beállításoknál körönként átállítható a nyert pályák száma és kattintgatva a pályakészlet, ki-/bekapcsolható a bronzmeccs, választható véletlen pályasorrend és a meccs előtti pálya-tiltás (nincs / 1–1 / 2–2) – később, a kupa nézetből is.
2. Egy meccsnél **▶ Indítás** → a játék szobát nyit a két csapat nevével, te **nézőként hostolsz** (nem játszol). A kódot kiteszed Discordra, a 4 játékos belép, mindenki a saját csapatát választja, te indítod a meccset. Játék közben alapból **osztott képernyőn** látod a két csapatot egymás mellett, felül az eredménnyel (ezt lehet Discordon streamelni); a **Tab** vált az osztott nézet és az egyes csapatok teljes nézete között.
3. A meccs végén az eredmény magától bekerül a bracketbe, a győztes továbblép (a vesztes elődöntős a bronzmeccsbe). Ha valami elcsúszik: **kézi** eredmény vagy **visszavonás**.
4. **🔗 Link másolása**: a bracket teljes állása benne van a linkben – kiteszed Discordra, bárki megnyitja és látja (csak olvasás). **💬 Discord-szöveg**: formázott összefoglaló a csatornába. **🖼 Kép letöltése**: PNG bracket.
5. A kupa a szervező böngészőjében mentődik, bezárás után is megvan.

Tipp a lebonyolításhoz: egy szervező egyszerre egy meccset tud futtatni, tehát a meccsek egymás után mennek (kb. 10–15 perc egy meccs): 4 csapat ≈ 1 óra, 8 csapat ≈ 2 óra, 16 csapat 3 óra fölött – utóbbinál érdemes rövidebb meccseket (2 nyert pálya) beállítani. Ha két szervező van, mindkettő a saját gépén futtathatja a saját meccseit, és a kézi eredmény-rögzítéssel kerül össze a bracket.

## Pályaszerkesztő

A főmenü **🛠 Pályaszerkesztő** gombja. 48 pálya helye van; mindegyiket a szerkesztőben rajzolod meg:

- **Bal oldalt** a pályák listája (szaggatott = még üres) és az elemek, csoportokban: **Alap** (padló, fal, kezdőpontok, cél), **Gyűjtés** (kristály, kötélkristály, kristálykapu, kulcs, lakat), **Lapok és ajtók** (színes lapok és ajtók, gomb és óra-ajtó, páros gomb és páros ajtó, kapcsoló és I-es/II-es falak), **Utak** (színes sávok, egyirányú kapuk, futószalagok, jég, teleportok, törékeny padló), **Veszély** (tüske), **Mozgó elemek**. Bal gombbal lerakod, jobb gombbal törlöd, húzva festesz, **Shift+húzással** téglalapot töltesz ki, **Ctrl+Z** visszavon.
- **Mozgó elemek:** őrjárat (kattints végig az útvonal pontjain – ferde szakasz is lehet –, Enter, az utolsó pontra kattintás vagy dupla kattintás: kész, jobb gomb: utolsó pont vissza), lézer, löveg, üldöző (egy kattintás a helyére). Bármelyik eszközzel **megfoghatod** a pályán: a pontokat és középpontokat húzva mozgatod, a kijelölt őrjárat szakaszának közepén lévő **„+"** új pontot szúr be, pontra **jobb gomb** = pont törlése, elemre jobb gomb vagy **Delete** = törlés, **Ctrl+D** = másolat, **nyilak** = egy cellával odébb. A jobb oldali panelen minden tulajdonságuk állítható: sebesség, méret, irány megfordítása; a lézer hossza, forgási sebessége és iránya, kezdőszöge, karjai; a löveg lövésgyakorisága, golyósebessége, késleltetése; az üldöző sebessége és hatótávja.
- **Párosítások:** az összetartozó elemek egy keretben, egymás alatt vannak a palettán (kulcs → lakatos ajtó, sárga gomb → óra-ajtó, lap → ajtó, páros gomb → páros ajtó, kapcsoló → I-es/II-es fal, kristály → kristálykapu, teleport ↔ párja), a gombokon látszik, hányat raktál le, és ⚠ jelzi, ha valamelyik félnek hiányzik a párja. Ha a kurzor egy ilyen elemen vagy a gombján áll, a pályán szaggatott nyíl köti össze a párokat; a „Párosítások mindig látszanak” pipával folyamatosan látszanak.
- **Sötét pálya:** jelölőnégyzet a jobb panelen – csak a figurák körül látni, a cél világít.
- **Jobb oldalt** a pálya neve, tippje, célideje, kötélhossza; **▶ Kipróbálás** (egy gépen, végtelen élettel, a szünet menüből vissza), **✔ Ellenőrzés** (kezdőpontok, cél, párosított elemek, elérhetőség), másolás/beillesztés pályák között.
- **Mentés:** minden változás magától mentődik a böngészőbe, és amíg a „A játék ezeket a pályákat használja" be van kapcsolva, minden mód (páros, 2v2, kupa, heti) ezekkel megy – a vendégek is a gazdától kapják a pályákat, nekik nem kell semmit csinálniuk.
- **Véglegesítés:** 💾 *Mentés fájlba* → a letöltött `palyak.json`-t tedd az `index.html` mellé, és töltsd fel GitHubra is. A játék indításkor ezt a fájlt tölti be, így mindenkinél ugyanazok a pályák lesznek – a szerkesztő piszkozata nélkül is. A `palyak_minta.json` egy kész 48-as készlet, ha kiindulási alap kell (*Mintapályák betöltése*).

## Pályaelemek

| Elem | Mit csinál |
|---|---|
| Kristály (kék gyémánt) | Mind kell, különben zárva a sárga kristálykapu |
| Nyomólap (lila/türkiz kör) | Amíg valaki rajta áll, nyitva az azonos színű ajtó |
| Kék / narancs sáv | Csak az adott színű játékos mehet át |
| Kulcs | Felveszed, és a lakatos ajtónak nekimenve kinyitod |
| Sárga gomb | 4,5 másodpercre kinyitja az óra-ajtót |
| Törékeny (repedt) padló | Rálépés után 0,7 mp-cel leszakad – egyszer lehet átmenni rajta |
| Tüske, vörös gömb, lézer, löveg | Érintés = a pálya elölről (és a kötelet is elvágják, a löveg kivételével) |
| Lézer | A falnál megáll – a fal mögött biztonságos |
| Kötélkristály (üreges, sárga) | Nem a figura szedi fel: a **kötélnek** kell áthaladnia rajta. A kristálykapuhoz ez is kell |
| Páros gomb (két narancs kör) | **Mindkettőtöknek egyszerre** kell rajta állnia – 4,5 mp-re nyitja a páros ajtót |
| Kapcsoló (sárga kar) | Minden érintésre vált: az I-es falak nyílnak és a II-esek zárnak, vagy fordítva |
| Egyirányú kapu (zöld nyíl) | Csak a nyíl irányába lehet átmenni |
| Futószalag (kék nyilak) | Tol a nyíl irányába |
| Jég | Csúszik: lassabb a megállás és a fordulás |
| Teleport (A: kék, B: lila örvény) | Belépsz az egyikbe, a párjából jössz ki – a kötél messziről elszakad, a társad álljon a kijárat mellett |
| Üldöző (lila gömb) | Ha a hatótávjába érsz, utánad megy (lassabb nálad); a kötelet is elvágja. Ha senki sincs a közelben, hazamegy |
| Sötét pálya | Csak a figurák körül látni |

## Ha nem jön létre a kapcsolat

- Mindkét gépen HTTPS-en fusson (a GitHub Pages ilyen) – fájlból (`file://`) megnyitva nem fog menni.
- Nagyon szigorú céges/iskolai hálózat vagy VPN blokkolhatja a WebRTC-t; próbáljátok mobilnetről vagy otthonról.
- Ha a kód „nem található”: a gazda oldalán nyitva kell lennie a lobbynak, és a kódot pontosan kell beírni.
- Teszteléshez van **Egy gépen** mód is: kék = WASD, narancs = nyilak.
