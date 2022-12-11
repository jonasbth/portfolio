---
Title: Last
Description: Analys av webbplatsers prestanda
---

Några byggvaruhandlares webbprestanda
=======================

Uppgiften handlar om att undersöka några webbplatsers laddningstid och användbarhet.

Urval
-----------------------

![Byggmax](../image/analysis/Byggmax.png) {.float-left .medium}
![Hornbach](../image/analysis/Hornbach.png) {.float-left .medium}
![Bauhaus](../image/analysis/Bauhaus.png) {.float-left .medium}

<p class="clear">
Jag valde att studera tre byggvaruhandlare som finns i eller i närheten av Helsingborg, och där jag brukar handla pellets
och diverse andra produkter som kan behövas till huset. Det handlar om Byggmax, Hornbach och Bauhaus.
</p>

Metod
-----------------------

Först använde jag Googles [PageSpeed Insights](https://pagespeed.web.dev/), som ger en poäng mellan 0 och 100 för webbplatsens
prestanda, tillgänglighet och ett par andra egenskaper. Det finns också mängder av detaljerad data och tips på förbättringar
att ta del av. Sedan gjorde jag egna mätningar med hjälp av Chromes Developer Tools nätverksverktyg. Där mätte jag antal förfrågningar,
överförd datamängd och nedladdningstid (med tre olika definitioner).

För varje webbplats undersöktes tre olika sidor, och för mätningarna med DevTools togs ett medelvärde av tre fullständiga sidnedladdningar.

Resultat
-----------------------

Resultaten sammanställdes i ett kalkylark enligt följande:

<div>
<iframe class="sheet"
    src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTNpbYWUPHnFEHPL4VWZPxrGEduajhnZsmm7ijK2UH45NUV_018pIKEt438XHg1ulHOx8R96rgUWoIT/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false">
</iframe>
</div>

Resultaten från PageSpeed Insights är färgmarkerade enligt samma princip som verktyget självt använder: Rött 0-49, Gult 50-89 och Grönt 90-100.
Poängen är ett viktat medelvärde från flera olika mätvärden som anses som viktiga från ett användarperspektiv. Rött betraktas som dåligt,
gult innebär att förbättringar krävs, och grönt är bra.

Analys
-----------------------

Genomgående kan man säga att mobilprestandan är dålig enligt PageSpeed, vilket är lite problematiskt för webbplatserna, eftersom Google
lägger stor vikt vid den mobila upplevelsen när sökresultat rankas.

Byggmax utmärker sig speciellt när det gäller dålig prestanda, vilket jag också tycker märks när man besöker webbplatsen: Det tar uppemot
10 sekunder innan webbsidan laddat alla delar och börjar "stabilisera" sig. Exempel på förbättringsförslag enligt PageSpeed är:

- Använd bilder med rätt storlek.
- Skjut upp inläsning av bilder som inte visas på skärmen.
- Skicka bilder i modernare bildformat (WebP och AVIF)
- Reducera JavaScript som inte används
- Ta bort resurser som blockerar renderingen.
- Stort DOM-träd (5047 element).
- Enorm nätverksbelastning (många MB laddas ned)

Vad gäller tillgängligheten (accessibility) får Byggmax lite bättre betyg, vilket är bra för personer med funktionsvariation. Från de 
egna mätningarna med DevTools ser man att det är många förfrågningar som krävs (uppemot 400) för att ladda en sida, och det blir många
MB totalt. Däremot ser det lite bättre ut för tiden till DOMContentLoaded eventet och Load eventet, vilket kan ha en positiv inverkan
på användarupplevelsen.

Hornbach har lite bättre mobilprestanda än Byggmax, men är fortfarande underkänd. Dock ser det bättre ut på desktop med bra prestanda
enligt PageSpeed. Tillgänglighetsbetyget är i topp (100 poäng), vilket är verkligt bra. Från mätningarna med DevTools ser man också
att antalet förfrågningar är flera gånger lägre än för Byggmax, och nedladdad datamängd är hälften eller mindre.

Slutligen Bauhaus har något bättre prestandavärden för mobilt, men det är inte bra. På desktop är prestandan bra som för Hornbach.
Däremot är tillgänglighetspoängen sämst i klassen med något sämre än Byggmax. Antalet förfrågningar vid laddning ligger någonstans emellan
Byggmax och Hornbach, och nedladdad datamängd liknar Hornbach för hemsidan, men är lite större för de två andra sidorna.

Den totala laddningstiden för Bauhaus enligt DevTools ligger på över 6 sekunder, men det verkar inte inverka på betygen från PageSpeed
i någon större utsträckning. Tydligen finns det andra parametrar som bidrar positivt. Man kan också ha i åtanke att poäng och laddningstider
kan variera över dygnet, beroende av belastning och annat. I mitt fall gjorde jag mätningar med PageSpeed en lördag förmiddag, och mätningar
med DevTools gjordes på eftermiddagen.

Förbättringsförslagen enligt PageSpeed är liknande för Hornbach och Bauhaus som för Byggmax, men något färre. För alla gäller att
använda bilder med rätt storlek och att använda ett modernare bildformat, vilket sammanfaller väl med temat för det här kursmomentet.

För att rangordna webbplatserna, så skulle jag säga att Hornbach är i topp och Byggmax i botten. Alla webbplatser upplevs som lite 
tunga enligt mig, med mycket bilder och resurser som laddas. Byggmax ger definitivt inte en godkänd upplevelse, som torde ligga på
en handfull sekunder i laddningstid, enligt mig.

Övrigt
-----------------------

Denna undersökning gjordes av undertecknad på egen hand.
