---
title: Mapy kódu
ms.date: 05/16/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 51b03ce504b2fe8f588cf3e360882f97d61664f8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896936"
---
# <a name="map-dependencies-with-code-maps"></a>Mapování závislostí pomocí map kódu

Vytvořením mapy kódu lze vizualizace závislostí ve vašem kódu. Mapy kódu vám umožní zjistit, jak zapadá kód společně bez přečtení soubory a řádky kódu.

![Zobrazení závislostí pomocí map kódu v sadě Visual Studio](../modeling/media/codemapsmainintro.png)

Vytvářet a upravovat map kódu, je třeba Visual Studio Enterprise edition. Ve Visual Studio Community a Professional edice umožňuje otevírat diagramy, které byly vytvořeny v edici Enterprise, ale nemůžete je upravovat.

> [!NOTE]
> Než budete sdílet mapy vytvořené v sadě Visual Studio Enterprise s jinými uživateli, kteří používají Visual Studio Professional, ujistěte se, že se zobrazují všechny položky na mapě (například skryté položky, rozšířené skupiny a odkazy křížové skupiny).

Můžete namapovat závislostí pro kód v těchto jazycích:

- Visual C# nebo Visual Basic v řešení nebo sestavení (*.dll* nebo *.exe*)

- Nativní nebo spravovaný kód C nebo C++ v projektech Visual C++, soubory hlaviček (*.h* nebo `#include`), nebo binární soubory

- Projekty X ++ a sestavení z modulů .NET pro aplikace Microsoft Dynamics AX

> [!NOTE]
> Pro projekty jiné než C# nebo Visual Basic jsou méně možností pro spuštění mapy kódu nebo při přidávání položek do existující mapy kódu. Nelze například klikněte pravým tlačítkem na objekt v textovém editoru projekt jazyka C++ a přidejte ho do mapy kódu. Však můžete přetahujete jednotlivé prvky nebo soubory **Průzkumníka řešení**, **zobrazení tříd**, a **prohlížeče objektů**.

## <a name="install-code-map-and-live-dependency-validation"></a>Mapa kódu instalace a ověření závislostí v reálném čase

K vytvoření mapy kódu v sadě Visual Studio 2017, nejdřív nainstalovat **mapy kódu** a **ověřování závislostí v reálném** komponenty:

1. Otevřít **instalační program sady Visual Studio**. Lze jej otevřít v nabídce Windows Start nebo v rámci sady Visual Studio tak, že vyberete **nástroje** > **stažení nástrojů a funkcí**.

1. Vyberte **jednotlivé komponenty** kartu.

1. Přejděte dolů k položce **kódu nástroje** a vyberte **mapy kódu** a **ověřování závislostí v reálném**.

   ![Mapa kódu a ověřování závislostí v reálném součásti v instalačním programu Visual Studio](media/modeling-components.png)

1. Vyberte **upravit**.

   **Mapy kódu** a **ověřování závislostí v reálném** součásti zahájení instalace. Můžete být vyzváni ukončit sadu Visual Studio.

## <a name="add-a-code-map"></a>Přidat mapu kódu

Můžete vytvořit mapu prázdný kód a přetáhnout položky do jeho, včetně odkazů na sestavení, soubory a složky, nebo můžete Generovat mapu kódu pro všechny nebo část vašeho řešení.

Chcete-li přidat mapu prázdný kód:

1. V **Průzkumníka řešení**, otevřete místní nabídku pro uzel nejvyšší úrovně řešení. Zvolte **přidat** > **nová položka**.

2. V **přidat novou položku** dialogového okna, v části **nainstalováno**, zvolte **Obecné** kategorie.

3. Zvolte **orientovaného grafu Document(.dgml)** šablonu a pak vyberte **přidat**.

   > [!TIP]
   > Tato šablona se nemusí zobrazit abecedně, takže přejděte dolů na konec seznamu šablony, pokud ho nevidíte.

   Prázdné mapování se zobrazí ve vašem řešení **položky řešení** složky.

Podobně můžete vytvořit nový soubor mapy kódu bez jeho přidání do vašeho řešení tak, že vyberete **architektura** > **novou mapu kódu** nebo **souboru**  >  **Nové** > **souboru**.

## <a name="generate-a-code-map-for-your-solution"></a>Generovat mapu kódu pro vaše řešení

Pokud chcete zobrazit všechny závislosti ve vašem řešení:

