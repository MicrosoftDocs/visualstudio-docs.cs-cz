---
title: Vytváření diagramů závislostí z kódu
description: Přečtěte si, jak můžete vytvořit diagram závislosti v aplikaci Visual Studio k vizualizaci logické architektury vysoké úrovně softwarového systému.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b07af93386d5062f28f19f01ce150fba8ec45dd2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389654"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Vytváření diagramů závislostí z kódu

K vizualizaci logické architektury vysoké úrovně softwarového systému vytvořte *diagram závislosti* v aplikaci Visual Studio. Chcete-li zajistit, že váš kód zůstává v souladu s tímto návrhem, ověřte kód pomocí diagramu závislostí. Diagramy závislosti lze vytvořit pro projekty v jazyce Visual C# a Visual Basic. Pokud chcete zjistit, které edice sady Visual Studio podporují tuto funkci, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools).

![Vytvoření diagramu závislostí](../modeling/media/layerdiagramvisualizecode.png)

Diagram závislosti umožňuje organizovat položky řešení sady Visual Studio do logických, abstraktních skupin nazývaných *vrstvy*. Pomocí vrstev můžete popsat hlavní úlohy, které provádějí tyto artefakty, nebo hlavní komponenty systému. Každá vrstva může obsahovat další vrstvy, které popisují podrobnější úlohy. Můžete také zadat zamýšlené nebo existující *závislosti* mezi vrstvami. Tyto závislosti, které jsou reprezentovány šipkami, zobrazují, které vrstvy mohou použít nebo právě používají funkce představované ostatními vrstvami. Chcete-li si udržet architektonickou kontrolu nad kódem, zobrazte zamýšlené závislosti v diagramu a potom ověřte kód proti diagramu.

