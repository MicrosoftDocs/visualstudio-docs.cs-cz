---
title: Vizualizace závislostí pomocí map kódu
description: Zjistěte, jak mapy kódu pomáhají zjistit, jak kód zapadá do sebe bez čtení souborů a řádků kódu.
ms.custom: SEO-VS-2020
ms.date: 05/16/2021
ms.topic: how-to
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d33e3d882d25045802f2c015c88b87b970d9d04e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390434"
---
# <a name="map-dependencies-with-code-maps"></a>Mapování závislostí s mapami kódu

V tomto článku se dozvíte, jak vizualizovat závislosti v kódu pomocí map kódu.

## <a name="what-are-code-maps"></a>Co jsou mapy kódu?

V Visual Studio vám mapy kódu pomůžou rychleji vidět, jak váš programový kód zapadá do sebe bez čtení souborů a řádků kódu.  Pomocí těchto map můžete vidět organizaci a vztahy ve vašem kódu, včetně jeho struktury a závislostí, jak ho aktualizovat a odhadnout náklady na navrhované změny.

![Zobrazení závislostí s mapami kódu v Visual Studio](../modeling/media/codemapsmainintro.png)

Závislosti pro kód můžete mapovat v těchto jazycích:

- Visual C# nebo Visual Basic v řešení nebo sestaveních (*.dll* nebo *.exe*)

- Nativní nebo spravovaný kód C nebo C++ v Visual C++, hlavičkových souborech (*.h* nebo `#include` ) nebo binárních souborech

- Projekty a sestavení X++ z modulů .NET pro Microsoft Dynamics AX

> [!NOTE]
> U jiných projektů než C# nebo Visual Basic existuje méně možností pro spuštění mapy kódu nebo přidání položek do existující mapy kódu. Nemůžete například kliknout pravým tlačítkem myši na objekt v textovém editoru projektu jazyka C++ a přidat ho do mapy kódu. Můžete ale přetáhnout jednotlivé elementy kódu nebo soubory z **Průzkumník řešení,** **Zobrazení tříd** a **Prohlížeče objektů**.

## <a name="prerequisites"></a>Požadavky

Pokud chcete vytvořit mapu kódu v Visual Studio, nejprve nainstalujte komponenty Code Map a [ **Live Dependency Validation.**](install-architecture-tools.md)

K vytváření a úpravám map kódu potřebujete **Visual Studio Enterprise edici**. V edicích Visual Studio Community a Professional však můžete otevřít diagramy vygenerované v edici Enterprise, ale nemůžete je upravovat.

> [!NOTE]
> Před sdílením map vytvořených v Visual Studio Enterprise s ostatními uživateli, kteří používají Visual Studio Professional, se ujistěte, že jsou viditelné všechny položky na mapě (například skryté položky, rozbalené skupiny a propojení mezi skupinami).

## <a name="add-a-code-map"></a>Přidání mapy kódu

Můžete vytvořit prázdnou mapu kódu a přetáhnout do ní položky, včetně odkazů na sestavení, souborů a složek, nebo můžete vygenerovat mapu kódu pro celé řešení nebo jeho část.

Přidání prázdné mapy kódu:

1. V **Průzkumník řešení** otevřete místní nabídku pro uzel řešení nejvyšší úrovně. Zvolte **Přidat**  >  **novou položku.**

2. V dialogovém **okně Přidat novou** položku v části **Nainstalováno** zvolte **kategorii** Obecné.

3. Zvolte šablonu **Directed Graph Document(.dgml)** a pak vyberte **Add (Přidat).**

   > [!TIP]
   > Tato šablona se nemusí zobrazovat v abecedním pořadí, proto se posuňte dolů do dolní části seznamu šablon, pokud ji nevidíte.

   Prázdná mapa se zobrazí ve složce Položky **řešení vašeho** řešení.

Podobně můžete vytvořit nový soubor mapy kódu bez jeho přidání do řešení tak, že vyberete **Architektura** Nová mapa kódu  >   nebo **Soubor**  >  **Nový**  >  **soubor**.

Další informace:
- [Sdílení map kódu](share-code-maps.md)
- [Vytvoření map kódu pro C++](code-maps-for-cpp.md)
- [Vylepšení výkonu map kódu](code-maps-performance.md)

## <a name="generate-a-code-map-for-your-solution"></a>Vygenerování mapy kódu pro vaše řešení

Zobrazení všech závislostí v řešení:

