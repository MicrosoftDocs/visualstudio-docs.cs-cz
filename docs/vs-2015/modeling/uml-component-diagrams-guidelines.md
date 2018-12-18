---
title: 'Diagramy komponent UML: Pokyny | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML diagrams, component
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML, component diagrams
- component diagrams
ms.assetid: 6c1bdd60-369e-477e-83ed-7f6fe75c9f0b
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7400bac1fa6dcbf086718e54d18288b8ab80f1b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801462"
---
# <a name="uml-component-diagrams-guidelines"></a>Diagramy komponent UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio, můžete nakreslit *diagram komponent* na zobrazit pomocí něj strukturu softwarového systému. Video ukázku naleznete v tématu [návrh fyzické struktury pomocí diagramů komponent](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Chcete-li vytvořit diagram komponent UML, na **architektura** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**.  
  
 Komponenta je modulární jednotka, která je ve svém prostředí nahraditelná. Její vnitřní součásti jsou skryty, ale má nejméně jedno dobře definované *poskytované rozhraní* přes který je přístupný jeho funkcí. Komponenta může mít také *požadovanými rozhraními*. Požadované rozhraní definuje, jaké funkce nebo služby vyžaduje od jiných komponent. Propojením poskytovaných a požadovaných rozhraní několika komponent lze sestavit větší komponenty. Jako komponentu lze chápat i kompletní softwarový systém.  
  
 Kreslení diagramů komponent má několik výhod:  
  
- Pokud budou vaše vývojové týmy přemýšlet o návrhu z hlediska hlavních bloků, lépe pochopí existující návrh a snáze vytvoří nový.  
  
- Pokud budete o svém systému přemýšlet jako o kolekci komponent s dobře definovanými poskytovanými a požadovanými rozhraními, můžete zlepšit rozdělení jednotlivých komponent. Díky tomu lze snáze pochopit návrh a jednodušeji jej změnit v případě, ze dojde ke změně požadavků.  
  
  Diagram komponent lze využít k reprezentaci návrhu bez ohledu na to, jaký jazyk nebo platformu používá nebo bude používat.  
  
##  <a name="OtherDiagrams"></a> Vztah k jiným diagramům  
 Diagram komponent lze použít společně s jinými diagramy.  
  
|Jiný diagram|Umožňuje diskutovat a sdělovat tyto aspekty návrhu|  
|-------------------|--------------------------------------------------------------------|  
|Sekvenční diagram UML|-Interakcí mezi komponentami systému<br />-Interakcí mezi částmi uvnitř komponenty.<br /><br /> Další informace najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).|  
|Diagram tříd UML|-Rozhraní komponenty. Diagram tříd nabízí podrobné informace o metodách rozhraní.<br />-Data odeslaná v parametrech napříč rozhraními komponent.<br /><br /> Další informace najdete v tématu [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md).|  
|Diagramy činností|-Vnitřní zpracování provádějí komponenty jako odpověď na příchozí zprávy.<br /><br /> Další informace najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).|  
|Diagramy vrstev|– Logické vrstvy architektury pro vaše komponenty.<br /><br /> Další informace najdete v tématu [diagramy vrstev: referenční](../modeling/layer-diagrams-reference.md).|  
  
##  <a name="Basics"></a> Základní kroky pro vytvoření diagramů komponent  
 Referenční informace o elementů v diagramech komponent, naleznete v tématu [diagramy komponent UML: referenční](../modeling/uml-component-diagrams-reference.md).  
  
 Další informace o tom, jak pomocí diagramů komponent při navrhování naleznete v tématu [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md).  
  
