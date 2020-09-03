---
title: Mapy kódu
ms.date: 05/16/2018
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 771a6ccf4749a3464204d3da75f4d403d1ab2dd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532714"
---
# <a name="map-dependencies-with-code-maps"></a>Mapování závislostí pomocí map kódu

Můžete vizualizovat závislosti v kódu vytvořením mapy kódu. Mapy kódu vám pomůžou zjistit, jak se kód vejde dohromady bez čtení souborů a řádků kódu.

![Zobrazení závislostí s mapami kódu v aplikaci Visual Studio](../modeling/media/codemapsmainintro.png)

Chcete-li vytvářet a upravovat mapy kódu, potřebujete Visual Studio Enterprise edici. V edicích Visual Studio Community a Professional můžete otevřít diagramy vygenerované v Enterprise Edition, ale nemůžete je upravovat.

> [!NOTE]
> Před sdílením map vytvořených v Visual Studio Enterprise s jinými uživateli, kteří používají Visual Studio Professional, se ujistěte, že jsou viditelné všechny položky na mapě (například skryté položky, rozšířené skupiny a odkazy křížové skupiny).

Závislosti pro kód můžete mapovat v těchto jazycích:

- Visual C# nebo Visual Basic v řešení nebo sestaveních (*. dll* nebo *. exe*)

- Nativní nebo spravovaný kód jazyka C nebo C++ v Visual C++ projekty, soubory hlaviček (*. h* nebo `#include` ) nebo binární soubory

- Projekty X + + a sestavení vytvořená z modulů .NET pro Microsoft Dynamics AX

> [!NOTE]
> Pro jiné projekty než C# nebo Visual Basic je k dispozici méně možností pro spuštění mapy kódu nebo přidávání položek do existující mapy kódu. Například nelze kliknout pravým tlačítkem myši na objekt v textovém editoru projektu jazyka C++ a přidat jej do mapy kódu. Jednotlivé prvky nebo soubory kódu však lze přetáhnout z **Průzkumník řešení**, **zobrazení tříd**a **Prohlížeč objektů**.

## <a name="install-code-map-and-live-dependency-validation"></a>Instalovat mapu kódu a ověřování živých závislostí

Chcete-li vytvořit mapu kódu v aplikaci Visual Studio, nejprve nainstalujte **mapu kódu** a komponenty **ověřování živé závislosti** :

1. Otevřete **instalační program pro Visual Studio**. Můžete ji otevřít z nabídky Start v systému Windows nebo v sadě Visual Studio tak, že vyberete **nástroje**  >  **získat nástroje a funkce**.

1. Vyberte kartu **jednotlivé součásti** .

1. Přejděte dolů k části **nástroje kódu** a vyberte **Mapa kódu** a **ověření živé závislosti**.

   ![Mapa kódu a komponenty ověřování živé závislosti v Instalační program pro Visual Studio](media/modeling-components.png)

1. Vyberte **Upravit**.

   Na **mapě kódu** a komponentách **ověřování živé závislosti** se zahájí instalace. Může se zobrazit výzva k zavření sady Visual Studio.

## <a name="add-a-code-map"></a>Přidat mapu kódu

Můžete vytvořit prázdnou mapu kódu a přetáhnout položky do ní, včetně odkazů na sestavení, souborů a složek, nebo můžete vygenerovat mapu kódu pro vše nebo část vašeho řešení.

Přidání prázdné mapy kódu:

1. V **Průzkumník řešení**otevřete místní nabídku uzlu řešení nejvyšší úrovně. Vyberte možnost **Přidat**  >  **novou položku**.

2. V dialogovém okně **Přidat novou položku** vyberte v části **nainstalováno**kategorii **Obecné** .

3. Zvolte šablonu **dokument orientovaného grafu (. dgml)** a pak vyberte **Přidat**.

   > [!TIP]
   > Tato šablona se nemůže zobrazit abecedně, takže se posuňte dolů k dolní části seznamu šablon, pokud ji nevidíte.

   Ve složce **položky řešení** vašeho řešení se zobrazí prázdná mapa.

Podobně můžete vytvořit nový soubor s mapou kódu, aniž byste ho přidali do vašeho řešení, a to tak, že vyberete **Architektura**  >  **Nová mapa kódu** nebo **soubor**  >  **Nový**  >  **soubor**.

## <a name="generate-a-code-map-for-your-solution"></a>Generovat mapu kódu pro vaše řešení