1. V řádku nabídek zvolte Architektura  >  **Generovat mapu kódu pro řešení.** Pokud se váš kód od posledního sestavení nezměnil, můžete místo toho vybrat **Architecture** Generate Code Map for Solution Without Building (Vygenerovat mapu kódu architektury pro řešení bez  >   sestavení).

   ![Vygenerování příkazu mapy kódu](../modeling/media/codemapsarchitecturemenu.png)

   Vygeneruje se mapa, která zobrazuje sestavení nejvyšší úrovně a agregovaná propojení mezi nimi. Čím širší agregační propojení, tím více závislostí představuje.

2. Pomocí tlačítka **Legenda** na panelu nástrojů mapy kódu můžete zobrazit nebo skrýt seznam ikon typu projektu (například Test, Web a Phone Project), položky kódu (například třídy, metody a vlastnosti) a typy relací (například Dědí z, Implementuje a Volání).

   ![Graf závislostí nejvyšší úrovně sestavení](../modeling/media/dependencygraph_toplevelassemblies.png)

   Toto příklad řešení obsahuje složky řešení (**testy a** **komponenty**), projekty testů, webové projekty a sestavení. Ve výchozím nastavení se všechny vztahy sbalení zobrazují jako *skupiny*, které můžete rozbalit a sbalit. Skupina **Externals** obsahuje cokoli mimo vaše řešení, včetně závislostí platformy. Externí sestavení obsahuje pouze položky, které jsou používány. Ve výchozím nastavení jsou základní typy systému na mapě skryté, aby se snížil počet nepotř počtů.

3. Chcete-li přejít k podrobnostem mapy, rozbalte skupiny, které představují projekty a sestavení. Vše můžete rozbalit stisknutím **kombinace kláves CTRL + A,** abyste  vybrali všechny uzly, a pak v místní nabídce zvolíte Skupina **,** Rozbalit.

   ![Rozbalení všech skupin v mapě kódu](../modeling/media/codemapsexpandallgroups.png)

4. To ale nemusí být užitečné pro velké řešení. Ve skutečnosti platí, že u složitých řešení vám omezení paměti bránit v rozbalení všech skupin. Místo toho ho rozbalte, abyste ho viděli uvnitř jednotlivého uzlu. Přesuňte ukazatel myši nad uzel a jakmile se zobrazí, klikněte na šipku dolů.

   ![Rozbalení uzlu v mapě kódu](../modeling/media/dependencygraph_containment.png)

   Nebo použijte klávesnici tak, že položku vyberete a pak stisknete klávesu plus ( **+** ). Pokud chcete prozkoumat hlubší úrovně kódu, proveďte totéž pro obory názvů, typy a členy.

   > [!TIP]
   > Další podrobnosti o práci s mapami kódu pomocí myši, klávesnice a dotykového ovládání najdete v tématu Procházení a [změna uspořádání map kódu.](../modeling/browse-and-rearrange-code-maps.md)

5. Pro zjednodušení mapy a zaměření  na jednotlivé části zvolte Filtry na panelu nástrojů mapy kódu a vyberte pouze typy uzlů a odkazů, které vás zajímají. Můžete například skrýt všechny kontejnery Složka řešení a Sestavení.

   ![Zjednodušení mapy filtrováním kontejnerů](../modeling/media/codemapsfilterfoldersassemblies.png)

   Mapu můžete také zjednodušit skrytím nebo odebráním jednotlivých skupin a položek z mapy, aniž by to ovlivnilo základní kód řešení.

6. Pokud chcete zobrazit relace mezi položkami, vyberte je na mapě. Barvy odkazů označují typy relace, jak je znázorněno v **podokně Legenda.**

   ![Zobrazení závislostí napříč řešeními](../modeling/media/codemapsmainintro.png)

   V tomto příkladu jsou fialová propojení volání, tečkované odkazy jsou odkazy a světle modré odkazy jsou přístup k poli. Zelené odkazy mohou být dědičnost nebo mohou být agregační propojení, *která* označují více než jeden typ relace (nebo *kategorii*).

   > [!TIP]
   > Pokud se zobrazí zelený odkaz, nemusí to znamenat, že existuje pouze vztah dědičnosti. Mohou také být volání metod, ale tato volání jsou skrytá vztahem dědičnosti. Pokud chcete zobrazit konkrétní typy odkazů, pomocí zaškrtávacích políček v **podokně Filtry** skryjte typy, které vás zajímají.

7. Pokud chcete získat další informace o položce nebo odkazu, přesuňte ukazatel nad položku, dokud se nezobrazí popis. Zobrazí se podrobnosti o elementu kódu nebo kategoriích, které odkaz představuje.

   ![Zobrazení kategorií relace](../modeling/media/codemapsshowlinkcatgories.png)

