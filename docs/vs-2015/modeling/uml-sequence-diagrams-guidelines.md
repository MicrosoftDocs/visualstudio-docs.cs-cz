---
title: 'Sekvenční diagramy UML: Pokyny | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 56ecc5c54611f94cdbfb0f08ec54a4e0722f0cbd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803627"
---
# <a name="uml-sequence-diagrams-guidelines"></a>Sekvenční diagramy UML: Pokyny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio, můžete nakreslit *sekvenční diagram* k zobrazení interakce. Interakce je posloupnost zpráv mezi typické instance tříd, komponenty, subsystémy nebo objekty actor.  
  
 Sekvenční diagramy UML jsou součástí modelu UML a existují jenom v rámci projektů pomocí modelování UML. K vytvoření sekvenčního diagramu UML na **architektura** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**. Další informace o [elementů diagramu UML pořadí](../modeling/uml-sequence-diagrams-reference.md) nebo [diagramů pomocí modelování UML](../modeling/edit-uml-models-and-diagrams.md) obecně. Video ukázku naleznete v tématu [náčrtu interakce s použitím sekvenčních diagramů (2010)](http://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>V tomto tématu  
 [Pomocí sekvenčních diagramech UML](#Using)  
  
 [Základní postup pro vytvoření sekvenčních diagramů](#BasicSteps)  
  
 [Vytváření a používání jednoduchý sekvenční diagramy](#Simple)  
  
 [Třídy a životnosti](#ClassesAndLifelines)  
  
 [Vytváření opakovaně použitelných interakce pořadí](#Multiple)  
  
 [Sbalení skupin životnosti](#Collapse)  
  
 [Popis struktury řízení pomocí fragmentů](#Fragments)  
  
##  <a name="Using"></a> Pomocí sekvenčních diagramech UML  
 Sekvenční diagramy můžete použít pro různé účely na různých úrovních podrobností programu. Typické situace pro nakreslení sekvenčního diagramu jsou následující:  
  
- Pokud máte diagram případu použití, který shrnuje uživatelé vašeho systému a své cíle, můžete nakreslit sekvenční diagramy k popisu interakci hlavní součásti systému pro splnění cíle každému případu použití. Další informace najdete v tématu [diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Pokud jste našli zprávy odeslané na rozhraní komponenty, můžete nakreslit sekvenční diagramy k popisu interakci vnitřních částí komponenty k dosažení výsledku, vyžaduje se pro příchozí zprávy. Další informace najdete v tématu [diagramy komponent UML: pokyny](../modeling/uml-component-diagrams-guidelines.md).  
  
  Vytvoření diagramů pořadí má několik výhod:  
  
- Můžete snadno zobrazit, jak jsou úlohy distribuované mezi komponentami.  
  
- Můžete identifikovat vzory interakcí, které ztěžují aktualizaci softwaru.  
  
## <a name="relationship-to-other-diagrams"></a>Vztah k jiným diagramům  
 Sekvenční diagramy UML spolu s jinými diagramy můžete použít několika způsoby.  
  
#### <a name="lifelines-and-types"></a>Životnosti a typy  
 Životnosti, které nakreslíte v sekvenčním diagramu lze představují typické instance komponentami nebo třídami v systému. Můžete vytvořit životnosti z typy a typy ze životností a zobrazení typů v diagramech tříd UML a diagramy komponent UML. Další informace najdete v tématu [třídy a životnosti](#ClassesAndLifelines).  
  
#### <a name="parameter-types"></a>Typy parametrů  
 Můžete také popisují v diagramu tříd UML typy parametrů a vrátí hodnoty, které byly použity ve zprávách odesílaných mezi životnosti.  
  
#### <a name="use-case-details"></a>Podrobnosti o případu použití  
 Případ použití představuje cíl uživatele, společně s posloupnost kroků k dosažení cíle. Postupně jednotlivé kroky můžete popsané v několika způsoby. Jednou z možností je nakreslit sekvenční diagram, který ukazuje interakce mezi uživateli a hlavní součásti systému. Další informace najdete v tématu [diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Základní postup pro vytvoření sekvenčních diagramů  
 Úplný seznam elementů v sekvenčních diagramech, naleznete v tématu [sekvenční diagramy UML: referenční](../modeling/uml-sequence-diagrams-reference.md).  
  
> [!NOTE]
>  Podrobné pokyny k vytvoření všech diagramů modelování jsou popsány v [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-sequence-diagram"></a>Chcete-li vytvořit sekvenční diagram  
  
1. Na **architektura** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**.  
  
2. V části **šablony**, klikněte na tlačítko **sekvenční Diagram UML**.  
  
3. Pojmenujte diagram.  
  
4. V **přidat k projektu modelování**, vyberte existující projekt modelování z řešení, nebo **vytvořte nový projekt modelování**a potom klikněte na tlačítko **OK**.  
  
    Zobrazí se nový diagram sekvence **sekvenční Diagram** sady nástrojů. Sada nástrojů obsahuje požadované prvky a konektory.  
  
   ![Části sekvenčního diagramu](../modeling/media/uml-sequence.png "UML_Sequence")  
  
#### <a name="to-draw-a-sequence-diagram"></a>Chcete-li nakreslit sekvenční diagram  
  
1.  Přetáhněte **životnosti** (1) z **nástrojů** do diagramu k reprezentaci instance tříd, komponenty, objekty actor nebo zařízení.  
  
    > [!NOTE]
    >  Můžete také vytvořit životnosti přetažením existující třídy, rozhraní, objektu actor nebo komponenty z **Průzkumníku modelů UML** do diagramu. Tím se vytvoří životnost představující instanci zvoleného typu.  
  
2.  Nakreslete zprávy zobrazující, jak spolupracovat životnosti k dosažení určitého cíle.  
  
     K vytvoření zprávy (3, 4, 6, 7), klikněte na nástroj message. Pak klikněte na tlačítko odeslání životnosti v místě, kde má být zpráva, kterou chcete spustit a klikněte na přijímající životnost.  
  
     Provádění události (5) se zobrazí v přijímající životnost. Spuštění výskyt představuje určitou dobu, během kterého je instance provádění metody. Můžete vytvořit další zprávy, které začínají výskytu spuštění.  
  
3.  Chcete-li zobrazit zprávu, která pochází z neznámého zdroje událostí (9) nebo vysílá Neznámý příjemcům (10), nakreslete asynchronních zpráv z nebo na prázdné místo v diagramu. Tyto zprávy se nazývají *nalezenými zprávami* (9) a *ztracené zprávy* (10).  
  
    > [!NOTE]
    >  Chcete-li přesunout skupinu životností se ztracenými či nalezenými zprávami, postupujte podle následujícího postupu vyberte životnosti předtím, než je přesunete: nakreslete okolo těchto životnosti, nebo když stisknete a podržíte obdélník **CTRL** klíče při výběru každé životnosti. Pokud používáte **Vybrat vše** nebo **CTRL**+**A** vyberete všechny životnosti a následně je přesunete, ztracené nebo nalezené zprávy připojené k těmto životnostem nepřesune. Pokud k této situaci dojde, můžete tyto zprávy přesunout samostatně.  
  
4.  Nakreslete sekvenční diagramy pro každou hlavní zprávu do stejné součásti nebo systému.  
  
#### <a name="to-change-the-order-of-messages"></a>Chcete-li změnit pořadí zpráv  
  
-   Přetáhněte zprávu směrem nahoru nebo dolů v jeho životnost. Můžete ji můžete přetáhnout nad další zprávy, nebo do nebo z něj blok spuštění.  
  
     \- nebo –  
  
-   Kliknutím na tuto zprávu a použít **šipka nahoru** a **šipka dolů** klíče upravit zprávu pozic. Použití **SHIFT + šipka nahoru** a **SHIFT + šipka dolů** Chcete-li změnit pořadí zpráv.  
  
#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Chcete přesunout nebo kopírovat sekvencemi zpráv na sekvenční diagram  
  
1.  Klikněte pravým tlačítkem na zprávu (3, 4) a pak klikněte na tlačítko **kopírování**.  
  
2.  Klikněte pravým tlačítkem na výskyt spuštění (5) nebo životnost (1), ze kterého chcete novou zprávu odeslat, a potom klikněte na **vložit**. Nový odesílatel může být na jiný diagram, chcete-li.  
  
     Kopie zprávy a všechny její podpůrné zprávy se přidá na konec provádění výskyt nebo na konci životnosti.  
  
    > [!NOTE]
    >  Vložená zpráva se zobrazí vždy na konci výskyt provádění nebo životnost. Po vložení ho ji můžete přetáhnout až starší pozice.  
  
#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Můžete zobrazit a upravit text podpis zprávy  
  
- Cílovou životnost musí být svázán nebo mapovány na typy pro text podpis viditelný. K provedení této úlohy, proveďte jednu z následujících kroků:  
  
  - Klikněte pravým tlačítkem na životnost a klikněte na tlačítko **vytvořit třídu**.  
  
     -nebo-  
  
  - Vyberte životnosti, stiskněte klávesu **F4**a potom v **vlastnosti** okno, nastavte **typ** vlastnost do existujícího typu nebo zadejte název nového typu. Klikněte pravým tlačítkem na popisek zprávy a klikněte na tlačítko **operace vytvoření**.  
  
    Podpis text se zobrazí pod popiskem zprávy. Teď můžete upravit text podpis. Další informace najdete v tématu [třídy a životnosti](#ClassesAndLifelines).  
  
#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Ke zlepšení rozložení sekvenční diagram  
  
-   Klikněte pravým tlačítkem na prázdnou část diagramu a potom klikněte na tlačítko **změnit uspořádání rozložení**.  
  
-   Chcete-li zrušit operaci, klikněte na tlačítko **upravit**a potom klikněte na tlačítko **zpět**.  
  
#### <a name="to-change-the-package-that-owns-the-interaction"></a>Chcete-li změnit balíček, který vlastní interakce  
  
1.  V **Průzkumníku modelů UML**, najít interakce zobrazující sekvenční diagram.  
  
    > [!NOTE]
    >  Interakce se nezobrazí v **Průzkumníku modelů UML** dokud nepřidáte první životnosti v sekvenčním diagramu.  
  
2.  Přetáhněte interakci do balíčku.  
  
     \- nebo –  
  
     Klikněte pravým tlačítkem na interakce a potom klikněte na **Vyjmout**. Klikněte pravým tlačítkem na balíček a pak klikněte na tlačítko **vložit**.  
  
##  <a name="Simple"></a> Vytváření a používání jednoduchý sekvenční diagramy  
 Nejjednodušší a největší nejběžněji používanými formou sekvenční diagram obsahuje pouze životností a zpráv. Diagram tohoto druhu umožňuje zřetelně typická posloupnost interakcí mezi objekty v návrhu, nebo mezi vašeho systému a na jejich uživatele. To je často dostatek můžete diskutovat a sdělovat svůj návrh.  
  
 Tady je pár věcí k uvážení při kreslení jednoduchý sekvenční diagram.  
  
### <a name="types-of-message"></a>Typy zpráv  
 Existují tři nástroje, které můžete použít k vytvoření zprávy.  
  
-   Použití **synchronní** nástroj k popisu interakci ve kterém odesílatel čeká příjemce vracet odpovědi (3).  
  
     A  **< \<vrátit >>** šipky se zobrazí na konci výskyt spuštění. Znamená to návrat ovládacího prvku do odesílatele.  
  
-   Použití **asynchronní** nástroj k popisu interakci ve kterém odesílatel může pokračovat okamžitě bez čekání na příjemce [4].  
  
-   Použití **vytvořit** nástroj k popisu interakci ve kterém Odesílatel vytvoří příjemce (8).  
  
     Vytvořit zprávu by měl být první zpráva, která přijímá příjemce.  
  
### <a name="annotating-the-interactions"></a>Zadávání poznámek k interakce  
 K popisu více podrobností o pořadí, můžete umístit **komentář** kdekoli v diagramu.  
  
 Pomocí **odkazy komentářů**, můžete propojit s komentáři životnosti, spuštění, interakcí a fragmenty.  
  
> [!CAUTION]
>  Pokud chcete připojit komentář na konkrétní místo v pořadí, propojte ho ke spuštění výskyt, použití interakcí, nebo fragment. Nepropojovat ho s životnost, protože v takovém případě ji není zůstanou připojené správné okamžiku v sekvenci.  
  
 Použijte komentář:  
  
-   Všimněte si, co bylo dosaženo klíčové body posloupnosti. To pomáhá čtenáři zobrazíte cílů interakce.  
  
-   Popište obecným cílem celé pořadí. Připojit komentář k výskytu počáteční provádění nebo ponechte nepřipojené. Například "zákazník zvolil položky v nabídce a udělil cenu."  
  
-   Popisuje povinnosti každé životnosti. Připojte komentář k životnosti. Například "řazení Manager shromažďuje volba z nabídky zákazníka."  
  
-   Mějte na paměti výjimky nebo alternativy, které může provádět jako alternativu k typická posloupnost znázorněno. Například "zákazníka můžete přeskočit zbývající část tohoto pořadí."  
  
    -   Zvažte použití fragmentů formálnější alternativou pro tento typ poznámek. Zobrazit [popisující struktury řízení pomocí fragmentů](#Fragments)  
  
## <a name="deciding-the-scope-of-the-diagram"></a>Rozhodování o tom, rozsah diagramu  
 Je důležité, aby bylo jasné, o jaké diagramu je určená k zobrazení.  
  
#### <a name="initiating-event"></a>Událost inicializace  
 Každý diagram by měl zobrazit posloupnost interakcí, které vyplývají z jedné zahájení události. To může být, například:  
  
-   Uživatel zahajuje případ použití, například, otevření webové stránky pro nákup pokrmu.  
  
-   Zpráva z jednoho systému komponenty do jiného, například dotazování dostupnost položky, které zákazník chce koupit.  
  
-   Událost aktivovaného změnou stavu, například akcie položky spadající pod prahovou hodnotu.  
  
#### <a name="level-of-detail"></a>Úroveň podrobností  
 Sekvenční diagramy můžete zobrazit různé úrovně podrobností. Můžete rozhodnout, úroveň podrobností ve dvou dimenzích samostatné téměř nezávisle na sobě:  
  
 Životnosti může představovat jednu z těchto úrovní podrobností:  
  
- Objekty v kódu programu, kterých existuje, nebo kterou vyvíjíte.  
  
- Komponenty nebo jejich. Tyto dílčí součásti, obvykle vynechání fasády, proxy servery a další mechanismy výkonu.  
  
- Váš systém a externích objektů aktor  
  
  Zprávy mohou představovat jednu z těchto úrovní podrobností:  
  
- Software zprávy v programovém kódu v rozhraní API nebo webové rozhraní.  
  
- Transakce nebo dílčí transakce, například mezi uživateli a systému, nebo mezi kódem a databáze.  
  
- Případy použití – hlavní interakce mezi uživateli a systému.  
  
  Zda zkoumáte existující kód nebo popisující nový návrh, je často užitečné pro kreslení a diskutovat o méně podrobné zobrazení.  
  
## <a name="describing-variations"></a>Popis změn  
 Diagram znázorňuje jeden typická posloupnost událostí. Pokud chcete zobrazit alternativní možnosti, jako je například scénáře selhání, můžete použít kteroukoli z těchto možností:  
  
-   Kreslit samostatné sekvenčních diagramů popisují tyto scénáře  
  
-   Použití [popisující struktury řízení pomocí fragmentů](#Fragments) zobrazíte smyčky, alternativy a tak dále.  
  
## <a name="assessing-the-design"></a>Posouzení návrhu  
 Diagram můžete použít k vyhodnocení rozdělení úloh mezi jeho objekty nebo komponenty. Zvážení refaktoringu, pokud se zobrazí tyto modely:  
  
-   Provádění všeho volání všechno ostatní, zatímco jiné životnosti na ně pouze odpovídají pasivně vypadá, že jedna životnost.  
  
-   Počet zpráv napříč životností. Každá životnost musí odesílat zprávy do několika okolí a nesmí komunikovat s okolím jeho okolím. By mělo být obvykle možné uspořádat životnosti, takže existují jenom na několika místech, kde zpráv mezi životnosti; a kde jsou přechody, cílovou životnost by neměl také vyměňovat zprávy, které mají překřížené životnosti.  
  
-   Pro zpracování více než jeden typ úkolu, který vypadá, že některé životností. By měl snadné najít jedné stručné věty, který popisuje povinnosti každé životnosti, shrnutí práce, kterou v reakci na každou zprávu, kterou přijímá.  
  
##  <a name="ClassesAndLifelines"></a> Třídy a životnosti  
 Životnosti v sekvenčních diagramech zobrazit instance třídy nebo rozhraní komponenty. Můžete pojmenovat životnost dvěma způsoby:  
  
|**Pro tento účel**|**Použijte tento formát**|  
|--------------------------|-------------------------|  
|Instanci anonymního typu.<br /><br /> Použijte, pokud máte pouze jedna životnost jednotlivých typů.|*typeName*|  
|Pojmenované instance typu.<br /><br /> Použijte, pokud chcete zobrazit sekvenci, která zahrnuje více než jednu instanci stejného typu.|*objectName*:*typeName*|  
  
### <a name="creating-lifelines-from-types"></a>Vytváření životnosti z typů  
 Můžete vytvořit nové životnosti ze třídy, které jsou již definovány, například v diagramu tříd.  
  
> [!NOTE]
>  Ujistěte se, že máte existující sekvenční diagram před provedením této úlohy.  
  
##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Vytvořte životnost z existujícího typu  
  
- Třída, komponenty nebo rozhraní z Průzkumníku modelů UML přetáhněte do sekvenčního diagramu.  
  
   \- nebo –  
  
  1. Klikněte pravým tlačítkem na třídu, komponenty nebo rozhraní na jeho odpovídající diagramu a potom klikněte na tlačítko **vytvořit životnost**.  
  
  2. V **vytvořit životnost** dialogovém okně vyberte sekvenčního diagramu a potom klikněte na tlačítko **OK**.  
  
     Zobrazí se nové životnosti s názvem instance, jehož typ je typ, kterou jste přetáhli.  
  
  > [!NOTE]
  >  Tato akce tolikrát, kolikrát chcete, můžete opakovat. Tím se vytvoří životnosti s názvy jiné instance.  
  
##### <a name="to-change-the-type-of-a-lifeline"></a>Chcete-li změnit typ životnosti  
  
1.  Klikněte pravým tlačítkem na životnost a potom klikněte na tlačítko **vlastnosti**.  
  
2.  V **vlastnosti** okno, nastaveno **typ** vlastnost. Můžete buď z rozevírací nabídky vyberte typ, nebo zadejte nový název.  
  
### <a name="creating-classes-from-lifelines"></a>Vytvoření třídy ze životnosti  
 Po vytvoření jednoho nebo více sekvenčních diagramů lze shrnout životnosti vytvořením třídy nebo rozhraní z nich.  
  
##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Chcete-li vytvořit třídu nebo rozhraní z objektu životnosti  
  
1.  Klikněte pravým tlačítkem na životnost a potom klikněte na tlačítko **vytvořit třídu** nebo **vytvořit rozhraní**.  
  
     Nová třída nebo rozhraní se zobrazí v Průzkumníku modelů UML.  
  
2.  Operace vytvoření třídy nebo rozhraní pro každou zprávu, která přijímá životnost:  
  
    1.  Vyberte všechny zprávy, které chcete zahrnout.  
  
    2.  Klikněte pravým tlačítkem na zprávy a pak klikněte na tlačítko **metodu vytvoření**.  
  
         Nová třída nebo rozhraní obsahuje operace pro každou vybranou zprávu.  
  
         Název operace se zobrazí pod každou zprávu šipku a v **operace** vlastnost zprávy.  
  
         Pokud zprávy zahrnuje parametry ve formě "(parameter: type)", zobrazí se v seznamu parametrů novou operaci.  
  
        > [!NOTE]
        >  Pokud chcete přidat nové zprávy v sekvenčním diagramu je nutné tento krok opakovat.  
  
3.  Chcete-li zobrazit novou třídu nebo rozhraní podrobně, přidejte do diagramu tříd nebo komponenty.  
  
    1.  Otevření nebo vytvoření diagramu tříd nebo komponenty.  
  
    2.  Přetáhněte novou třídu nebo rozhraní z **Průzkumníku modelů UML** do diagramu tříd.  
  
         Třída nebo rozhraní se zobrazí v diagramu tříd.  
  
         \- nebo –  
  
    3.  Přetáhnout rozhraní z **Průzkumníku modelů UML** do komponenty nebo port v diagramu komponent.  
  
         Rozhraní se zobrazí na komponentu jako lollipop.  
  
### <a name="creating-classes-for-parameters"></a>Vytvoření tříd pro parametry  
 Parametry můžete zahrnout zprávy v sekvenčním diagramu. Diagram tříd UML můžete použít k popisu typy parametrů.  
  
##  <a name="Multiple"></a> Vytváření opakovaně použitelných interakce pořadí  
 Samostatné diagram lze použít k popisu sekvenci, která obsahuje podrobnosti, které chcete oddělit, nebo to je obvyklé v rámci několika diagramů.  
  
 Obdélník použitím interakce (12) můžete vytvořit na jednom diagramu, který odkazuje na podrobnosti do jiného diagramu.  
  
 Dvakrát klikněte na panel použitím interakce otevřete sekvenční diagram, který je propojen.  
  
#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Vytvoření opakovaně použitelné interakce pořadí z existující životnosti  
  
1.  V **nástrojů**, klikněte na tlačítko **použitím interakce**.  
  
2.  V sekvenčním diagramu podržte tlačítko myši přetáhněte napříč životnosti, které chcete zahrnout do opakovaně použitelného pořadí. Začínají znakem svislé umístění, kam chcete vložit použitím interakce.  
  
     Použitím interakce se zobrazuje v vybrané životnosti v sekvenčním diagramu.  
  
3.  Dvakrát klikněte na název týkající se použití interakce a přejmenujte ho na popisují vliv opakovaně použitelné pořadí v tomto diagramu.  
  
     \- nebo –  
  
     Vypsání názvu jako volání funkce s parametry.  
  
4.  Propojte s použitím interakce jiného sekvenční diagram. Klikněte pravým tlačítkem na použití interakce a potom buď:  
  
     Klikněte na tlačítko **vytvořit novou sekvenci** vytvořte nový sekvenční diagram  
  
     \- nebo –  
  
     Klikněte na tlačítko **odkaz na pořadí** propojit existující diagramu.  
  
     Visual Studio vytvoří propojení mezi použitím interakce a nové pořadí interakce.  
  
     Nový sekvenční diagram se zobrazí ve vašem řešení. Obsahuje životnosti, které jste použili k vytvoření použitím interakce.  
  
    > [!NOTE]
    >  Pouze životnosti, pro kterou jste použili k vytvoření použitím interakce budou zahrnuty. Nový diagram nebude obsahovat životnosti, které jste vytvořili po interakce použít, i v případě použití interakce je nyní zahrnuje.  
  
#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Vytvoření opakovaně použitelné pořadí z existujících zpráv  
  
-   Klikněte pravým tlačítkem na zprávu, kterou chcete přesunout a potom klikněte na tlačítko **přesunout do diagramu**.  
  
     Visual Studio:  
  
    -   Nahradí interakci použít vybrané zprávy a všechny podpůrné zprávy.  
  
    -   Nahrazené zprávy přesune na nový sekvenční diagram.  
  
    -   Vytvoří propojení mezi použitím interakce a nový sekvenční diagram.  
  
#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Přejít na pořadí odkazuje použitím interakce  
  
-   Dvakrát klikněte na panel použitím interakce.  
  
     \- nebo –  
  
     Klikněte pravým tlačítkem na použití interakce a potom klikněte na tlačítko **přejít na pořadí**.  
  
### <a name="creating-a-placeholder-with-an-interaction-use"></a>Vytváření zástupný symbol se zárukou smlouvy interakce  
 Bez propojení do jiného diagramu můžete vytvořit použitím interakce. Můžete jako zástupný symbol pro součást sekvence jejíž podrobnosti ještě mají být vyřešeny. Použijte název interakce použijte k určení výsledku, který chcete.  
  
##  <a name="Collapse"></a> Sbalení skupin životnosti  
 Sada životnosti můžete sbalit společně, tak, aby daná skupina zobrazovat jako jedna životnost. To vám umožňuje vizualizovat skupiny objektů jako jedinou součást. Zprávy a interakcí mezi životnosti sbalené skupiny jsou skryté. Zprávy a interakce sekvence, které obsahují jiné životností se zobrazí.  
  
#### <a name="to-collapse-a-group-of-lifelines-together"></a>Sbalit skupinu životností se společně  
  
1.  Vyberte dvě nebo více životností.  
  
2.  Klikněte pravým tlačítkem na jeden z nich a potom klikněte na **sbalit**.  
  
     Samostatné životností jsou nahrazeny jednoho životnost.  
  
     Zprávy a interakcí, které se týkají jenom členové skupiny jsou skryté.  
  
3.  Chcete-li přejmenovat skupinu, klikněte na název.  
  
    > [!NOTE]
    >  Název skupiny budou ztraceny, když rozšiřujete skupině.  
  
#### <a name="to-expand-a-collapsed-group"></a>Chcete-li rozbalit sbalené skupiny  
  
-   Klikněte pravým tlačítkem na sbalený životnost a potom klikněte na tlačítko **Rozbalit**.  
  
    > [!NOTE]
    >  Název skupiny se ztratí, společně s odkazy ze skupiny na komentáře nebo pracovní položky.  
  
##  <a name="Fragments"></a> Popis struktury řízení pomocí fragmentů  
 Kombinované fragmenty (13) můžete použít k definování smyčky, větve a souběžné zpracování v sekvenčním diagramu. Případně zvažte místo toho použití diagramu činnosti. Diagram činnosti není tak užitečné zobrazují zpráv mezi objekty actor, ale v některých případech je lepší zobrazují smyčky, větve a souběžnosti.  
  
 Úplný seznam typů fragment, naleznete v tématu [Describe toku řízení pomocí fragmentů v sekvenčních diagramech UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).  
  
#### <a name="to-create-a-combined-fragment"></a>K vytvoření kombinovaného fragmentu  
  
1.  Vyberte zprávu nebo s posloupností zpráv všechno začíná na stejném výskyt provádění nebo životnost.  
  
    > [!NOTE]
    >  Pomocí šipek. zprávy, není výskyty spuštění, přejděte na zprávy.  
  
2.  Klikněte pravým tlačítkem na zprávy, přejděte na **obklopit fragmentem**a potom klikněte na typ fragment, která požadujete.  
  
     Zobrazí se nové fragment. Obsahuje zprávy, které jste vybrali.  
  
     Pokud typ kombinovaného fragmentu umožňuje více fragmentů, zobrazí se také prázdný fragment.  
  
3.  Chcete-li nastavit guard fragment, klikněte pravým tlačítkem myši na okraj fragment a klikněte na **vlastnosti**. Nastavte **Guard** vlastnost.  
  
     Ochranného zařízení se používá k definování podmínku pro větev nebo smyčku.  
  
4.  Přidat nové fragment pro typ, který umožňuje více fragmentů, klikněte pravým tlačítkem na hranici fragment a přejděte na **přidat**. Klikněte na možnost **interakce Operand před** nebo **Operand interakce po**.  
  
5.  Přidat nové zprávy k fragmentům, pomocí nástroje zprávy, nebo zkopírujte a vložte.  
  
## <a name="see-also"></a>Viz také  
 [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)   
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Video: Navrhování interakce s použitím sekvenčních diagramů](http://go.microsoft.com/fwlink/?LinkId=201113)



