---
title: 'Diagramy případů použití UML: Pokyny | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b4a4bc02202f8ec1f41052dcdea63d97bbcb9671
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793084"
---
# <a name="uml-use-case-diagrams-guidelines"></a>Diagramy případů použití UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio, můžete nakreslit *diagramu případu použití* slouží ke shrnutí, kdo používá vaše aplikace nebo systému, a co mohou provádět s ním. Chcete-li vytvořit diagram případu použití UML, na **architektury** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**.  
  
 Video ukázku naleznete v tématu [do případy použití funkce uspořádání](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Díky diagramu případu použití můžete diskutovat a sdělovat:  
  
- Scénáře v které systému nebo aplikace komunikuje se lidé, organizace nebo externích systémů.  
  
- Cíle, které pomůže tyto objekty actor dosáhnout.  
  
- Rozsah vašeho systému.  
  
  Diagram případu použití nezobrazuje podrobnosti o použití: pouze shrnuje některé z relací mezi případy použití, objekty actor a systémy. Zejména diagram nezobrazuje pořadí, ve kterém jsou kroky provést k dosažení cílů každému případu použití. Popíšete tyto podrobnosti v jiných diagramů a dokumenty, které můžete propojit s každému případu použití. Další informace najdete v tématu [popisující případy použití podrobně](#Details) v tomto tématu.  
  
  Popisy, které zadáte pro případy použití použije několik výrazů souvisejících k doméně, ve kterém funguje v systému, jako jsou prodej, nabídky, zákazníků a tak dále. Je důležité, abyste jasně definovat tyto podmínky a jejich vztahy a můžete to udělat pomocí diagramu tříd UML. Další informace najdete v tématu [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md).  
  
  Případy použití řešení pouze v funkční požadavky na systém. Další požadavky, jako je například obchodní pravidla, kvalitu služby požadavky a omezení implementace musí reprezentovat samostatně. Architektura a interních detailů musí být také popsána samostatně. Další informace o tom, jak definovat požadavky uživatelů najdete v tématu [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
  Příkladů použitých v tomto tématu se vztahují na webovou stránku, na kterém zákazníci mohou objednat jídlo z místní restaurací.  
  
  ![Prvky v diagramu případu použití](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
- *Objektu actor* (1) je třída osoby, organizace, zařízení nebo externí softwarová součást, která komunikuje s vašeho systému. Příklad actors jsou **zákazníka**, **restaurace**, **teplotní snímač**, **Authorizer platební karty.**  
  
- A *případ použití* akce, které provádí jeden nebo více objektů actor ve snaze o konkrétní cíl představuje (2). Vzorové případy použití jsou **objednávka jídla**, **nabídka aktualizace**, **zpracování platby**.  
  
   Na diagramu případu použití jsou případy použití přidružené (3) s objektů actor, které jsou provedeny.  
  
- Vaše *systému (4)* je cokoli, co při vývoji. Může být malé softwarová součást, jehož actors jsou jenom další softwarové komponenty; nebo může být hotové aplikace; nebo může být velký sada distribuované aplikace nasazené přes mnoho počítačů a zařízení. Příklad subsystémy jsou **jídla řazení webu**, **jídla doručování obchodní**, **webu verze 2**.  
  
   Diagram případu použití lze zobrazit, které případy použití jsou podporovány vašeho systému nebo jeho subsystémy.  
  
##  <a name="BasicSteps"></a> Základní postup pro vytvoření diagramy případů použití  
  
> [!NOTE]
>  Podrobné pokyny k vytvoření všech diagramů modelování jsou popsány v [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-new-use-case-diagram"></a>Chcete-li vytvořit nový diagram případu použití  
  
1.  Na **architektura** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**.  
  
2.  V části **šablony**, klikněte na tlačítko **Diagram případu UMLUse**.  
  
3.  Pojmenujte diagram.  
  
4.  V **přidat k projektu modelování**, vyberte existující projekt modelování z řešení, nebo **vytvořit nový projekt modelování**a potom klikněte na tlačítko **OK**.  
  
#### <a name="to-draw-a-use-case-diagram"></a>Chcete-li nakreslit diagram případu použití  
  
1.  Přetáhněte **subsystému** hranic z panelu nástrojů do diagramu, ke znázornění celý systém nebo jeho hlavní komponenty.  
  
    -   Lze nakreslit diagram případu použití bez vašeho systému nebo její součásti systému, které jsou podporovány hranice, pokud nechcete k popisu, který případy použití.  
  
    -   Přetažením rohu systému, chcete-li zvětšit, pokud je to nezbytné.  
  
    -   Přejmenujte odpovídajícím způsobem.  
  
2.  Přetáhněte **Actors** z panelu nástrojů do diagramu (umístěním je mimo hranice jakékoli systému).  
  
    -   Objekty actor představují třídy uživatelů, organizace a externí systémy, které pracují ve vašem systému.  
  
    -   Přejmenujte. Příklad: **agentura zákazník, restaurace, platební karty.**  
  
3.  Přetáhněte **případy použití** z panelu nástrojů na příslušné systémy.  
  
    -   Případy použití představují aktivity, které objekty actor provádět pomocí systému.  
  
    -   Přejmenujte pomocí titulů, které by pochopit objektů actor samy. Nepoužívejte názvy, které se vztahují na váš kód. Příklad: **objednávka jídla, platby jenom za jídla, poskytovat jídla**.  
  
    -   Začněte s hlavní transakce, jako **objednávka jídla**, dokud novější menší interakcí, jako odejít ze **vyberte položku nabídky**.  
  
    -   Umístit každý případ použití v systému nebo hlavní subsystém, který podporuje (ignoruje všechny "fasády" nebo komponentu zapojenou pouze připojení na uživatele).  
  
    -   Můžete nakreslit případu použití mimo hranice systému zobrazíte, že podporován systém, třeba v konkrétní verzi nebo verzi.  
  
4.  Klikněte na tlačítko **přidružení** na panelu nástrojů, pak případu použití a objekt actor, který se účastní případu použití. Propojte každého herce jeho případy použití tímto způsobem.  
  
5.  Struktura použití případech se **zahrnout**, **rozšířit** a **generalizace** vztahy. Každá z těchto odkazů vytvoříte kliknutím na nástroje, a následné použití případu, pak cílový zdroj. Viz následující část [strukturování případy použití](#Structuring).  
  
6.  Případy použití podrobněji popisují. Viz následující část [popisující případy použití podrobně](#Details).  
  
7.  Kreslit samostatné diagramy se zaměřením na různé subsystémy nebo jiné skupiny souvisejících svědectví. Všechny diagramy v jednom projektu modelování jsou zobrazení stejného modelu.  
  
##  <a name="Actors"></a> Kreslení Actors a případy použití  
 Hlavním účelem diagramu případu použití je zobrazit, který komunikuje s vašeho systému a hlavních cílů, které jejich dosažení s ním.  
  
-   Vytvoření **Actors** představující třídy lidé, organizace, jiných systémů, softwaru nebo zařízení, které pracují s systému nebo subsystému.  
  
    -   Zjistěte, jak nakreslit objekty actor a další prvky, naleznete v tématu [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
    -   Pro každou odlišnou sadu cílů Identifikujte actors podle jejich typu nebo role, i když fyzické osoby nebo entity můžou být stejné. Restaurace a zákazníků jsou samostatné subjekty, i když zaměstnanec restaurace může být někdy zákazníka.  
  
-   Vytvoření **případy použití** pro jednotlivé cíle, které každý objekt actor se snaží dosáhnout pomocí systému.  
  
    -   Zadejte název a popis případy použití ve slovech, které by objekt actor rozumí, namísto implementace podmínky.  
  
-   Použít **přidružení** k aktéry s případy použití.  
  
### <a name="inheritance-between-actors"></a>Dědičnost mezi objekty actor  
 ![Diagram případu použití zobrazení dědičnosti](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")  
  
 Lze nakreslit **generalizace** propojení mezi objekty actor. Specializovaný objekt actor, například Club zákazníka v tomto příkladu dědí případy použití generalizované objektu actor, jako je například zákazník. Šipky směřovat na obecnější objektu actor, jako je například zákazník. Při vytváření propojení bodu nejprve na specializovanější objektu actor.  
  
 Specializovaný objekt actor může mít svůj vlastní dodatečné využívání případy, které nejsou k dispozici pro jiné objekty actor.  
  
> [!CAUTION]
>  Neprovádějte smyčky vztahů generalizace, jejichž výsledkem zobecňuje samotný prvek "actor". Smyčky může způsobit chyby.  
  
### <a name="alternative-actor-icons"></a>Ikony alternativní objektu Actor  
 Vlastní ikony můžete použít k reprezentaci objektu actor, místo standardní obrázek. Můžete například změnit ho tak, aby připomínaly zařízení, restaurace, bank a tak dále.  
  
##### <a name="to-change-the-appearance-of-an-actor"></a>Chcete-li změnit vzhled prvek "actor"  
  
1.  Klikněte pravým tlačítkem na objekt actor a potom klikněte na tlačítko **vlastnosti**.  
  
     **Vlastnosti** zobrazí se okno.  
  
2.  Nastavte **cestu k bitové kopii** vlastnost do umístění souboru obrázku.  
  
    -   Můžete použít některou z několika formátů obrázku, včetně GIF, JPG, BMP.  
  
    -   Použijte soubor, který je součástí správy zdrojového kódu řešení nebo projekt tak, aby se při přesunutí nebo zkopírování řešení stále k dispozici.  
  
3.  K replikaci tento vzhled v jiných diagramy případů použití, kopírování objektu actor a jeho vložením do jiného diagramu.  
  
    -   Změna bitové kopie se vztahuje pouze na zobrazení diagramu konkrétní. Nevztahuje se na základní prvek modelu. Pokud přetáhnete objekt actor z Průzkumníku modelů UML do jiného diagramu, zobrazí se jako standardní stonek obrázek.  
  
### <a name="multiplicities-between-actors-and-use-cases"></a>Násobnosti mezi objekty actor a případy použití  
 Přidružení mezi prvek "actor" a případ použití lze zobrazit *násobnost* na každém konci.  
  
 ![Případ 1: 1 pomocí objektu actor](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")  
  
> [!NOTE]
>  Násobnosti asociace v diagramu případu použití jsou skryté, pokud jsou oba **1**.  
  
 Ve výchozím nastavení, je každý násobnost **1**. V striktní výklad modelu násobnost 1 znamená, že, například pouze jednoho zákazníka se účastní řazení každé jídlo a, že každého zákazníka objednávky jídla pouze jeden po druhém.  
  
 Můžete změnit tyto násobnosti.  
  
 Příklad:  
  
 ![Příklad zobrazující násobnost n: n použití](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")  
  
- Na stav, že několik objektů actor stejné třídy dá využít jeden výskyt případu použití, nastavení násobnosti na konci přidružení objektu actor ** 1... \\***.  
  
   Na obrázku dá využít jeden nebo více restaurace v plnění stejné objednávka jídla.  
  
- Chcete-li zobrazit, že každý objekt actor se můžete zúčastnit ve stejnou dobu v několika výskytů případu použití, nastavení násobnosti na konci případu použití přidružení k **\\***.  
  
   Na obrázku může každý restaurace pracovat na splnění pořadí více než jeden po druhém.  
  
##### <a name="to-set-multiplicities-on-an-association"></a>Nastavení násobnosti na přidružení  
  
1. Klikněte pravým tlačítkem na přidružení a potom klikněte na tlačítko **vlastnosti**.  
  
2. Rozbalte buď **první Role** nebo **druhá Role**.  
  
    *Role* znamená, že element na jednom konci přidružení.  
  
3. Nastavte vlastnost Multiplicity výběrem ze seznamu:  
  
   - **1** podílí každý odkaz na stav tohoto přesně jednu instanci této role.  
  
   - **1..\\*** stav, který jeden nebo více instancí této role, které jsou součástí každého odkazu.  
  
   - **0..1** stanovit účast je dobrovolná.  
  
   - **\\*** do stavu, který nula nebo víc instancí této role, na které se účastní odkazu.  
  
> [!NOTE]
>  Mnoho týmů Neumísťujte násobnost informace na diagramy případů použití, byste museli opustit násobnosti na výchozí hodnotu 1. Místo toho poskytují informace v popisy případy použití. V takovém případě se skryjí všechny násobnosti v diagramech případů použití.  
  
### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Pomocí objektu actor nebo použití případu na více diagramů  
 Můžete zobrazit stejné objekty actor a případy použití v několika diagramů. Příklad:  
  
-   Použití v odlišných situacích, ve kterých se tak zapojí jednoho objektu actor se můžete popsat v různých diagramech.  
  
-   Můžete pomocí jednoho diagramu můžete zobrazit objekty actor a subsystémy, ke které je přidružen případu použití a pomocí jiného diagramu můžete zobrazit, jak případ použití strukturovaná do součástí a rozšířené použití.  
  
##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>K zobrazení stejného objektu actor nebo případ použití v různých diagramech  
  
1.  Vytvořte objekt actor nebo na jednom diagramu případu použití.  
  
2.  Vytvořte další diagram případu použití.  
  
3.  Přetáhněte prvek "actor" nebo případ použití vypnout **Průzkumníka modelů** do nového diagramu.  
  
    > [!NOTE]
    >  Pokud umístíte na nový diagram prvek "actor" a případ použití, které jsou již propojeny, přidružení mezi nimi se automaticky zobrazí v novém diagramu.  
  
##  <a name="Details"></a> Případy použití podrobně popisují  
 Představuje případ použití:  
  
- Cílem prvek "actor" v systému, jako například **koupit pokrmu**; a  
  
- Jeden nebo více *scénáře*, to znamená pořadí kroků provést při sledování cíle, například: {**objednávka jídla, platit, poskytování**}. Kromě úspěch scénářů, mohou existovat několik výjimek nebo chyby scénáře, jako například **odmítl platební karty**.  
  
  Případ použití můžete popsané v různé úrovně podrobností. V rané fázi návrhu stačí pouze na název v diagramu případu použití.  Později může být napsán Podrobnější popisy scénářů.  
  
  V sadě Visual Studio Ultimate můžete popsat případu použití několika způsoby, které je možné použít samostatně nebo společně:  
  
- Propojení případu použití s jiný diagram nebo diagramy v projektu.  
  
  -   Diagram činnosti pomáhá vysvětlit složitější procesu tam, kde jsou smyčky a větve paralelních vláken. Můžete také zobrazit tok dat mezi částmi tohoto procesu. Další informace najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).  
  
  -   Sekvenční diagram vám vysvětlují komplexní řadu interakcí mezi různé objekty actor. Také vám pomůže ho zobrazit, co se stane v systému v reakci na každý případ použití. Další informace najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).  
  
- Propojení případu použití stránky Onenotu, části nebo odstavce, která případ použití podrobně popisuje.  
  
- Propojení případu použití s Wordový dokument, ve kterém vám text, snímky obrazovky, a tak dále se popisují scénáře případu použití. Další informace najdete v tématu [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Propojení případu použití diagramu nebo soubor ve stejném řešení  
  
1.  Nakreslení diagramu, jako je například sekvenční diagram nebo aktivita diagram pro ilustraci scénář případu použití.  
  
2.  Přejděte zpět na diagramu případu použití.  
  
3.  Přetáhněte diagram nebo souboru z Průzkumníku řešení na prázdnou část diagramu případu použití.  
  
4.  Připojení z artefaktů k případu použití pomocí **závislost**.  
  
#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Odkaz na soubor řešení například dokument aplikace Word nebo prezentace aplikace PowerPoint  
  
1.  Zápis dokumentu, který používá text, snímky obrazovky, a tak dále k popisu scénáře případu použití.  
  
2.  Přidání dokumentu do řešení.  
  
    1.  Přesunete do stejné složky jako řešení Windows Wordový dokument.  
  
    2.  V Průzkumníku řešení klikněte pravým tlačítkem na řešení, přejděte na **přidat**a potom klikněte na tlačítko **existující položku**.  
  
    3.  Přejděte do dokumentu aplikace Word a klikněte na tlačítko **přidat**.  
  
         Dokument aplikace Word se zobrazí ve složce řešení v Průzkumníku řešení.  
  
3.  Dokument aplikace Word přetáhněte z Průzkumníka řešení na prázdnou část diagramu případu použití.  
  
     Zobrazí se nové artefaktů.  
  
4.  Připojení z artefaktů k případu použití pomocí **závislost**.  
  
#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Odkaz na sdílený dokument, OneNote element nebo webové stránky  
  
1.  Získáte adresu URL sdílené elementu. To může být, například na začátku cesty souboru sítě "\\\\", nebo na webové stránce nebo adresa URL Sharepointu začátek 'http://' nebo odkaz na oddíl Onenotu stránce nebo odstavce začátku "onenote:".  
  
2.  Na panelu nástrojů klikněte na tlačítko **artefaktů** a potom klikněte na tlačítko v diagramu případu použití.  
  
3.  S novou artefakt vybrali, zadejte nebo vložte adresu URL do **hypertextový odkaz** vlastnost.  
  
> [!NOTE]
>  Klikněte dvakrát na artefakt otevření diagramu nebo dokumentu na které odkazuje.  
  
### <a name="linking-use-cases-to-work-items"></a>Propojení případy použití s pracovními položkami  
 Pokud váš projekt používá [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] a máte [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], každý případ použití můžete propojit s pracovní položkou v [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Zjistěte, jak provést tyto odkazy, najdete v článku [propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md).  
  
 To vám umožní:  
  
-   Popište případ použití v propojené pracovní položky. Konkrétně Pokud váš projekt používá šablonu procesu formální sady Visual Studio, můžete propojit s pracovní položkou případu použití. Tento typ pracovní položky obsahuje pole pro popis cíle a scénáře případu použití.  
  
-   Propojení testovacích případů pro případ použití, takže můžete získat zprávy o tom, jak daleko kód vyvíjených implementuje případu použití.  
  
-   Propojit úkoly s případem použití tak, aby mohl sledovat průběh vývojářské práce.  
  
##  <a name="Structuring"></a> Strukturování případy použití  
 Pokuste se popisují chování vašeho systému s několika hlavními svědectví. Každý případ použití velkých definuje hlavní cíl prvek "actor" zřetězený, jako je například nákupu produktu, nebo od dodavatele pohledu poskytuje produkty pro prodej.  
  
 Po provedení těchto cílů vymazat, můžete přejít do další podrobnosti o jak dosáhnout každý cíl a kolísání základní cíle.  
  
 Vyhněte se rozložení případů použití do příliš mnoho podrobností. Případy použití jsou o uživatelské prostředí systému, namísto jeho vnitřní činnost. Kromě toho obecně najdete je produktivnější vytváření starší verze pracovních kódu namísto útraty čas strukturování případy použití v úplných podrobností.  
  
 Na diagramu případu použití lze shrnout vztahy mezi hlavní a podrobnější svědectví. Následující části popisují toto:  
  
-   [Zobrazení podrobností případu použití s zahrnutí](#Include)  
  
-   [Sdílení cílů s generalizace](#Inheritance)  
  
-   [Oddělení na varianty případů s rozšířením](#Extend)  
  
###  <a name="Include"></a> Zobrazení podrobností případu použití s zahrnutí  
 Použití **zahrnout** vztah, chcete-li zobrazit tento případ použití jedné obsahuje také popis některých podrobností jiného. Na obrázku **objednávka pokrmu** zahrnuje **platit**, **zvolte nabídku**, a **zvolte položku nabídky**. Každá z případů využití zahrnutých, podrobnější je krok, který objekt actor nebo objekty actor možná třeba provést k dosažení celkového cíle včetně případu použití. Na šipku by měla odkazovat v případu použití podrobnější, součást.  
  
> [!CAUTION]
>  Ve smyčkách obsahují vztahy, jejichž výsledkem případ použití, včetně samotného by neměla provést. Smyčky může způsobit chyby.  
  
 Můžete sdílet případy použití zahrnuté. V tomto příkladu **objednávka pokrmu** a **předplatit revize** zahrnují případy použití **platit**.  
  
 ![Rozložit s případy použití zahrnují](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")  
  
 Cíle a scénáře zahrnuté uživatelských případů musí dávat smysl nezávisle tak, že mohou být součástí případy použití, které jsou navržené tak, později.  
  
 Oddělení případů použití do včetně a zahrnuté částí slouží k naplnění následujících cílů:  
  
-   Struktury popisů případů použití do různých úrovní podrobností.  
  
-   Vyhněte se opakující se sdílené scénáře použití v odlišných situacích.  
  
####  <a name="Steps"></a> Definovat pořadí podrobný postup  
 Diagram případu použití neříká nic o pořadí, ve které musí provádět podrobné kroky ani o tom, zda každý z nich je vždy nezbytné.  
  
 Pokud chcete, aby pořadí kroků vymazat, můžete použít **artefaktů** připojit samostatné dokumentu včetně případu použití. V následujícím příkladu připojit diagram aktivity pořadí jídla případu použití. Alternativně můžete použít textový dokument, který má seznam kroků nebo posloupnost snímky obrazovky. Další informace najdete v tématu [popisující případy použití podrobně](#Details).  
  
 Všimněte si, že tyto zásady vytváření názvů při použití diagramu činnosti:  
  
- Název aktivity celý je stejný jako včetně případu použití.  
  
- Akce v diagramu činnosti mají stejné názvy jako zahrnutou případy použití.  
  
  Další informace najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).  
  
  ![Použijte kroky v případu ukazuje diagram propojenou aktivitu](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")  
  
###  <a name="Inheritance"></a> Sdílení cílů s generalizace  
 Pomocí relaci generalizace ukazují, že *specializované* případem použití je konkrétní způsob, jak dosáhnout cílů jiným vyjádřena *Obecné* případu použití. Otevřít šipky směřovat v obecnější případu použití.  
  
 ![Případy použití znázorňující na relaci generalizace](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")  
  
 Například **platit** zobecňuje **platit kreditní kartou** a **platit platební**.  
  
> [!CAUTION]
>  Neprovádějte smyčky generalizace vztahů, jejichž výsledkem zobecňuje samotný prvek "actor". Smyčky může způsobit chyby.  
  
 Případy použití specializované vám umožňují zobrazit různé způsoby, že váš systém můžete dosáhnout stejné.  
  
 Případy použití specializované jsou považovány za dědit cílů a objektům aktor obecné případu použití. Není nutné mít své vlastní; scénáře případu obecné použití jeho specializace popisují různé způsoby dosažení cílů.  
  
##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>Jak Refaktorovat běžné případy použití cíle ze dvou nebo více  
  
1.  Vytvoření a název nové obecné případu použití.  
  
2.  Vytvoření **generalizace** relace s velký šipka směřující na nový případ obecné použití.  
  
    1.  Klikněte na tlačítko **generalizace** na panelu nástrojů.  
  
    2.  Klikněte na možnost případu použití specializované (**platit kreditní kartou** v příkladu).  
  
    3.  Klikněte na možnost případu obecné použití (**platit** v příkladu).  
  
3.  Pokud máte popsané cíle pro případy použití specializované, přesun že společné části do popisu obecné případu použití.  
  
4.  Objektů actor, které jsou sdíleny mezi případy použití specializované můžete přesunout do případu obecné použití.  
  
###  <a name="Extend"></a> Oddělení variant případů s rozšířením  
 Pomocí odkazu na rozšíření můžete zobrazit, že jeden případ použití může přidat funkce do jiného případ použití za určitých okolností. Na šipku směřovat na případ hlavní, rozšířené použití.  
  
 ![Jeden případ použití jiného rozšiřuje](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")  
  
> [!CAUTION]
>  Neměli byste provádět ve smyčkách rozšířit vztahů, jejichž výsledkem zobecňuje samotný prvek "actor". Smyčky může způsobit chyby.  
  
 Například **přihlášení** případ použití typické webové stránky mohou zahrnovat **registrovat nové uživatele** – ale jenom Pokud uživatel již nemá účet.  
  
##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Chcete rozdělit do hlavní a rozšiřování části případu použití  
  
1. Vytvoření a název nového rozšíření případu použití.  
  
2. Vytvoření **rozšířit** vztahu se šipkou ukazující na rozšířenému případu použití.  
  
   1.  Klikněte na tlačítko **rozšířit** na panelu nástrojů.  
  
   2.  Klikněte na rozšíření případu použití (**registrovat nové uživatele** v příkladu).  
  
   3.  Klikněte na tlačítko rozšířenému případu použití (**přihlášení** v příkladu).  
  
       > [!NOTE]
       >  Vyhněte se vytváření smyčku vztahů rozšířit v diagramu. Je nesprávný pro případ použití bude rozšíření sebe sama.  
  
3. Pokud jste již vytvořili scénáře pro rozšířenému případu použití, přesuňte příslušné kroky do scénáře rozšíření.  
  
4. Popis rozšíření (**registrovat nové uživatele** v příkladu) by měl obsahovat podrobnosti o where v hlavní scénáře použití tato hodnota se vrátí a za jakých okolností. Si ho představit jako změnu popis hlavních případu.  
  
   Případ použití rozšíření představuje kroky scénáře, které by jinak byly součástí scénáře nejčastěji. Scénář a cílem rozšíření budou vždy číst v kontextu případ využívá proto, že nemají být užitečné nezávisle na sobě.  
  
   Oddělení si rozšíření může být užitečné pro popis těchto situacích:  
  
-   Existují další účastníky, kteří se podílejí pouze v případě použití rozšíření. Správce je potřeba Schválit registraci zákazníka na webové stránce.  
  
-   Samostatné subsystému se bude zabývat případ použití rozšíření.  
  
-   Toto rozšíření bude k dispozici pouze v konkrétních verzích systému. Jednotlivé verze můžete zobrazit jako samostatné subsystém v diagramu případu použití.  
  
##  <a name="Subsystems"></a> Pomocí hranice podsystému  
 Použití hranice podsystému, chcete-li zobrazit, co případy použití jsou v rámci oboru svého systému.  
  
#### <a name="to-draw-a-subsystem-boundary"></a>Chcete-li nakreslit hranice podsystému  
  
1. Na panelu nástrojů klikněte na tlačítko **subsystému**, pak klikněte na tlačítko diagram.  
  
    Subsystém se zobrazí v diagramu.  
  
2. Přetahováním rohů subsystému a upravte jeho velikost.  
  
3. Přetáhněte existující případů použití do nebo z něj subsystému a upravte jeho obsah.  
  
   \- nebo –  
  
   Chcete-li vytvořit nový případ použití přímo v subsystému, klikněte na tlačítko **případ použití** v sadě nástrojů klikněte do subsystému.  
  
> [!NOTE]
>  **Predmety** vlastnost způsobu použití určuje, jaké subsystém je obsažena v.  
  
### <a name="use-cases-outside-the-system-scope"></a>Případy použití mimo obor systému  
 Je často užitečné umístit na případy použití diagramu, které jsou součástí obchodní, ale ne zabývat systému, které vyvíjíte. To pomáhá vývojářům, aby pochopili kontextu své práce. Například může poskytovat jídla zobrazit jako případ použití zahrnující actors restaurace a zákazníků, ale mimo odpovědnost na jídla řazení webu.  
  
### <a name="multiple-subsystems"></a>Více subsystémů  
 Můžete vytvořit několik hranice podsystému zobrazíte jak různé použití případů se zabývá různých komponent systému. Například **přidat hodnocení restaurace** mohou být předmětem na samostatné fórum webu. Mějte na paměti, že by měl řešit diagram případu použití s tím, co je viditelné pro uživatele. Pokud chcete popsat vnitřní rozdělení práce v systému, zvažte použití diagramu komponent.  
  
### <a name="system-versions"></a>Verze systému  
 Pro ilustraci různých verzích systému můžete použít různé subsystému hranice. Například případ použití platby může zahrnovat webu verze 2, ale není ve verzi 1 z toho vyplývá, že systém pomáhá zákazníkům Zkontrolujte své objednávky. Avšak musí přímo zaplatí restauraci.  
  
 Použití **závislost** vztahy propojení subsystémy reprezentující různé verze nebo proměnných typu variant.  
  
 ![Subsystémy zobrazit různé verze systému](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")  
  
## <a name="see-also"></a>Viz také  
 [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)   
 [Sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)   
 [Video: Funkce pro organizaci na případy použití](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases/)



