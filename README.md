# Kötelék – 2 fős coop (és 2v2 verseny) ügyességi játék a böngészőben

Két játékos, egy energiakötél. Ha túl messze kerültök egymástól, elszakad, és a pálya elölről indul.
40 pálya, 5 világ (kötelék → gépezet → veszély → fejtörő → kihívás), kb. 2 óra két embernek.
Világonként 8 élet van: ha elfogy, a világ elölről indul (a főmenüben kikapcsolható: „Végtelen élet”).

Egyetlen fájl az egész (`index.html`), nem kell hozzá saját szerver: a két gép közvetlenül,
böngészőből kapcsolódik egymáshoz (WebRTC, PeerJS). GitHub Pages csak a fájlt szolgálja ki.

## Feltöltés GitHubra (kb. 3 perc)

1. GitHubon **New repository** → név pl. `kotelek` → Public → Create.
2. **Add file → Upload files** → húzd be az `index.html`-t → Commit changes.
3. A repo **Settings → Pages** menüjében: *Source: Deploy from a branch*, *Branch: main* / *(root)* → Save.
4. 1–2 perc múlva él a játék itt: `https://<felhasználóneved>.github.io/kotelek/`
   (a Pages oldalon kiírja a pontos címet).

Ha később módosítod az `index.html`-t, csak töltsd fel újra ugyanoda.

## Így játsszatok

### Ketten (páros játék)

1. Mindketten nyissátok meg a linket (asztali böngésző, Chrome/Edge/Firefox).
2. Az egyikőtök: **Szoba létrehozása** → kap egy 4 betűs kódot → elküldi a másiknak.
3. A másik: **Csatlakozás kóddal** → beírja → Mehet.
4. A szoba gazdája látja, hogy a társa csatlakozott, és elindítja (akár a pályaválasztóból is).

- A főmenüben adj meg egy nevet és válassz arcot – ezt látják a többiek a lobbyban és a figurád fölött.
- Mozgás: **WASD** vagy **nyilak**. **R**: pálya gyors újrakezdése (gazda). A főmenü ❓ Súgója minden pályaelemet elmagyaráz; az új elemek első találkozáskor a pályán is kapnak egy rövid tippet.
- **Esc** (a szoba gazdájánál): szünet, pálya újra, pálya átugrása, főmenü.
- A célmezőre **mindkettőtöknek** rá kell állnia, miután minden kristályt összeszedtetek.
- **A kötelet elvágja** a tüske, az őrjárat és a lézer – mindig ugyanazon az oldalon legyetek, és együtt menjetek át.
- A kötél nem húzza magával a másikat: aki lemarad, annál elszakad.
- Zene és hangeffektek a főmenüben (és a szünet menüben) ki-/bekapcsolhatók – a beállítás megmarad a böngészőben. A zene az első kattintás után indul (böngésző-szabály).
- A legjobb idők a gazda gépén mentődnek (böngésző tároló), a pályaválasztóban látszanak a csillagok.

### Négyen (2v2 verseny)

1. A gazda szobát nyit, a másik három ugyanazzal a kóddal csatlakozik.
2. A lobbyban mindenki látja a két csapatot, és a saját nevénél lévő gombbal átülhet a másikba (ha tele van, helyet cserél az ottanival). A gazda bárkit átültethet.
3. A gazda a lobbyban beállítja a verseny hosszát (5 / 10 / 20 / mind a 40 pálya) és indít.
4. Mindkét páros ugyanazt a pályát futja egyszerre, a saját példányán – az ellenfelet áttetsző szellemként látjátok.
   Aki előbb ér be (mindkét tag a célon, minden kristállyal), pontot kap. **Életek nincsenek**: ha elhaltok, csak ti kezditek elölről a pályát, az ellenfél közben halad.
5. A verseny végén az összesített pontszám dönt; az eredmény egy gombbal másolható Discordra.

### Kupa (Discord-bajnokság, 2 / 4 / 8 / 16 csapat)

A főmenü **🏆 Kupa** pontja a szervezőnek való:

1. Kiválasztod a csapatok számát (2, 4, 8 vagy 16 – alapból 8), beírod a kupa nevét és a csapatneveket (soronként egy; a sorrend adja a párokat, a 🎲 Sorsolás keveri) → **Kupa létrehozása**. Alapból: negyeddöntők és elődöntők 3 nyert pályáig, a döntő 5-ig, van bronzmeccs, és minden körnek saját, nehezedő pályakészlete van (bemelegítő pályák nélkül). A ⚙ Beállításoknál körönként átállítható a nyert pályák száma és kattintgatva a pályakészlet, ki-/bekapcsolható a bronzmeccs, és választható véletlen pályasorrend – később, a kupa nézetből is.
2. Egy meccsnél **▶ Indítás** → a játék szobát nyit a két csapat nevével, te **nézőként hostolsz** (nem játszol). A kódot kiteszed Discordra, a 4 játékos belép, mindenki a saját csapatát választja, te indítod a meccset. Játék közben a **Tab** a másik csapat nézetére vált.
3. A meccs végén az eredmény magától bekerül a bracketbe, a győztes továbblép (a vesztes elődöntős a bronzmeccsbe). Ha valami elcsúszik: **kézi** eredmény vagy **visszavonás**.
4. **🔗 Link másolása**: a bracket teljes állása benne van a linkben – kiteszed Discordra, bárki megnyitja és látja (csak olvasás). **💬 Discord-szöveg**: formázott összefoglaló a csatornába. **🖼 Kép letöltése**: PNG bracket.
5. A kupa a szervező böngészőjében mentődik, bezárás után is megvan.

Tipp a lebonyolításhoz: egy szervező egyszerre egy meccset tud futtatni, tehát a meccsek egymás után mennek (kb. 10–15 perc egy meccs): 4 csapat ≈ 1 óra, 8 csapat ≈ 2 óra, 16 csapat 3 óra fölött – utóbbinál érdemes rövidebb meccseket (2 nyert pálya) beállítani. Ha két szervező van, mindkettő a saját gépén futtathatja a saját meccseit, és a kézi eredmény-rögzítéssel kerül össze a bracket.

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

## Ha nem jön létre a kapcsolat

- Mindkét gépen HTTPS-en fusson (a GitHub Pages ilyen) – fájlból (`file://`) megnyitva nem fog menni.
- Nagyon szigorú céges/iskolai hálózat vagy VPN blokkolhatja a WebRTC-t; próbáljátok mobilnetről vagy otthonról.
- Ha a kód „nem található”: a gazda oldalán nyitva kell lennie a lobbynak, és a kódot pontosan kell beírni.
- Teszteléshez van **Egy gépen** mód is: kék = WASD, narancs = nyilak.
