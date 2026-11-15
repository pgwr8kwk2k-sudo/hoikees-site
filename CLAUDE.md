# Kees — projectcontext voor Claude Code

Lees dit eerst. Dit is de volledige context van het project. Antwoord in het Nederlands.

## Wie en wat
- Eigenaar: Bruce, solo-ondernemer in Oost-Nederland (Almelo). Werkt op een Mac. Bekende stack: React, Supabase, Vercel (gebruikt hij ook voor zijn andere project Walima).
- **Kees** is een algemeen AI-platform voor mensen die in Nederland wonen. Geen "betere ChatGPT", maar iets dat voelt als Nederland zelf: alledaagse gesprekspartner, kent de buurt, de dagen, de gewoontes, en geeft eerlijk productadvies met actuele prijzen.
- Productnaam en assistent: **Kees**. Bedrijfsnaam: **Dijk**. Slogan: "Klaar is Kees".
- Domein: **hoikees.nl** (geclaimd). Social: @hoi.kees (Instagram, TikTok).
- **Vertrouwelijk:** naar buiten toe (partners, publieke pagina's) niet benadrukken dat het een Nederlandse AI is. Teksten zeggen "assistent", kloppen altijd, maar gaan niet over de techniek.

## Huidige taak
Een "binnenkort"-pagina (`index.html`) online zetten op hoikees.nl, zodat de Awin-aanmelding (affiliate-netwerk) kan worden afgerond. Awin eist een live, publiek bereikbare site en raadt aan het woord "Awin" in de broncode te zetten (staat er al in als `<meta name="awin">` en commentaar).

Stappen:
1. `CONTACT@VOORBEELD.NL` (2x) vervangen door het e-mailadres dat Bruce opgeeft.
2. Private GitHub-repo `hoikees-site`.
3. Deploy naar Vercel, domein `hoikees.nl` (en `www.hoikees.nl` → redirect) koppelen.
4. Bruce precies vertellen welke DNS-records hij bij zijn registrar moet invullen.
Verander niets aan inhoud of stijl van de pagina tenzij Bruce het vraagt.

## Volgende fase (na deze taak): testversie voor Coolblue
Coolblue (via Awin) en bol hebben in principe ja gezegd op samenwerking.
- Coolblue wil: een werkende testversie met contactgegevens (login mag), uitleg hoe bezoekers bij Coolblue-producten komen, en het Awin publisher-ID. Bij livegang tweede check.
- bol wil later: een openbare, goed gevulde site met eigen toegevoegde waarde. Bruce is verantwoordelijk voor AI-content. Feed/API pas na goedkeuring.
- Eerste categorie: kleine keukenapparaten (airfryers, staafmixers, blenders, waterkokers, koffiezetters).

Architectuur testversie:
1. Nachtelijk script haalt Coolblue-productfeed via Awin; niet-op-voorraad en niet-commissiegevende producten eruit; rest in Supabase met tijdstip.
2. Gebruikersvraag → eerst zoeken in Supabase → alleen die producten naar het taalmodel.
3. **Het taalmodel verzint nooit prijzen.** Het formatteert alleen data uit de database.
4. Validatie vóór tonen: elke prijs en productnaam moet exact in de database staan, anders opnieuw of zonder dat product.
5. Knop "Bekijk bij Coolblue" = Awin-link.
6. Supabase voor database en login, Vercel voor hosting. Zoveel mogelijk gratis plannen; dagmaximum op de taalmodel-API.

Later: supermarktaanbiedingen via PrijsProfeet API (gratis tier commercieel toegestaan mits zichtbare bronvermelding "Supermarktprijzen via PrijsProfeet" op elk scherm met die prijzen; cache max 24 uur; niet de catalogus crawlen of doorverkopen; data verwijderen binnen 14 dagen na stoppen). Lokale winkels voeren zelf hun aanbiedingen in (pilot Almelo).

## Karakter van Kees
- Nuchter (kort, direct), hartelijk (droge kwinkslag), betrouwbaar (altijd bron en tijd, nooit verzonnen), van hier.
- Nooit toeristisch (klompen/kaas/molens als grap), nooit kinderachtig.
- Mening alleen als iemand om advies vraagt. Twee standen: "Kort en zakelijk" en "Denk mee".
- Onzekerheid alleen met concrete reden; "niet gevonden" is nooit het hele antwoord: zeg wat wel bekend is en hoe je het zeker weet.
- Zegt nooit dat hij een mens is (ook verplicht onder de EU AI-regels).
- Standaard Algemeen Nederlands; alles wat iemand naar een ander stuurt altijd in nette, algemene taal.
- Geen betaalde plekken in advies, ooit.

## Huisstijl (vastgelegd)
Kleuren:
| Naam | Licht | Donker | Taak |
| --- | --- | --- | --- |
| Kees-oranje | #C2410C | #F07A3C | Logo, sjaal, knoppen (~10%) |
| Zuivelcrème | #FBF6EC | #141B24 | Achtergrond (~60%) |
| Polderinkt | #1F2A37 | #F3ECDD | Tekst (~30%) |
| Slootgroen | #3F7D58 | #7CC49A | Alleen "klopt": bron, gecontroleerde prijs |
- Rood-wit-blauw alleen bij feestdagen. Geen paars/blauw verloop, geen felrode waarschuwingen (waarschuwing = inkt met oranje streep links).
- Alle tekstcombinaties halen WCAG 4,5:1. Donkere modus volgt systeem.

Letters (Google Fonts):
- Fredoka Bold: alleen de naam "Kees", logo, mascotte-momenten.
- Nunito ExtraBold: kopjes en prijzen. Nunito Regular: lopende tekst (17px mobiel). Nunito-cijfers zijn standaard even breed.

Vormen: kaart 20px radius, knop 13px, app-icoon 16px, invoer/pil volledig rond. Lijniconen met ronde uiteinden in polderinkt.
Beeld: illustraties als in een goede krant (gedempte huisstijlkleuren, echte verhoudingen, fijne lijn, papierstructuur, lage horizon, alleen Kees heeft een gezicht). Foto's alleen echt (product van winkel, lokaal van winkelier), nooit stock. Hoogstens één Nederlands beeldaccent per scherm; dunne horizonlijn mag altijd.

Mascotte: Kees de reiger, van opzij, lange dunne poten, slanke nek, vleugel van één lijn, kuif, dolksnavel, oranje sjaal. Kijkt altijd naar de tekst. Als plaatje alleen op startscherm, wachtscherm, feestdagen, marketing; nooit bij nare onderwerpen. Nooit een product/merk vasthouden. In donker lichte poten.

Startscherm: groet + dag + plek ("Almelo ✎"), Kees klein rechtsboven, balk "In Nederland" (één landelijk onderwerp, vertaald naar de gebruiker) en balk "Bij jou" (weer, aanbiedingen met afstand, eigen winkels), beide dicht één regel, openklapbaar; weetje over vandaag gestippeld eronder; typveld onderaan.
Plek: gebruiker geeft plaats of 4 cijfers postcode (nooit volledig adres), GPS optioneel, altijd wijzigbaar.
Wachtscherm: alleen bij >~1s; Kees vliegt (nek ingetrokken, poten achteruit) over landschap van de regio, "Kees zoekt het even uit…", balk zonder percentages, weetje van vandaag; stilstaand bij prefers-reduced-motion.

## Documenten (alleen ter info, niet nodig voor deze taak)
- Stijlgids: https://claude.ai/artifact/1ya3po83W41SSD7MiNTWHa
- Plan testversie: https://claude.ai/artifact/BNfv6SVsPrLqjUUTwG7CkS
- Huisstijl-canvas: https://claude.ai/artifact/3MnnbWbiFZVWyxA24SV2VW

## Werkwijze
- Bruce wil dat elke keuze een reden heeft. Leg kort uit waarom.
- Zakelijke situatie: nog geen KvK en geen merkregistratie; Awin-aanmelding als particulier, bedrijfsnaam "Dijk". Geld zoveel mogelijk gratis houden.
- Vraag bevestiging voordat je iets onomkeerbaars doet of iets dat geld kost.
