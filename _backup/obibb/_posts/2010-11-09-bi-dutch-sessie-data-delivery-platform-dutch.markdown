---
author: makumbe
comments: true
date: 2010-11-09 18:14:20+00:00
layout: post
link: http://blog.daanalytics.nl/2010/11/09/bi-dutch-sessie-data-delivery-platform-dutch/
slug: bi-dutch-sessie-data-delivery-platform-dutch
title: BI Dutch sessie - Data Delivery Platform (Dutch)
wordpress_id: 549
categories:
- BI Dutch
tags:
- Data Delivery Platform
- Federation
- Oracle BI Server
---

[](http://obibb.files.wordpress.com/2010/11/oracle_s-enterprise-performance-management-system.png)Gisterenavond ben ik aanwezig geweest bij een sessie georganiseerd door [Johan van der Kooij](http://nl.linkedin.com/in/johanvanderkooij) van [BI Dutch](http://www.linkedin.com/groups?home=&gid=46641&trk=anet_ug_hm) bij Sogeti. Johan is in staat geweest om [Rick van der Lans](http://www.r20.nl/) van der Lans te strikken, om te komen vertellen over het Data Delivery Platform (DDP). Rick heeft al eerder artikelen geschreven over het [Data Delivery Platform](http://www.b-eye-network.com/channels/5087/view/9960).

Rick heeft een prettige manier van presenteren. Al direct in het begin weet hij een ieder te boeien met een aantal interessante stellingen en uitspraken. Wat ik persoonlijk een hele leuke vind om over na te denken;

Een Datawarehouse is een middel en géén doel op zich. Een klant vraagt in eerste instantie alleen maar om (snelle) toegang tot zijn of haar bedrijfsgegevens.

[Gartner](http://www.gartner.com/technology/home.jsp) spreekt over Datawarehouses van [Terra- en wellicht wel Zettabytes](http://nl.wikipedia.org/wiki/Veelvouden_van_bytes). [Nigel Pendse ](http://www.bi-verdict.com/)daarentegen heeft aan een paar Gigabytes al voldoende. Het verschil tussen de Bruto en de Netto dataopslag in een Datawarehouse. De Bruto dataopslag kan vele male hoger uitvallen doordat de data op verschillende plekken gedupliceerd en opgeslagen wordt. Interessant kan zijn om eens uit te rekenen wat het dubbel opslaan van data kost in termen van licenties, ontwikkeling ETL, beheer, etc. Uiteraard zullen er legio redenen te bedenken zijn waarom er gekozen wordt voor de traditionele DWH structuren. Toch kan het géén kwaad om een naar alternatieven te kijken. Zet de traditionele DWH structuur eens af tegen de (nieuwe) mogelijkheden op het gebied van In Memory Analytics en [Datawarehouse Appliances](http://www.beyeresearch.com/executive/4639)[](http://obibb.files.wordpress.com/2010/07/data-delivery-platform-bi-dutch.gif). De huidige hardware is er klaar voor.

[![](http://obibb.files.wordpress.com/2010/07/data-delivery-platform-bi-dutch.gif?w=300)](http://obibb.files.wordpress.com/2010/07/data-delivery-platform-bi-dutch.gif)

Terug naar het DDP. Het Data Delivery Platform is een architectuur. Een archictectuur waarbij de applicatie losgekoppeld wordt van de opslagstructuur. Er wordt een 'Metalaag' tussen de applicatie en de opslag geplaatst. In deze Metalaag wordt de vertaalslag gemaakt van applicatie naar data, er wordt intelligentie uit de BI Tool vastgelegd en in het ideale geval metadata vastgelegd. Doormiddel van een aantal viewlagen worden diverse fysieke tabellen aan diverse gebruikers(groepen) gepresenteerd. Tools welke dit verzorgen worden Federation Server genoemd. Het verschil tussen DDP en een Federation Server zit hem de Architectuur versus de Tool. Een Federation Server zal veelal deel uitmaken van een DDP.

Een eindgebruiker kan met een willekeurige BI Tool aansluiten op het DDP. Ook hoeft hij/zij zich géén zorgen meer te maken over waar de dat vandaan komt. Dit wordt allemaal afgehandeld binnen het DDP. Intelligentie en specificaties zijn voor meerdere toepassingen en gebruikersgroepen bruikbaar. Het DDP moet uiteindelijk leiden tot een flexibele, uitgeklede omgeving. Uitgekleed in de zin van het beperken van dupliceren van data.

Mijn interesse voor deze sessie werd bij gewekt vanwege de overeenkomsten tussen DDP en de Oracle BI Server. [Leander van Dongen](http://leandervandongen.blogspot.com/2009/07/data-delivery-platform-van-rick-van-der.html) heeft hier vorig jaar al een en ander over geschreven. De Oracle BI Server moet worden gezien als een Federation Server. Wanneer we kijken naar Oracle’s Enterprise Performance Management System, dan kunnen we de overeenkomsten zien.

[![](http://obibb.files.wordpress.com/2010/11/oracle_s-enterprise-performance-management-system.png?w=300)](http://obibb.files.wordpress.com/2010/11/oracle_s-enterprise-performance-management-system.png)

Ook Oracle gaat in haar architectuur van een gelaagde architectuur. Er kunnen diverse bronnen gekoppeld worden en via allerhande tooling ontsloten worden. De [Oracle BI Server](http://www.oracle.com/global/nl/bi/oracle_bi_suite.html) zorgt via het Common Enterprise Information Model voor de koppeling, integratie en structurering van de informatie uit de fysieke databronnen.

Zowel bij de Federation Servers in een DDP architectuur als in de Oracle BI Server is er sprake van een virtuele 'kijk' naar physieke data. Data wordt niet gedupliceerd, maar gemodelleerd.

Aan het slot van de sessie is Rick onder leiding van Johan ingegaan op een aantal zeer kritische vragen. Het aanwezige publiek leek zich niet zomaar zonder meer te willen laten overtuigen. Ogenschijnlijk zonder problemen behandelde Rick de vragen. Een kleine greep:

Een DDP sluit traditionele Datawarehousing met Datamarts niet uit. Er wordt echter wel kritisch gekeken of het dupliceren van data nodig is (bijv. in het geval van Periode sluitingen). Ook Data Vault structuren staan een DDP niet in de weg. Een Data Vault is echter meestal niet ideaal om op te querien. Dit zal echter binnen de views van de Federation Server opgelost kunnen worden. Cleaning kan via profiling logica, on-demand, geïntegreerd worden. Voorstellen voor opgeschoonde daten kunnen dan zelfs ter beoordeling aan de eindgebruiker aangeboden worden.

Ik ben benieuwd hoe het Data Delivery Platform zich in de toekomst gaat ontwikkelen. Wanneer het publiek van gisteren een afspiegeling is van de 'BI Samenleving', dan heeft het DDP nog wel een lange weg te gaan. 'Het lijkt erop dat tools, die 'In Memory Analytics' ondersteunen, en Data Warehouse Appliances meer kans van slagen hebben.

Al met al een interessant event, met dank aan Johan van der Kooij en Rick van der Lans. Hier is het laatste woord nog niet over geschreven.

**_[](http://www.r20.nl/)_**