> [!NOTE]
>  Podrobné pokyny k vytvoření všech diagramů modelování jsou popsány v [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-component-diagram"></a>Chcete-li vytvořit diagram komponent  
  
1.  Na **architektura** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**.  
  
2.  V části **šablony**, klikněte na tlačítko **Diagram komponent UML**.  
  
3.  Pojmenujte diagram.  
  
4.  V **přidat k projektu modelování**, vyberte existující projekt modelování z řešení, nebo **vytvořit nový projekt modelování**a potom klikněte na tlačítko **OK**...  
  
     Nový diagram komponent se zobrazí s UML **Diagram komponent** sady nástrojů. Sada nástrojů obsahuje požadované prvky a vztahy.  
  
### <a name="drawing-components"></a>Kreslení komponent  
 ![Součásti s rozhraními](../modeling/media/uml-compdrawing.png "UML_CompDrawing")  
  
 Vytvoření *komponenty* (1) pro každou hlavní funkční jednotku v systému nebo aplikace.  
  
 Například pro aplikaci, hardwarové zařízení, webovou službu, sestavení .NET, třídu programu či skupinu tříd nebo všechny oddělitelné segmenty programu.  
  
##### <a name="to-create-components"></a>Vytváření komponent  
  
1.  Klikněte na tlačítko **komponenty** na panelu nástrojů a potom klikněte na prázdnou část diagramu.  
  
     \- nebo –  
  
     Zkopírujte a vložte existující komponentu.  
  
    1.  Najděte existující komponentu v diagramu nebo v **Průzkumníku modelů UML**.  
  
    2.  Klikněte pravým tlačítkem na komponentu a potom klikněte na tlačítko **kopírování**.  
  
    3.  Otevřete diagram, v němž se má zkopírovaná komponenta zobrazit.  
  
    4.  Klikněte pravým tlačítkem na prázdnou část diagramu a potom klikněte na tlačítko **vložit**.  
  
         Zobrazí se kopie komponenty pod novým názvem.  
  
2.  Po kliknutí na název komponenty jej můžete změnit.  
  
3.  Pokud chcete zobrazit pouze záhlaví komponenty, klikněte na dvojitou šipku (5).  
  
### <a name="showing-the-ports-of-a-component"></a>Zobrazení portů komponenty  
 A *port* (2, 3) představuje skupinu zpráv nebo volání operace, které předávají do nebo z komponenty. Skupinu popisuje rozhraní, které definuje typ daného portu. Port může rozhraní buď poskytovat, nebo vyžadovat.  
  
 Port s *poskytovaným rozhraním* (2) poskytuje operace, které jsou implementovány komponentou a, který mohou využívat jiné komponenty.  
  
 Patří mezi ně například uživatelské rozhraní, webová služba, rozhraní .NET nebo kolekce funkcí v libovolném programovacím jazyce.  
  
 Port s *požadované rozhraní* (3) představuje požadavek komponenty na skupinu operací nebo služeb mají být poskytovány jinými součástmi nebo externí systémy.  
  
 Například webový prohlížeč vyžaduje webové servery nebo doplněk aplikace vyžaduje služby aplikace.  
  
 Komponenta může mít libovolný počet portů.  
  
##### <a name="to-add-ports-to-a-component"></a>Přidání portů do komponenty  
  
1. Na panelu nástrojů klikněte na tlačítko **poskytované rozhraní** nebo **požadované rozhraní**.  
  
2. Klikněte na část, k níž ho chcete přidat.  
  
    Port se zobrazí na hranici komponenty.  
  
    Nové rozhraní je vytvořeno jako typ portu. Toto rozhraní se zobrazí v **Průzkumníku modelů UML**.  
  
3. Přetáhněte port kolem hranice komponenty a umístěte jej na požadovanou pozici.  
  
4. Pozici popisku daného portu upravte rovněž přetažením.  
  
5. Po kliknutí na popisek jej můžete změnit. Popisek zobrazuje název rozhraní. Pokud jej změníte, změníte název rozhraní.  
  
   Pokud chcete zobrazit seznam atributů a operací rozhraní, stačí je přidat do rozhraní v Průzkumníku modelů UML. Případně můžete přetáhnout rozhraní z Průzkumníku modelů UML na diagram tříd a přidat operace a atributy tam.  
  
### <a name="linking-between-components"></a>Propojení mezi komponentami  
 Pomocí závislosti (4) lze zobrazit, že jednomu požadavku komponenty lze vyhovět pomocí operací nebo služeb poskytovaných jinou komponentou.  
  
##### <a name="to-show-that-a-provided-interface-can-satisfy-a-required-interface"></a>Zobrazení, že poskytované rozhraní dokáže uspokojit požadavky požadovaného rozhraní  
  
1. Na panelu nástrojů klikněte na tlačítko **závislost**.  
  
2. Klikněte na port s požadovaným rozhraním na jedné komponentě a poté klikněte na port s poskytovaným rozhraním v jiné komponentě.  
  
   Snažte se vyhnout navrhování závislostních smyček, v nichž všechny komponenty ve skupině závisí na všech ostatních komponentách.  
  
##### <a name="to-add-a-port-for-an-existing-interface-to-a-component"></a>Přidání portu pro existující rozhraní do komponenty  
  
-   Najděte rozhraní v **Průzkumníku modelů UML** a potom z něj přetáhněte na komponentu.  
  
     -nebo-  
  
-   Zkopírujte a vložte odkaz z diagramu do rozhraní.  
  
    1.  V diagramu tříd nebo diagramu komponent klikněte pravým tlačítkem na rozhraní a pak klikněte na **kopírování**.  
  
    2.  V diagramu komponent klikněte pravým tlačítkem na komponentu a potom klikněte na tlačítko **vložit odkaz**.  
  
         Na komponentě se zobrazí poskytované rozhraní. Poblíž se zobrazí značka Akce.  
  
        > [!NOTE]
        >  Pokud používáte **vložit** místo **vložit odkaz**, vytvoří se nové rozhraní s novým názvem.  
  
    3.  Pokud jste chtěli vytvořit požadované rozhraní, klikněte na značku akce a potom klikněte na tlačítko **převést na požadované rozhraní**.  
  
##  <a name="Parts"></a> Zobrazení vnitřních částí komponenty  
 ![Diagram komponent zobrazení vnitřních částí](../modeling/media/uml-compshowing.png "UML_CompShowing")  
  
 Do komponenty (1) lze umístit části (3), pomocí nichž je možné zobrazit, jak je komponenta složena z menších komponent, které vzájemně spolupracují.  
  
 Diagram na obrázku ukazuje, že každá instance typu webové služby Dinner Now obsahuje jednu instanci serveru Zákazník a jednu instanci serveru Kuchyně.  
  
 Část je vlastností své nadřazené komponenty, podobně jako atribut patří do běžné třídy. Část má svůj vlastní typ, kterým je obvykle také komponenta. Popisek části má stejný formulář jako obyčejný atribut:  
  
 `+ partName : TypeName`  
  
 Jednotlivé části uvnitř nadřazené komponenty zobrazují poskytovaná a požadovaná rozhraní, která jsou definována pro příslušný typ (4, 5). Operace a služby, které jsou vyžadovány jednou stranou, mohou být druhou stranou poskytovány. Můžete použít **sestavení částí** konektory k zobrazení připojení částmi mezi sebou (6).  
  
 Lze také zobrazit, že je rozhraní nadřazené komponenty skutečně poskytováno nebo požadováno jednou z jejích částí. Možné připojit port nadřazeného prvku k portu vnitřní části pomocí **delegování** vztah (9). Oba porty musí být stejného druhu (poskytované, nebo požadované) a jejich typy rozhraní by měl být kompatibilní.  
  
 Novou část lze vytvořit buď pomocí nového typu, nebo z existujícího typu.  
  
#### <a name="to-add-parts-to-a-component"></a>Přidání částí do komponenty  
  
1.  Vytvořte část pro každou hlavní funkční jednotku, kterou považujete za součást nadřazené komponenty.  
  
    1.  Klikněte na tlačítko **komponenty** v panelu nástrojů a pak klikněte na tlačítko uvnitř nadřazené komponenty (1).  
  
         Nová část (3) se zobrazí uvnitř nadřazené komponenty.  
  
         Je vytvořena nová komponenta v **Průzkumníku modelů UML**. Toto je typ nové části.  
  
         \- nebo –  
  
         Přetáhněte existující komponentu z Průzkumníku modelů UML na nadřazenou komponentu.  
  
         Nová část (3) se zobrazí uvnitř nadřazené komponenty. Jejím typem je komponenta, kterou jste přetáhli z Průzkumníku modelů UML.  
  
         \- nebo –  
  
         Klikněte pravým tlačítkem na komponentu v diagramu nebo v Průzkumníku modelů UML a potom klikněte na tlačítko **kopírování**.  
  
         Klikněte pravým tlačítkem na nadřazenou komponentu a potom klikněte na tlačítko **vložit odkaz**.  
  
         Nová část (3) se zobrazí uvnitř nadřazené komponenty. Jejím typem je komponenta, kterou jste zkopírovali.  
  
    2.  Název nové části můžete změnit poté, co na něj kliknete. Její typ měnit nelze.  
  
    3.  Do nové části můžete přidat poskytované a požadované rozhraní (4, 5). Klikněte na tlačítko **poskytované rozhraní** nebo **požadované rozhraní** nástroje a potom klikněte do části.  
  
         \- nebo –  
  
         Přetáhněte existující rozhraní z **Průzkumníku modelů UML** do části.  
  
         Rozhraní jsou přidána do typu části a zobrazí se přímo na části. Nadřazená komponenta v případě potřeby upraví jeho velikost.  
  
2.  Propojte části mezi sebou.  
  
    -   Použití **závislost** nástroj pro připojení portů různých částí (6).  
  
3.  Připojte části k portům nadřazené komponenty:  
  
    1.  Na nadřazené komponentě vytvořte jeden nebo více portů (7). Klikněte na tlačítko **požadované rozhraní** nebo **poskytované rozhraní** na panelu nástrojů a potom klikněte na nadřazenou komponentu.  
  
    2.  Delegujte (9) port jedné části nebo více částem. Klikněte na tlačítko **delegování** nástroj, pak port na nadřazené komponentě a port na části. Stejným způsobem můžete připojit porty, které buď poskytují, nebo vyžadují rozhraní.  
  
### <a name="showing-the-parts-of-a-part"></a>Zobrazení částí části  
 Poté, co jste rozložili komponentu na jednotlivé části, můžete rovněž rozložit jednotlivé typy částí na vlastní vnitřní části.  
  
 Nejjednodušší je provést každou vrstvu rozložení v samostatném diagramu komponenty. Nejprve musíte vyhledat typ části. Například na obrázku, jedna z částí jmenuje `DNCustomerServer`, a jejím typem je komponenta s názvem `CustomerServer`. Tento typ můžete najít v Průzkumníku modelů UML a umístit jej do jiného diagramu. Poté můžete vytvořit její vlastní vnitřní části.  
  
##### <a name="to-place-a-parts-type-on-a-diagram"></a>Umístění typu části do diagramu  
  
1.  Určete plně kvalifikovaný název typu části.  
  
     Klikněte pravým tlačítkem na části a pak klikněte na tlačítko **vlastnosti**.  
  
     Název typu se zobrazí v **typ** pole v okně Vlastnosti.  
  
2.  Vyhledejte typ části v **Průzkumníku modelů UML**.  
  
     Klikněte na tlačítko **zobrazení**, přejděte na **ostatní Windows**a potom klikněte na tlačítko **Průzkumníku modelů UML**.  
  
     Rozbalte projekt a v případě potřeby také každý balíček, ke kterému typ patří.  
  
     Typ bude uveden jako **komponenty**.  
  
     Pokud chcete, můžete zde jeho název změnit.  
  
3.  Otevřete nebo vytvořte další diagram komponent.  
  
4.  Přetáhněte typ z Průzkumníku modelů UML do diagramu.  
  
     Typ se v diagramu zobrazí jako komponenta.  
  
     Má stejná rozhraní, která jste definovali pro část.  
  
     Nyní můžete dovnitř přidat části.  
  
##  <a name="Designing"></a> Navrhování komponent  
  
### <a name="describing-how-the-parts-collaborate"></a>Popis způsobu spolupráce částí  
 Můžete nakreslit sekvenční diagram zobrazující způsob, jak spolu části vzájemně spolupracují v reakci na zprávu, která dorazí na nadřazenou komponentu.  
  
 Tyto diagramy lze použít k vysvětlení existující komponenty i k návrhu nové komponenty.  
  
 Pokud komponentu stále ještě navrhujete, můžete sekvenční diagramy nakreslit ještě předtím, než se rozhodnete, jaké části bude výsledná komponenta mít. Pomocí sekvenčních diagramů můžete experimentovat s různými částmi, požadovanými rozhraními a sekvencemi zpráv. Sekvenční diagramy nakreslete pro nejčastěji používané a nejdůležitější příchozí zprávy. Následně lze v komponentě vytvořit části, jež odpovídají životnosti, pro kterou jste se rozhodli.  
  
 Pomocí sekvenčních diagramů lze posoudit, jak je práce systému rozložena mezi různé komponenty.  
  
- Pokud příliš velká část práce leží na jediné části, pravděpodobně bude obtížnější aplikaci aktualizovat, než když bude práce rovnoměrně rozložena.  
  
- Pokud bude práce rozvržena příliš slabě a bude docházet k mnoha interakcím, výkon systému může poklesnout a systém může být obtížněji pochopitelný.  
  
  ![Diagram znázorňující spolupráce částí pořadí](../modeling/media/uml-compdescparts.png "UML_CompDescParts")  
  
##### <a name="to-draw-a-sequence-diagram-that-shows-collaboration-between-parts"></a>Nakreslení sekvenčního diagramu, který zobrazuje spolupráci mezi částmi  
  
1.  Vytvořte nový sekvenční diagram.  
  
     Další informace najdete v tématu [sekvenční diagramy UML: pokyny](../modeling/uml-sequence-diagrams-guidelines.md).  
  
2.  Vytvořte životnost pro externí komponentu, uživatele, zařízení nebo jiný objekt aktor (1), který odesílá zprávy této komponentě.  
  
     Můžete nastavit **objektu Actor** vlastnosti této životnosti na hodnotu true, to znamená, že je mimo uvažovanou komponentu. Nad životností se zobrazí obrázek postavičky.  
  
3.  Vytvořte životnost pro poskytované rozhraní (2) této komponenty, na kterou vybraný objekt aktor odesílá zprávy.  
  
4.  Vytvořte životnost pro každou část (3) komponenty.  
  
5.  Vytvořte životnost pro každé požadované rozhraní (4) komponenty.  
  
6.  Nakreslete zprávy od externího objektu aktor (5). Zobrazte způsob předávání zpráv do částí a způsob spolupráce při odpovídání na zprávu.  
  
7.  V případě potřeby zobrazte zprávy odeslané do požadovaného rozhraní (6). V rámci spuštění zprávy nezobrazujte žádné podrobnosti.  
  
### <a name="is-the-component-more-than-its-parts"></a>Je komponenta více než její části?  
 V některých případech není komponenta nic víc než název připojený ke kolekci částí. Veškerou práci provádí části a v době spuštění neexistuje žádný kód či jiný artefakt, který by představoval komponentu.  
  
 To lze naznačit v modelu nastavením **instance je vytvořena nepřímo** vlastnost komponenty. V tomto případě by měla být všechna rozhraní komponenty na portech, s delegací do vnitřních částí.  
  
### <a name="describing-the-process-inside-each-part"></a>Popis procesu uvnitř jednotlivých částí  
 Diagramy aktivit slouží k zobrazení způsobu, jakým komponenta zpracovává příchozí zprávy. Další informace najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Diagram činnosti s vyrovnávací paměť dat](../modeling/media/uml-compdescribingproc.png "UML_CompDescribingProc")  
  
 Pomocí volby Přijmout akci události (1) lze znázornit, že příchozí zpráva začíná nové vlákno.  
  
 Pomocí uzlů objektu a vstupních a výstupních spojek lze znázornit tok informací a místo, kde jsou informace uloženy. V příkladu slouží objekt uzlu (2) k zobrazení položek, které jsou mezi dvěma vlákny ukládány do vyrovnávací paměti.  
  
