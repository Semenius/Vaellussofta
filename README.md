# Vaellussofta

**"Seikkailusofta"** on tarkoitus olla avoimeen dataan pohjautuva ohjelma, joka enemmän tai vähemmän on omaa mielenkiintoa sekä GIS-harjoittelua. Softa laskee optimaalisen vaellusreitin käyttäjän määrittämien välipisteiden kautta. Se hyödyntää ilmaisia maastokarttoja ja korkeusmalleja reittien optimointiin ottaen huomioon etäisyydet ja korkeuserot.

Täten tarkoitukseksi voidaan tarketaan tuottaa työkalu, jonka avulla vaeltajat _kuten minä_ voivat optimoida esimerkiksi erämaavaelluksia. Tämä edellyttää, että huomioidaan reitin vaakasuora etäisyys sekä aika ja fyysiset ponnistukset, jotka aiheutuvat korkeuseroista. 

"Optimaalisuuden" määritelmä vaelluksessa on luonnostaan subjektiivinen, mutta se sisältää aina kriittisen kompromissin vaakasuoran etäisyyden ja pystysuoran nousun/laskun välillä. Reitti, joka on fyysisesti lyhyempi mutta sisältää äärimmäisiä korkeuseroja _(esim. erittäin jyrkkiä nousuja)_, voi olla monille vaeltajille vähemmän "optimaalinen" kuin hieman pidempi reitti, jossa on loivempia rinteitä.  

## Omainsuudet
- Reitin laskenta määritettyjen paikkojen kautta
- Mahdollisten open source polkuverkoston analyysi ja verkon muodostaminen
- Korkeusprofiilin huomiointi reittikustanuksille
- Reitin ja korkeusprofiilin visualisointi kartalle
- Open sourcen käyttö kuten Maanmittauslaitos, OpenStreetMaps

## Mahdolliset/Käytetyt teknologiat ja riippuvuudet
- [ChatGPT 4o](https://chatgpt.com/) & [Gemini 2.5 Flash](https://gemini.google.com/)
    * Projektin hahmoittaminen sekä alustaminen
- Python x.y
    * Python on laajalti tunnustettu paikkatietoalan suosituimmaksi ja monipuolisimmaksi kieleksi sen yksinkertaisen syntaksin, luettavuuden ja laajan erikoistuneiden kirjastojen ekosysteemin ansiosta.
- [GeoPandas](https://geopandas.org/)
    * Laajentaa suosittuja Pandas-tietorakenteita käsittelemään paikkatietoa, yksinkertaistaen spatiaalisia operaatioita ja analyysejä vektoridatalla.
-  [GDAL/OGR](https://gdal.org/en/stable/)
    * Peruskirjasto laajan valikoiman rasteri- (GDAL) ja vektori- (OGR) paikkatietomuotojen lukemiseen, kirjoittamiseen ja käsittelyyn. Se tarjoaa Python-sidokset, mikä tekee siitä välttämättömän MML- ja OSM-datan käsittelyssä. 
- [Fiona](https://fiona.readthedocs.io/)
    * Tarjoaa luku-/kirjoitusoikeuden yleisiin vektoritietomuotoihin.
- [Rasterio](https://rasterio.readthedocs.io/)
    * Suunniteltu erityisesti rasteridatan lukemiseen ja kirjoittamiseen, mikä on ratkaisevan tärkeää DEM-tietojen kanssa työskenneltäessä.
- [Folium](https://python-visualization.github.io/folium/) & [Matplotlib](https://matplotlib.org/)
    * Matplotlib- ja Folium-kirjastoja reitin ja karttojen visualisoimiseen. OSMnx:llä on omia piirtotoimintoja (esim. plot_graph_route), ja Foliumin avulla saat interaktiivisen web-kartan (vaikka työkalusi olisikin paikallinen, Folium renderöi HTML-kartan esim. Jupyterissa).
- [PostgresSQL]()
    * Tehokas, avoimen lähdekoodin relaatiotietokannan hallintajärjestelmä
- [PostGIS]()
    * PostgreSQL-laajennus, joka lisää tuen paikkatietojen (pisteet, viivat, polygonit, 2D/3D-geometriat) tallentamiseen, indeksointiin ja kyselyyn. 
- [QGIS]()
    * QGIS on ilmainen ja avoimen lähdekoodin työpöytä-GIS-sovellus. Vaihtoehtoisesti Python GUI kuten Tkinter tai PyQt.
- [GrassHopper]()
    * Java-pohjainen reititysmoottori, joka on myös erittäin nopea ja muokattavissa. GraphHopperia voi ajaa itsenäisenä palveluna tai upottaa kirjastoina toiseen sovellukseen. Se tukee useita profiileja (auto, pyörä, jalankulku) ja mahdollistaa myös kustomoidut profiilit – esimerkiksi voit ottaa korkeuserot huomioon määrittelemällä omia kustannuslaskelmia tai käyttämällä sille syötettyä korkeusmallia. GraphHopper käyttää OSM-dataa (tai muuta verkostodataa) ja pystyy myös luomaan isokokoisia reititysaineistoja (maailmanlaajuisesti) suhteellisen pienehköllä muistilla, minkä takia se on suosittu myös mobiilisovelluksissa. Openrouteservice (ORS) on eräs palvelu, joka taustalla käyttää GraphHopperia, joten ne ovat ominaisuuksiltaan samankaltaisia.
- [pgRouting]()
    * PostgreSQL-tietokantaan (PostGIS-laajennuksella) integroitu reititysmoottori. pgRouting mahdollistaa reitinhaun suoraan SQL-kyselyillä tietokantaan talletetusta tieverkosta. Se tukee useita algoritmeja (Dijkstra, A*, jne.) ja on joustava datan suhteen (voit käyttää mitä tahansa tie/verkkoaineistoa, kunhan se on topologisesti mallinnettu oikein).

[Shapely](https://shapely.readthedocs.io/) ?
[NetworkX](https://networkx.org/) ?




## Alustavasti Out-of-Scope
Webbipohjainen alusta

## Ja ennenkaikkea miksi?
Todennäköisesti naiivi idea vaeltamisen yhdistämisestä JAMKin soveltan matematiikan kurssiin _Verkkomallit ja optimoinnin yhdistäminen_. Eihän se ole kuin verkon arvojen laskeminen maaston mukaan ja homma toimii, _toivottavasti_.