8. Pokud chcete prozkoumat položky a závislosti reprezentované agregačním odkazem, vyberte odkaz a pak otevřete jeho místní nabídku. Zvolte **Show Contributing Links** (Zobrazit odkazy pro přispívání) (nebo **Show Contributing Links on New Code Map**(Zobrazit odkazy pro přispívání na novou mapu kódu). Tím se rozbalí skupiny na obou koncích odkazu a zobrazí se pouze položky a závislosti, které jsou součástí odkazu.

9. Pokud se chcete zaměřit na konkrétní části mapy, můžete pokračovat v odebírání položek, které vás zajímají. Pokud například chcete přejít k podrobnostem v zobrazení třídy a člena, jednoduše vyfiltrujte všechny uzly oboru názvů v **podokně Filtry.**

   ![Rozbalování na úrovni třídy a člena](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Dalším způsobem, jak se zaměřit na komplexní mapu řešení, je vygenerovat novou mapu obsahující vybrané položky z existující mapy. Podržte **klávesu Ctrl** a vyberte položky, na které se chcete zaměřit, otevřete místní nabídku a v nabídce Výběr zvolte **Nový graf.**

    ![Zobrazení vybraných položek na nové mapě kódu](../modeling/media/codemapsshowonnewmap.png)

11. Objekt obsahující kontext se přenést do nové mapy. Pomocí podokna Filtry skryjte Složky řešení a všechny ostatní **kontejnery, které nechcete** zobrazit.

    ![Filtrování kontejnerů pro zjednodušení zobrazení](../modeling/media/codemapsexpandnewgroups.png)

12. Rozbalte skupiny a výběrem položek na mapě zobrazte relace.

    ![Výběr položek pro zobrazení relací](../modeling/media/codemapsviewnewrelationships.png)

Další zdroje informací:

- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Vyhledání potenciálních problémů v kódu spuštěním [analyzátoru](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-dependencies"></a>Zobrazení závislostí

Předpokládejme, že máte revize kódu, která se má provést v některých souborech s čekajícími změnami. Pokud chcete zobrazit závislosti v těchto změnách, můžete z těchto souborů vytvořit mapu kódu.

   ![Zobrazení konkrétních závislostí na mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png)

1. V **Průzkumník řešení** vyberte projekty, odkazy na sestavení, složky, soubory, typy nebo členy, které chcete mapovat.

   ![Vyberte položky, které chcete mapovat.](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Na panelu **Průzkumník řešení** vyberte **Zobrazit** na mapě kódu Tlačítko Vytvořit nový graf z ![ vybraných ](../modeling/media/createnewgraphfromselectedbutton.gif) uzlů. Nebo otevřete místní nabídku pro jednu nebo skupinu položek a zvolte **Zobrazit na mapě kódu**.

   Můžete také přetáhnout položky **z Průzkumník řešení**, **Zobrazení tříd**, nebo **Object Browser** do nové [nebo](#add-a-code-map) existující mapy kódu. Pokud chcete zahrnout nadřazenou hierarchii položek, stiskněte a podržte  klávesu **Ctrl** při přetahování položek nebo pomocí tlačítka Zahrnout nadřazené prvky na panelu nástrojů mapy kódu určete výchozí akci. Můžete také přetáhnout soubory sestavení z Visual Studio, například z **Průzkumník Windows**.

   > [!NOTE]
   > Když přidáte položky z projektu, který je sdílený mezi více aplikacemi, jako je Windows Phone nebo Microsoft Store, zobrazí se tyto položky na mapě s aktuálně aktivním projektem aplikace. Pokud změníte kontext na jiný projekt aplikace a přidáte další položky ze sdíleného projektu, tyto položky se nyní zobrazí s nově aktivním projektem aplikace. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.

3. Mapa zobrazuje vybrané položky v rámci jejich obsahujících sestavení.

   ![Vybrané položky zobrazené jako skupiny na mapě](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Pokud chcete prozkoumat položky, rozbalte je. Přesuňte ukazatel myši nad položku a po zobrazení klikněte na ikonu šipky dolů.

   ![Rozbalení uzlu v mapě kódu](../modeling/media/dependencygraph_containment.png)

   Pokud chcete rozbalit všechny položky, vyberte je pomocí **Ctrl** A, otevřete místní nabídku mapy a + zvolte **Rozbalit**  >  **skupinu.** Tato možnost ale není dostupná, pokud rozbalení všech skupin vytvoří nepoužitelné problémy s mapou nebo pamětí.

5. Pokračujte v rozbalování položek, které vás zajímají, přímo dolů na úroveň třídy a členu, pokud je to potřeba.

   ![Rozbalení skupin na úroveň třídy a člena](../modeling/media/codemapsexpandtoclassandmember.png)

   Pokud chcete zobrazit členy, kteří jsou v kódu, ale  nezobrazují se na mapě, klikněte v levém horním rohu skupiny na ikonu Znovu načtou děti Ikona Znovu načtou ![ ](../modeling/media/dependencygraph_deletednodesicon.png) děti.

6. Pokud chcete zobrazit další položky související s těmi, které jsou na mapě, vyberte jednu položku a na panelu nástrojů mapy kódu zvolte Zobrazit související a pak vyberte typ souvisejících položek, které chcete do mapy přidat.  Můžete také vybrat jednu nebo více položek, otevřít  místní nabídku a pak zvolit možnost Zobrazit pro typ souvisejících položek, které se přidávají do mapy. Příklad:

    Pro **sestavení zvolte:**

    |Možnost|Popis|
    |-|-|
    |**Zobrazit sestavení – tyto odkazy**|Přidejte sestavení, na které odkazuje toto sestavení. Externí sestavení se zobrazí ve **skupině Externí.**|
    |**Zobrazit sestavení odkazující na tuto**|Přidejte sestavení do řešení, která odkazují na toto sestavení.|

    Pokud obor **názvů** není **viditelný,** zvolte Zobrazit obsahující sestavení .

    Pro **třídu nebo** **rozhraní** zvolte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazení základních typů**|V případě třídy přidejte základní třídu a implementovaná rozhraní.<br /><br /> V rámci rozhraní přidejte základní rozhraní.|
    |**Zobrazení odvozených typů**|V případě třídy přidejte odvozené třídy.<br /><br /> V rámci rozhraní přidejte odvozené rozhraní a implementaci tříd nebo struktur.|
    |**Show Types This References**|Přidejte všechny třídy a jejich členy, které tato třída používá.|
    |**Zobrazit typy odkazující na tuto**|Přidejte všechny třídy a jejich členy, které tuto třídu používají.|
    |**Zobrazit obsahující obor názvů**|Přidejte nadřazený obor názvů.|
    |**Zobrazit obsahující obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|
    |**Zobrazit všechny základní typy**|Přidejte rekurzivně hierarchii základní třídy nebo rozhraní.|
    |**Zobrazit všechny odvozené typy**|V případě třídy přidejte všechny odvozené třídy rekurzivně.<br /><br /> V rámci rozhraní přidejte rekurzivně veškerá odvozená rozhraní a implementaci tříd nebo struktur.|

     Pro **metodu** zvolte:

    |Možnost|Popis|
    |-|-|
    |**Show – metody, které tato volání**|Přidejte metody, které tato metoda volá.|
    |**Show Fields This References**|Přidejte pole, na která odkazuje tato metoda.|
    |**Zobrazit obsahující typ**|Přidejte nadřazený typ.|
    |**Zobrazit obsahující typ, obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|
    |**Zobrazení přepsané metody**|V případě metody, která přepíše jiné metody nebo implementuje metodu rozhraní, přidejte všechny abstraktní nebo virtuální metody základních tříd, které jsou přepsány, a případně metodu rozhraní, které je implementováno.|

     U pole **nebo** **vlastnosti** zvolte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit obsahující typ**|Přidejte nadřazený typ.|
    |**Zobrazit obsahující typ, obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|

    ![Show methods called by this member](../modeling/media/codemapsshowrelatedmethods.png)

7. Na mapě se zobrazí relace. V tomto příkladu mapa zobrazuje metody vvané metodou a jejich umístění v řešení `Find` nebo externě.

   ![Zobrazení konkrétních závislostí na mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png)

8. Pro zjednodušení mapy a zaměření  na jednotlivé části zvolte Filtry na panelu nástrojů mapy kódu a vyberte pouze typy uzlů a odkazů, které vás zajímají. Můžete například vypnout zobrazení složek řešení, sestavení a oborů názvů.

   ![Zjednodušení zobrazení pomocí podokna Filtr](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Viz také

- [Sdílení map kódu](share-code-maps.md)
- [Vytvoření map kódu pro C++](code-maps-for-cpp.md)
- [Vylepšení výkonu map kódu](code-maps-performance.md)
- [Video: Principy návrhu z kódu s mapami Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Video: Principy návrhu z kódu s mapami Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