### <a name="defining-data-and-classes"></a>Definování dat a tříd  
 Diagram tříd UML lze použít k popisu podrobného obsahu:  
  
-   Rozhraní komponent. Když do komponenty přidáváte vyžadovaný nebo poskytovaný port, zobrazí se rozhraní v Průzkumníku modelů UML. Můžete jej přetáhnout nebo zkopírovat do diagramu tříd UML, čímž zobrazíte jeho atributy, operace a vztahy s jinými rozhraními.  
  
-   Data předaná v parametrech operací v rozhraní.  
  
-   Data uložená v komponentách, například jak ukazují toky objektů v diagramech aktivit.  
  
### <a name="general-dependencies-between-components"></a>Obecné závislosti mezi komponentami  
 Diagram komponent lze použít pouze k zobrazení hlavních částí návrhu a jejich vzájemných závislostí.  
  
 ![Závislosti mezi komponentami](../modeling/media/uml-compdepend.png "UML_CompDepend")  
  
 Použití **závislost** nástroj závislost nakreslete. To značí, že návrh jedné komponenty závisí na jiné komponentě.  
  
 Mezi typické druhy závislostí patří:  
  
- Jedna komponenta volá kód v rámci druhé.  
  
- Jedna komponenta vytvoří instanci třídy, která je definována v jiné třídě.  
  
- Jedna komponenta využívá informace vytvořené jinou komponentou.  
  
  Název šipky závislostí lze použít k označení určitého druhu použití. Pokud chcete nastavit název, klikněte pravým tlačítkem myši na šipku a potom klikněte na **vlastnosti**a nastavte **název** pole v okně Vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Video: Návrh fyzické struktury pomocí diagramů komponent](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-6-Designing-a-Projects-Physical-Structure/)