Chcete-li zobrazit všechny závislosti ve vašem řešení:

1. Na panelu nabídek vyberte možnost **Architektura**  >  **Generovat mapu kódu pro řešení**. Pokud se váš kód od posledního sestavení nezměnil, můžete vybrat **architekturu**  >  **Generovat mapu kódu pro řešení bez nutnosti vytvářet** místo.

   ![Vytvoření mapy kódu – příkaz](../modeling/media/codemapsarchitecturemenu.png)

   Vygeneruje se mapa, která zobrazuje sestavení nejvyšší úrovně a agregované odkazy mezi nimi. Širší agregovaný odkaz, který představuje více závislostí.

2. Použijte tlačítko **Legenda** na panelu nástrojů mapa kódu k zobrazení nebo skrytí seznamu ikon typu projektu (například testovací, webové a telefonní projekty), položek kódu (například tříd, metod a vlastností) a typů vztahů (například dědění z, Implements a Calls).

   ![Graf závislosti nejvyšší úrovně sestavení](../modeling/media/dependencygraph_toplevelassemblies.png)

   Tento příklad řešení obsahuje složky řešení (**testy** a **komponenty**), projekty testů, webové projekty a sestavení. Ve výchozím nastavení se všechny vztahy zahrnutí zobrazí jako *skupiny*, které můžete rozbalit nebo sbalit. Skupina **externals** obsahuje cokoli mimo vaše řešení, včetně závislostí platformy. Externí sestavení obsahuje pouze položky, které jsou používány. Ve výchozím nastavení jsou systémové základní typy na mapě skryté, aby se snížila přehlednost.

3. Chcete-li přejít k podrobnostem o mapě, rozbalte skupiny, které reprezentují projekty a sestavení. Můžete rozbalit vše stisknutím **kombinace kláves CTRL + a** a vybrat všechny uzly a pak vybrat **skupinu**a **Rozbalit** z místní nabídky.

   ![Rozbalování všech skupin v mapě kódu](../modeling/media/codemapsexpandallgroups.png)