1. V panelu nabídky zvolte **architektura** > **Generovat mapu kódu pro řešení**. Pokud váš kód nebyl změněn od posledního vytvořená, můžete si vybrat **architektura** > **Generovat mapu kódu pro řešení bez vytváření** místo.

   ![Generování příkazu mapy kódu](../modeling/media/codemapsarchitecturemenu.png)

   Mapování se vygeneruje, který ukazuje sestavení nejvyšší úrovně a souhrnná propojení mezi nimi. Širší agregační odkaz, další závislosti představuje.

2. Použití **legendy** položky kódu (jako jsou třídy, metody a vlastnosti) a typy vztahů (například dědí z tlačítka na panelu nástrojů mapy kódu zobrazit nebo skrýt seznam ikony typu projektu (například testování, webové a projektu Phone), Implementuje a volání).

   ![Graf závislosti nejvyšší úrovně sestavení](../modeling/media/dependencygraph_toplevelassemblies.png)

   Tento příklad řešení obsahuje složky řešení (**testy** a **součásti**), projekty testů, webové projekty a sestavení. Ve výchozím nastavení, zobrazí všechny vztahy členství ve skupině jako *skupiny*, které můžete rozbalit nebo sbalit. **Externích typů** skupina obsahuje všechno mimo řešení, včetně závislostí platformy. Externí sestavení obsahuje pouze položky, které jsou používány. Ve výchozím nastavení jsou na mapě přehlednost skryté systému základní typy.

3. Chcete přejít k podrobnostem do objektu map, rozbalte skupiny, které představují projekty a sestavení. Můžete rozbalit vše, co stisknutím kombinace kláves **CTRL + A** vybrat všechny uzly a poté výběrem **skupiny**, **Rozbalit** z místní nabídky.

   ![Že rozšíření všech skupin v mapě kódu](../modeling/media/codemapsexpandallgroups.png)

4. To však nemusí být užitečná pro velká řešení. Ve skutečnosti pro komplexní řešení, omezení paměti může bránit že rozšíření všech skupin. Místo toho pokud chcete zobrazit uvnitř jednotlivých uzlů, rozbalte ho. Přesuňte ukazatel myši nad uzel a potom klikněte na dvojitou šipku (šipku) jakmile se zobrazí.

   ![Rozbalení uzlu na mapě kódu](../modeling/media/dependencygraph_containment.png)

   Nebo pomocí klávesnice podle pak vyberete požadovanou položku a pak stisknete klávesu plus (**+**). Prozkoumat hlubší úrovně kódu, totéž proveďte pro obory názvů, typy a členy.

   > [!TIP]
   > Další informace o práci s kódem mapuje pomocí myši, klávesnice a dotykového ovládání, naleznete v tématu [Procházet a uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md).

5. Pro zjednodušení mapy a zaměřte se na jednotlivé části, zvolte **filtry** na panelu nástrojů Mapa kódu a vyberte jenom typy uzlů a propojení se zajímáte. Lze například skrýt kontejnery složku řešení a sestavení.

   ![Zjednodušení mapy pomocí filtrování kontejnery](../modeling/media/codemapsfilterfoldersassemblies.png)

   Na mapě můžete také zjednodušit skryjete nebo odebrání jednotlivých skupin a položek z mapy, bez ovlivnění původního kódu řešení.

6. Pokud chcete zobrazit vztahy mezi položkami, vyberte je v objektu map. Barvy odkazy označují typů vztahu, jak je znázorněno **legendy** podokně.

   ![Zobrazení závislostí napříč vaším řešením](../modeling/media/codemapsmainintro.png)

   V tomto příkladu fialové odkazy jsou volání tečkovaná odkazy jsou odkazy a světle modrá odkazy jsou přístup k poli. Zelená může se jednat o dědičnosti, nebo může být *agregovat odkazy* označující více než jeden typ vztahu (nebo *kategorie*).

   > [!TIP]
   > Pokud se zobrazí zelená propojení, nemusí to znamenat, že není právě vztah dědičnosti. Může také být volání metody, ale ty jsou skryta vztah dědičnosti. Pokud chcete zobrazit konkrétní typy odkazů, pomocí zaškrtávacích políček v **filtry** podokně typy nepotřebujete.

7. Pokud chcete získat další informace o položce nebo propojení, přesuňte ukazatel myši dojde k jeho zvýraznění její popisek. Zobrazí podrobnosti o prvek kódu nebo kategorií, které představuje odkaz.

   ![Zobrazení kategorií v relaci](../modeling/media/codemapsshowlinkcatgories.png)