[Video: ověření závislostí architektury v reálném čase](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="create-a-dependency-diagram"></a><a name="CreateDiagram"></a> Vytvoření diagramu závislostí

Než vytvoříte diagram závislosti, ujistěte se, že vaše řešení obsahuje projekt modelování.

> [!IMPORTANT]
> Nepřidávat, přetahovat ani kopírovat existující diagram závislostí z projektu modelování do jiného projektu modelování nebo na jiné místo v řešení. Tím budou zachovány odkazy z původního diagramu i v případě, že změníte diagram. Rovněž to způsobí, že ověřování vrstev nebude fungovat správně. Důsledkem mohou být i další problémy, jako jsou například chybějící prvky nebo jiné chyby při pokusu o otevření diagramu.
>
> Místo toho přidejte nový diagram závislosti do projektu modelování. Zkopírujte prvky ze zdrojového diagramu do nového diagramu. Uložte projekt modelování i nový Diagram závislostí.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Přidání nového diagramu závislostí do projektu modelování

> [!NOTE]
> Diagramy závislostí pro projekty .NET Core jsou podporovány počínaje verzí Visual Studio 2019 verze 16,2.

1. V nabídce **Architektura** vyberte **nový Diagram závislostí**.

2. V části **šablony** vyberte možnost **Diagram závislostí**.

3. Pojmenujte diagram.

4. V rámci **Přidat do projektu modelování** vyhledejte a vyberte existující projekt modelování ve vašem řešení.

     -nebo-

     Chcete-li přidat nový projekt modelování do řešení, vyberte možnost **vytvořit nový projekt modelování** .

    > [!NOTE]
    > Diagram závislosti musí existovat v rámci projektu modelování. Můžete jej však propojit s položkami kdekoli v řešení.

5. Nezapomeňte uložit projekt modelování i Diagram závislostí.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Přetažení nebo zkopírování a vložení z mapy kódu

1. Vygenerujte mapu kódu pro řešení pomocí nabídky **Architektura** .

2. Zvažte použití filtru mapy kódu pro odebrání složek řešení a "testovací prostředky", pokud chcete vyhovět pouze závislostem v kódu produktu.

3. Na vygenerované mapě kódu odeberte vnější uzel nebo ho rozbalte pro zobrazení externích sestavení v závislosti na tom, zda chcete vynutilit závislosti oboru názvů a odstranit Nepožadovaná sestavení z mapy kódu.

4. Vytvoření nového diagramu závislostí pro řešení pomocí nabídky **Architektura**

5. Vyberte všechny uzly na mapě kódu (pomocí _kombinace kláves CTRL_  +  _a_ použijte výběr pro pružných čar stisknutím klávesy _SHIFT_ a teprve potom klikněte na, přetáhněte a uvolněte.

6. Přetáhněte nebo zkopírujte a vložte vybrané prvky do nového diagramu ověřování závislostí.

7. Tím se zobrazí aktuální architektura aplikace. Rozhodněte, jak má architektura odpovídajícím způsobem upravit diagram závislosti.

![Diagram závislosti generovaný z mapy kódu](media/dependency-validation-01.png)

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a> Vytváření vrstev z artefaktů
 Vrstvy můžete vytvářet z položek řešení sady Visual Studio, jako jsou projekty, soubory kódu, obory názvů, třídy a metody. Tím se automaticky vytvoří spojení mezi vrstvami a položkami, čímž dojde k jejich zahrnutí do procesu ověření vrstev.

 Vrstvy můžete spojovat i s položkami, které ověřování nepodporují, jako například dokumenty aplikace Word nebo prezentace aplikace PowerPoint, takže vrstvu můžete přidružit ke specifikacím nebo plánům. Vrstvy můžete také spojovat se soubory v projektech, které jsou sdíleny napříč více aplikacemi, ale proces ověření nebude zahrnovat ty vrstvy, které se zobrazí s obecnými názvy, například „Vrstva 1“ a „Vrstva 2“.

 Chcete-li zjistit, zda propojená položka podporuje ověřování, otevřete **Průzkumníka vrstev** a Prohlédněte si vlastnost **podporuje ověření** položky. Viz [Správa odkazů na artefakty](#Managing).

|**Do**|**Postupujte podle těchto kroků**.|
|-|-|
|Vytvoření vrstvy pro jeden artefakt|<ol><li>Přetáhněte položku na diagram závislostí z těchto zdrojů:<br /><br /> <ul><li>**Průzkumník řešení**<br /><br />         Přetáhnout můžete například soubory nebo projekty.</li><li>Mapy kódu<br /><br />         Viz [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md) a [použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Zobrazení tříd** nebo **Prohlížeč objektů**</li></ul><br />     Vrstva se zobrazí v diagramu a je propojena s artefaktem.</li><li>Přejmenujte vrstvu tak, aby odrážela odpovědnosti přidruženého kódu nebo artefaktů.</li></ol> **Důležité informace:**  Přetahování binárních souborů do diagramu závislostí nepřidá automaticky své odkazy do projektu modelování. Binární soubory, které chcete ověřit, je třeba ručně přidat do projektu modelování. **Přidání binárních souborů do projektu modelování** <ol><li>V **Průzkumník řešení** otevřete místní nabídku pro projekt modelování a zvolte možnost **Přidat existující položku**.</li><li>V dialogovém okně **Přidat existující položku** vyhledejte binární soubory, vyberte je a pak zvolte **OK**.     Binární soubory se zobrazí v projektu modelování.</li><li>V **Průzkumník řešení** zvolte binární soubor, který jste přidali, a potom stisknutím klávesy **F4** otevřete okno **vlastnosti** .</li><li>V každém binárním souboru nastavte vlastnost **Akce sestavení** na hodnotu **ověřit**.</li></ol>|
|Vytvoření jedné vrstvy pro všechny vybrané artefakty|Přetáhněte všechny artefakty do diagramu závislostí současně.<br /><br /> Vrstva se zobrazí v diagramu a je propojena se všemi artefakty.|
|Vytvoření vrstvy pro každý vybraný artefakt|Stiskněte a podržte klávesu **SHIFT** a přetáhněte všechny artefakty do diagramu závislostí současně. **Poznámka:**  Použijete-li k výběru rozsahu položek klávesu **SHIFT** , po výběru artefaktů uvolněte klíč. Stiskněte a podržte ji znovu, když přetahujete artefakty do diagramu. <br /><br /> Vrstva pro každý artefakt se zobrazí v diagramu a je propojena se všemi artefakty.|
|Přidání artefaktu do vrstvy|Přetáhněte artefakt do vrstvy.|
|Vytvoření nové nepropojené vrstvy|V sadě **nástrojů** rozbalte část **Diagram závislostí** a přetáhněte **vrstvu** do diagramu závislostí.<br /><br /> Chcete-li přidat více vrstev, dvakrát na nástroj klikněte. Po dokončení vyberte nástroj **ukazatel** nebo stiskněte klávesu **ESC** .<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku pro diagram závislosti, zvolte možnost **Přidat** a pak zvolte možnost **vrstva**.|
|Vytvoření vnořených vrstev|Přetáhněte existující vrstvu na jinou vrstvu.<br /><br /> - nebo -<br /><br /> Otevřete místní nabídku pro vrstvu, zvolte možnost **Přidat** a poté vyberte možnost **vrstva**.|
|Vytvoření nové vrstvy, která obsahuje dvě nebo více existujících vrstev|Vyberte vrstvy, otevřete místní nabídku pro svůj výběr a zvolte možnost **Skupina**.|
|Změna barvy vrstvy|Nastavte jeho vlastnost **Color** na barvu, kterou chcete.|
|Zadání toho, aby artefakty spojené s vrstvou nesměly patřit zadanému oboru názvů|Zadejte obory názvů do vlastnosti **zakázané obory názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|
|Zadání toho, aby artefakty spojené s vrstvou nemohly záviset na zadaných oborech názvů|Zadejte obory názvů ve vlastnosti **zakázané závislosti oboru názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|
|Zadání toho, aby artefakty spojené s vrstvou musely patřit jednomu ze zadaných oborů názvů|Zadejte obor názvů do vlastnosti **požadované obory názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|

 Číslo ve vrstvě udává počet artefaktů, které jsou spojeny s vrstvou. Při čtení tohoto čísla však pamatujte na následující skutečnosti:

- Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.

     Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.

- Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.

## <a name="manage-links-between-layers-and-artifacts"></a><a name="Managing"></a> Správa propojení mezi vrstvami a artefakty

1. V diagramu závislostí otevřete místní nabídku pro vrstvu a pak zvolte možnost **Zobrazit odkazy**.

     **Průzkumník vrstev** zobrazuje odkazy artefaktů pro vybranou vrstvu.

2. Ke správě těchto propojení použijte následující úlohy:

|**Do**|**V Průzkumníkovi vrstev**|
|-|-|
|Odstranění propojení mezi vrstvou a artefaktem|Otevřete místní nabídku pro odkaz na artefakt a pak zvolte **Odstranit**.|
|Přesunutí propojení z jedné vrstvy do druhé|Přetáhněte do diagramu propojení artefaktu s existující vrstvou.<br /><br /> - nebo -<br /><br /> 1. Otevřete místní nabídku pro odkaz na artefakt a pak zvolte **Vyjmout**.<br />2. v diagramu závislostí otevřete místní nabídku pro vrstvu a zvolte možnost **Vložit**.|
|Kopírování propojení z jedné vrstvy do druhé|1. Otevřete místní nabídku pro odkaz na artefakt a pak zvolte **Kopírovat**.<br />2. v diagramu závislostí otevřete místní nabídku pro vrstvu a zvolte možnost **Vložit**.|
|Vytvoření nové vrstvy z existujícího propojení artefaktu|Přetáhněte propojení artefaktu do prázdné oblasti na diagramu.|
|Ověřte, zda propojený artefakt podporuje ověřování proti diagramu závislostí.|Podívejte se na sloupec **Podpora ověřování** pro odkaz na artefakt.|

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a> Zpětná analýza existujících závislostí
 Závislost existuje všude, kde artefakt, který je spojen s jednou vrstvou, odkazuje na artefakt, který je přidružen k jiné vrstvě. Třída v jedné vrstvě například deklaruje proměnnou, která má třídu v jiné vrstvě. Je možné provádět zpětnou analýzu existujících závislostí pro artefakty, které jsou propojeny s vrstvami v diagramu.

> [!NOTE]
> Pro určité druhy artefaktů nelze provádět zpětnou analýzu žádných závislostí. Zpětnou analýzou například nebudou získány žádné závislosti z vrstvy nebo do ní, když je propojena s textovým souborem. Chcete-li zjistit, které artefakty mají závislosti, které je možné zpětně analyzovat, otevřete místní nabídku pro jednu nebo více vrstev a pak zvolte možnost **Zobrazit odkazy**. V **Průzkumníku vrstev** Projděte sloupec **Podpora ověřování** . Pro artefakty, pro které tento sloupec zobrazuje **hodnotu false**, nebude možné provádět zpětnou analýzu závislostí.

- Vyberte jednu nebo více vrstev, otevřete místní nabídku pro vybranou vrstvu a pak zvolte možnost **Generovat závislosti**.

  Obvykle se zobrazí nějaké závislosti, které by neměly existovat. Tyto závislosti lze upravit, aby odpovídaly zamýšlenému návrhu.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a> Úprava vrstev a závislostí pro zobrazení zamýšleného návrhu
 Chcete-li popsat změny, které plánujete udělat v systému nebo zamýšlené architektuře, upravte diagram závislosti:

|**Do**|**Proveďte tyto kroky**|
|-|-|
|Změna nebo omezení směru závislosti|Nastavte vlastnost **Direction** .|
|Vytvoření nových závislostí|Použijte nástroje **závislosti** a **obousměrné závislosti** .<br /><br /> Chcete-li nakreslit více závislostí, klikněte na nástroj dvakrát. Po dokončení vyberte nástroj **ukazatel** nebo stiskněte klávesu **ESC** .|
|Zadání toho, aby artefakty spojené s vrstvou nemohly záviset na zadaných oborech názvů|Zadejte obory názvů ve vlastnosti **zakázané závislosti oboru názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|
|Zadání toho, aby artefakty spojené s vrstvou nesměly patřit zadanému oboru názvů|Zadejte obory názvů do vlastnosti **zakázané obory názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|
|Zadání toho, aby artefakty spojené s vrstvou musely patřit jednomu ze zadaných oborů názvů|Zadejte obor názvů do vlastnosti **požadované obory názvů** vrstvy. K oddělení oborů názvů použijte středník (**;**).|

## <a name="change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a> Změna způsobu zobrazení prvků v diagramu
 Velikost, tvar, barvu a polohu vrstev nebo barvu závislostí můžete změnit úpravou jejich vlastností.

## <a name="discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a> Zjišťování vzorů a závislostí na mapě kódu
 Při vytváření diagramů závislostí můžete také vytvořit **mapy kódu**. Tyto diagramy vám mohou při zkoumání kódu pomáhat při vyhledávání vzorů a závislostí. Pomocí Průzkumník řešení, Zobrazení tříd nebo Prohlížeč objektů můžete prozkoumat sestavení, obory názvů a třídy, které často odpovídají existujícím vrstvám. Další informace o mapách kódu naleznete v tématu:

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)

- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)

- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Viz také

- [Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [Video: ověření závislostí architektury v reálném čase](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Diagramy závislostí: Pokyny](../modeling/layer-diagrams-guidelines.md)
- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)
- [Vizualizace kódu](../modeling/visualize-code.md)