4. To však nemusí být užitečné pro velké řešení. V případě složitých řešení vám možná omezení paměti brání v rozšiřování všech skupin. Místo toho, abyste viděli v rámci jednotlivého uzlu, rozbalte ho. Přesuňte ukazatel myši nad uzel a pak klikněte na dvojitou šipku (šipka dolů), když se objeví.

   ![Rozbalení uzlu v mapě kódu](../modeling/media/dependencygraph_containment.png)

   Nebo použijte klávesnici tak, že vyberete položku a stisknete klávesu plus ( **+** ). Chcete-li prozkoumat hlubší úrovně kódu, proveďte stejný pro obory názvů, typy a členy.

   > [!TIP]
   > Další informace o práci s mapami kódu pomocí myši, klávesnice a dotykového ovládání najdete v tématu [procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

5. Chcete-li zjednodušit mapu a soustředit se na jednotlivé části, zvolte možnost **filtry** na panelu nástrojů mapa kódu a vyberte pouze typy uzlů a odkazy, které vás zajímají. Můžete například skrýt všechny složky řešení a kontejnery sestavení.

   ![Zjednodušení mapy filtrováním kontejnerů](../modeling/media/codemapsfilterfoldersassemblies.png)

   Mapu můžete také zjednodušit skrytím nebo odebráním jednotlivých skupin a položek z mapy, aniž by to ovlivnilo základní kód řešení.

6. Chcete-li zobrazit vztahy mezi položkami, vyberte je na mapě. Barvy odkazů označují typy vztahů, jak je znázorněno v podokně **Legenda** .

   ![Zobrazení závislostí napříč vaším řešením](../modeling/media/codemapsmainintro.png)

   V tomto příkladu fialové odkazy jsou voláním, tečkované odkazy jsou odkazy a světle modré odkazy jsou přístup k poli. Zelené odkazy mohou být děděny nebo mohou být *agregované odkazy* , které označují více než jeden typ vztahu (nebo *kategorie*).

   > [!TIP]
   > Pokud vidíte zelený odkaz, nemusí to znamenat pouze vztah dědičnosti. Může to být také volání metody, ale vztah dědičnosti je skrytý. Chcete-li zobrazit konkrétní typy odkazů, můžete pomocí zaškrtávacích políček v podokně **filtry** skrýt typy, které vás zajímají.

7. Chcete-li získat další informace o položce nebo propojení, přesuňte ukazatel nad něj, dokud se nezobrazí popisek. To ukazuje podrobnosti prvku kódu nebo kategorií, které odkaz představuje.

   ![Zobrazit kategorie vztahu](../modeling/media/codemapsshowlinkcatgories.png)

8. Chcete-li prošetřit položky a závislosti reprezentované agregovaným odkazem, nejprve vyberte odkaz a pak otevřete místní nabídku. Vyberte **Zobrazit přispívající odkazy** (nebo **Zobrazit přispívající odkazy na nové mapě kódu**). Tím se rozbalí skupiny na obou koncích propojení a zobrazí se jenom položky a závislosti, které se účastní odkazu.

9. Pokud se chcete zaměřit na konkrétní části mapy, můžete i nadále odebírat položky, které vás zajímají. Chcete-li například přejít k zobrazení tříd a členů, jednoduše vyfiltrujte všechny uzly oboru názvů v podokně **filtry** .

   ![Přechod na úroveň třídy a člena](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Dalším způsobem, jak se zaměřit na složitou mapu řešení, je vytvoření nové mapy obsahující vybrané položky z existující mapy. Podržte stisknutou **klávesu CTRL** a vyberte položky, na kterých se chcete zaměřit, otevřete místní nabídku a zvolte možnost **Nový graf z výběru**.

    ![Zobrazit vybrané položky na nové mapě kódu](../modeling/media/codemapsshowonnewmap.png)

11. Obsažený kontext je převedený na novou mapu. Pomocí podokna **filtry** skryjte složky řešení a další kontejnery, které nechcete zobrazit.

    ![Filtrování kontejnerů pro zjednodušení zobrazení](../modeling/media/codemapsexpandnewgroups.png)

12. Rozbalením skupin a výběrem položek v mapě zobrazíte relace.

    ![Vyberte položky pro zobrazení vztahů](../modeling/media/codemapsviewnewrelationships.png)

Další zdroje informací:

- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Hledání potenciálních problémů v kódu [spuštěním analyzátoru](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Zobrazit konkrétní závislosti v mapě kódu

Předpokládejme, že máte revizi kódu, který se má provést v některých souborech s probíhajícími změnami. Chcete-li zobrazit závislosti v těchto změnách, můžete z těchto souborů vytvořit mapu kódu.

   ![Zobrazit konkrétní závislosti na mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png)

1. V **Průzkumník řešení**vyberte projekty, odkazy na sestavení, složky, soubory, typy nebo členy, které chcete namapovat.

   ![Vyberte položky, které chcete namapovat.](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Na panelu nástrojů **Průzkumník řešení** klikněte na tlačítko **Zobrazit na mapě kódu** ![ vytvořit nový graf z vybraných uzlů ](../modeling/media/createnewgraphfromselectedbutton.gif) . Případně můžete otevřít místní nabídku pro jednu nebo skupinu položek a zvolit **Zobrazit na mapě kódu**.

   Můžete také přetáhnout položky z **Průzkumník řešení**, **zobrazení tříd**nebo **Prohlížeč objektů**do [nové](#add-a-code-map) nebo existující mapy kódu. Chcete-li zahrnout nadřazenou hierarchii pro vaše položky, stiskněte a podržte klávesu **CTRL** při přetahování položek nebo použijte tlačítko **Zahrnout nadřazené** položky na panelu nástrojů mapa kódu a určete výchozí akci. Soubory sestavení můžete také přetáhnout mimo aplikaci Visual Studio, například z **Průzkumníka Windows**.

   > [!NOTE]
   > Při přidávání položek z projektu, který je sdílen mezi více aplikacemi, například Windows Phone nebo Microsoft Store, se tyto položky zobrazí na mapě s aktuálně aktivním projektem aplikace. Pokud změníte kontext na jiný projekt aplikace a přidáte další položky ze sdíleného projektu, tyto položky se nyní zobrazí s nově aktivním projektem aplikace. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.

3. Mapa zobrazuje vybrané položky v rámci jejich obsahující sestavení.

   ![Vybrané položky zobrazené jako skupiny na mapě](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Chcete-li prozkoumat položky, rozbalte je. Přesuňte ukazatel myši nad položku a potom po zobrazení klikněte na ikonu s dvojitou šipkou (šipka dolů).

   ![Rozbalení uzlu v mapě kódu](../modeling/media/dependencygraph_containment.png)

   Chcete-li rozbalit všechny položky, vyberte je pomocí **kombinace kláves CTRL** + **a**, pak otevřete místní nabídku pro mapu a zvolte možnost **Skupina**  >  **Rozbalit**. Tato možnost není k dispozici, pokud rozšíření všech skupin vytvoří nepoužitou mapu nebo problémy s pamětí.

5. V případě potřeby dál Rozšiřte položky, které vás zajímají, na úrovni třídy a člena.

   ![Rozbalení skupin na úrovni třídy a člena](../modeling/media/codemapsexpandtoclassandmember.png)

   Chcete-li zobrazit členy, kteří jsou v kódu, ale nezobrazují se na mapě, klikněte na ikonu znovu **načíst podřízené** položky ![ ](../modeling/media/dependencygraph_deletednodesicon.png) v levém horním rohu skupiny.

6. Chcete-li zobrazit další položky týkající se těch na mapě, vyberte je a zvolte možnost **Zobrazit související** na panelu nástrojů mapa kódu a pak vyberte typ souvisejících položek, které chcete přidat do mapy. Případně vyberte jednu nebo více položek, otevřete místní nabídku a zvolte možnost **Zobrazit** pro typ souvisejících položek, které chcete přidat do mapy. Příklad:

    V případě **sestavení**vyberte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit sestavení s odkazy**|Přidejte sestavení, na které odkazuje toto sestavení. Externí sestavení se zobrazí ve skupině **externí** typy.|
    |**Zobrazit sestavení odkazující na tuto**|Přidejte sestavení do řešení, která odkazují na toto sestavení.|

    V případě **oboru názvů**vyberte možnost **Zobrazit obsahující sestavení**, pokud není viditelná.

    Pro **třídu** nebo **rozhraní**vyberte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit základní typy**|V případě třídy přidejte základní třídu a implementovaná rozhraní.<br /><br /> V rámci rozhraní přidejte základní rozhraní.|
    |**Zobrazit odvozené typy**|V případě třídy přidejte odvozené třídy.<br /><br /> V rámci rozhraní přidejte odvozené rozhraní a implementaci tříd nebo struktur.|
    |**Zobrazit typy těchto odkazů**|Přidejte všechny třídy a jejich členy, které tato třída používá.|
    |**Zobrazit typy odkazující na tuto**|Přidejte všechny třídy a jejich členy, které tuto třídu používají.|
    |**Zobrazit obsahující obor názvů**|Přidejte nadřazený obor názvů.|
    |**Zobrazit obsahující obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|
    |**Zobrazit všechny základní typy**|Přidejte rekurzivně hierarchii základní třídy nebo rozhraní.|
    |**Zobrazit všechny odvozené typy**|V případě třídy přidejte všechny odvozené třídy rekurzivně.<br /><br /> V rámci rozhraní přidejte rekurzivně veškerá odvozená rozhraní a implementaci tříd nebo struktur.|

     Pro **metodu**vyberte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit metody tato volání**|Přidejte metody, které tato metoda volá.|
    |**Zobrazit pole s odkazy**|Přidejte pole, na která odkazuje tato metoda.|
    |**Zobrazit obsahující typ**|Přidejte nadřazený typ.|
    |**Zobrazit obsahující typ, obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|
    |**Zobrazit přepsané metody**|V případě metody, která přepíše jiné metody nebo implementuje metodu rozhraní, přidejte všechny abstraktní nebo virtuální metody základních tříd, které jsou přepsány, a případně metodu rozhraní, které je implementováno.|

     Pro **pole** nebo **vlastnost**vyberte:

    |Možnost|Popis|
    |-|-|
    |**Zobrazit obsahující typ**|Přidejte nadřazený typ.|
    |**Zobrazit obsahující typ, obor názvů a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|

    ![Zobrazit metody volané tímto členem](../modeling/media/codemapsshowrelatedmethods.png)

7. Mapa zobrazuje vztahy. V tomto příkladu Mapa zobrazuje metody volané `Find` metodou a jejich umístění v řešení nebo externě.

   ![Zobrazit konkrétní závislosti na mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png)

8. Chcete-li zjednodušit mapu a soustředit se na jednotlivé části, zvolte možnost **filtry** na panelu nástrojů mapa kódu a vyberte pouze typy uzlů a odkazy, které vás zajímají. Například vypněte zobrazení složek řešení, sestavení a oborů názvů.

   ![Zjednodušení zobrazení pomocí podokna filtru](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Viz také

- [Video: Principy návrhu z kódu pomocí map kódu Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