8. Chcete-li zkontrolovat položky závislosti reprezentované souhrnným odkazem, nejprve vyberte odkaz a pak otevřete místní nabídku. Zvolte **zobrazit přispívající vazby** (nebo **zobrazit přispívající vazby na nové mapě kódu**). To rozbalí skupiny na obou koncích spojení a zobrazí pouze položky a závislosti, které se účastní v odkazu.

9. Chcete-li se zaměřit na konkrétní části mapy, můžete nadále odebrat položky, které nepotřebujete. Například zobrazit podrobné informace o zobrazení tříd a členů, jednoduše filtrovat všechny uzly oboru názvů v **filtry** podokně.

   ![Procházení na úrovni tříd a členů](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Dalším způsobem, abyste se mohli zaměřit na mapě komplexní řešení je Generovat mapu s novým obsahující vybrané položky z existujícího mapování. Uložení **Ctrl** při výběru položky, měli byste se zaměřit na, otevřete místní nabídku a zvolte **nový graf z výběru**.

    ![Zobrazit vybrané položky na nové mapě kódu](../modeling/media/codemapsshowonnewmap.png)

11. Obsahující kontext se přenesou na novou mapu. Skrýt složky řešení a všechny kontejnery, které nechcete zjistit, **filtry** podokně.

    ![Filtrovat kontejnery pro zjednodušení zobrazení](../modeling/media/codemapsexpandnewgroups.png)

12. Rozbalit skupiny a vyberte položky v objektu map, chcete-li zobrazit vztahy.

    ![Vyberte položky, které chcete-li zobrazit vztahy](../modeling/media/codemapsviewnewrelationships.png)

Viz také:

- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Vyhledávání potenciálních problémů v kódu podle [spuštěna analyzátor](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Zobrazení konkrétních závislostí na mapě kódu

Předpokládejme, že máte přezkoumání kódu provést některé soubory s probíhající změny. Zobrazení závislostí v tyto změny, můžete vytvořit mapu kódu z těchto souborů.

   ![Zobrazit konkrétní závislosti v mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png)

1. V **Průzkumníka řešení**, vyberte projekty, odkazy na sestavení, složky, soubory, typy nebo členy, které chcete propojit.

   ![Vyberte položky, které chcete propojit](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Na **Průzkumníka řešení** nástrojů, zvolte **zobrazit na mapě kódu** ![vytvořit nový graf z vybrané uzly tlačítko](../modeling/media/createnewgraphfromselectedbutton.gif). Nebo, otevřete místní nabídku pro jeden nebo skupina položek a zvolte **zobrazit na mapě kódu**.

   Můžete také přetáhnout položky z **Průzkumníka řešení**, **zobrazení tříd**, nebo **prohlížeče objektů**, do [nové](#add-a-code-map) nebo mapovat existující kód. Chcete-li zahrnout nadřízenou hierarchii pro vaše položky, stiskněte a podržte **Ctrl** klávesu můžete přetáhnout položky, nebo použít **zahrnout nadřazené položky** tlačítko na panelu nástrojů mapy kódu k určení výchozí akci. Můžete také přetáhnout soubory sestavení z mimo sadu Visual Studio, například z **Windows Explorer**.

   > [!NOTE]
   > Když přidáváte položky z projektu, který je sdílen mezi více aplikacemi, jako jsou Windows Phone nebo Microsoft Store, tyto položky se zobrazí na mapě s aktuálně aktivním projektem aplikace. Pokud změníte kontext na jiný projekt aplikace a přidáte další položky ze sdíleného projektu, tyto položky se nyní zobrazí s nově aktivním projektem aplikace. Operace, které provádíte s položkou na mapě, se vztahují pouze na ty položky, které sdílejí stejný kontext.

3. Mapa zobrazuje vybrané položky v rámci jeho obsahujícího sestavení.

   ![Vybrané položky zobrazené jako skupiny na mapě](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Chcete-li procházet položky, je rozbalte. Přesuňte ukazatel myši nad položku a pak klikněte na ikonu dvojité šipky (šipka) dolů, když se objeví.

   ![Rozbalte uzel na mapě kódu](../modeling/media/dependencygraph_containment.png)

   Chcete-li rozbalit všechny položky, vyberte je pomocí **Ctrl**+**A**, otevřete místní nabídku pro mapy a zvolte **skupiny**  >   **Rozbalte**. Ale tato možnost není k dispozici v případě, že rozšíření všech skupin vytvoří mapu nepoužitelná nebo problémy s pamětí.

5. Rozbalte položky, které vás zajímají, přímo na úrovni třídy a člena v případě potřeby i nadále.

   ![Rozbalit skupiny na úrovni tříd a členů](../modeling/media/codemapsexpandtoclassandmember.png)

   Členové, kteří jsou v kódu, ale nejsou zobrazeny na mapě zobrazíte kliknutím **znovu načíst podřízené** ikonu ![znovu načíst podřízené položky ikonu](../modeling/media/dependencygraph_deletednodesicon.png) v levém horním rohu skupiny.

6. Pokud chcete zobrazit další položky související s nastavením na mapu, vyberte jeden a zvolte **zobrazit související** na panelu nástrojů Mapa kódu, vyberte typ související položky a přidejte do mapy. Můžete také vybrat jednu nebo více položek, otevřete místní nabídku a klikněte na tlačítko **zobrazit** možnost pro typ související položky pro přidání do mapy. Příklad:

    Pro **sestavení**, zvolte možnost:

    |||
    |-|-|
    |**Zobrazit odkazovaná sestavení**|Přidejte sestavení, na které odkazuje toto sestavení. Externí sestavení se zobrazí v **externích typů** skupiny.|
    |**Zobrazit sestavení odkazující se na toto**|Přidejte sestavení do řešení, která odkazují na toto sestavení.|

    Pro **obor názvů**, zvolte **zobrazit obsahující sestavení**, pokud není viditelná.

    Pro **třídy** nebo **rozhraní**, zvolte možnost:

    |||
    |-|-|
    |**Zobrazit základní typy**|V případě třídy přidejte základní třídu a implementovaná rozhraní.<br /><br /> V rámci rozhraní přidejte základní rozhraní.|
    |**Zobrazit odvozené typy**|V případě třídy přidejte odvozené třídy.<br /><br /> V rámci rozhraní přidejte odvozené rozhraní a implementaci tříd nebo struktur.|
    |**Zobrazit odkazované typy**|Přidejte všechny třídy a jejich členy, které tato třída používá.|
    |**Zobrazit typy odkazující se na toto**|Přidejte všechny třídy a jejich členy, které tuto třídu používají.|
    |**Zobrazit obsahující Namespace**|Přidáte nadřazený obor názvů.|
    |**Zobrazit obsahující Namespace a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|
    |**Zobrazit všechny základní typy**|Přidejte rekurzivně hierarchii základní třídy nebo rozhraní.|
    |**Zobrazit všechny odvozené typy**|V případě třídy přidejte všechny odvozené třídy rekurzivně.<br /><br /> V rámci rozhraní přidejte rekurzivně veškerá odvozená rozhraní a implementaci tříd nebo struktur.|

     Pro **metoda**, zvolte možnost:

    |||
    |-|-|
    |**Zobrazit volané metody**|Přidejte metody, které tato metoda volá.|
    |**Ukázat odkazovaná pole**|Přidejte pole, na která odkazuje tato metoda.|
    |**Zobrazit obsahující typ**|Přidáte nadřazeného typu.|
    |**Zobrazit obsahující typ, Namespace a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|
    |**Zobrazit přepsané metody**|V případě metody, která přepíše jiné metody nebo implementuje metodu rozhraní, přidejte všechny abstraktní nebo virtuální metody základních tříd, které jsou přepsány, a případně metodu rozhraní, které je implementováno.|

     Pro **pole** nebo **vlastnost**, zvolte možnost:

    |||
    |-|-|
    |**Zobrazit obsahující typ**|Přidáte nadřazeného typu.|
    |**Zobrazit obsahující typ, Namespace a sestavení**|Přidejte hierarchii nadřazeného kontejneru.|

    ![Zobrazit metody volané tohoto člena](../modeling/media/codemapsshowrelatedmethods.png)

7. Mapa znázorňuje vztahy. V tomto příkladu na mapě ukazuje metody volané `Find` metoda a jejich umístění v řešení nebo externě.

   ![Zobrazit konkrétní závislosti v mapě kódu](../modeling/media/codemapsspecificdependenciesintro.png)

8. Pro zjednodušení mapy a zaměřte se na jednotlivé části, zvolte **filtry** na panelu nástrojů Mapa kódu a vyberte jenom typy uzlů a propojení se zajímáte. Například vypněte zobrazení složek řešení, sestavení a obory názvů.

   ![Pomocí podokna filtru pro zjednodušení zobrazení](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Viz také:

- [Video: porozumění celkové koncepci kódu pomocí map kódu Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)]
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Procházení a změna uspořádání map kódu](../modeling/browse-and-rearrange-code-maps.md)
- [Přizpůsobení map kódu úpravou souborů DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
