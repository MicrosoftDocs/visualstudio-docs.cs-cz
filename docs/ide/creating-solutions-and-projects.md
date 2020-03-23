---
title: Vytváření řešení a projektů
ms.date: 02/06/2018
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 503b343299f7b30e9f5e834099274215b262a635
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301816"
---
# <a name="create-solutions-and-projects"></a>Vytváření řešení a projektů

*Projekty* uchovávají položky potřebné k vytvoření aplikace v sadě Visual Studio, jako jsou soubory zdrojového kódu, bitmapy, ikony a odkazy na komponenty a služby. Při vytváření nového projektu visual studio vytvoří *řešení* obsahující projekt. Potom můžete přidat další nové nebo existující projekty do řešení, pokud chcete. Řešení mohou také obsahovat soubory, které nejsou připojeny k žádnému konkrétnímu projektu.

![Hierarchie řešení/projektu](./media/vside-proj-soln.png)

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Vytváření projektů ve Visual Studiu pro Mac](/visualstudio/mac/create-new-projects).

Řešení a projekty můžete zobrazit v okně nástroje s názvem **Průzkumník řešení**. Následující snímek obrazovky ukazuje ukázkové řešení v **Průzkumníku řešení** (**BikeSharing.Xamarin-UpWP**), které obsahuje dva projekty: **BikeSharing.Clients.Core** a **BikeSharing.Clients.Windows**. Každý projekt obsahuje více souborů, složek a odkazů. Název projektu tučně je *projekt spuštění*; to znamená projekt, který se spustí při spuštění aplikace. Můžete určit, který projekt je spouštěcí projekt.

![Průzkumník řešení s projekty](./media/vside-solution-explorer-projects.png)

Zatímco můžete vytvořit projekt sami přidáním potřebné soubory k němu, Visual Studio nabízí výběr šablon projektu, aby vám náskok. Vytvoření nového projektu ze šablony poskytuje projekt s základy pro daný typ projektu a můžete přejmenovat soubory nebo přidat nový nebo existující kód a další zdroje podle potřeby.

Jak je uvedeno, řešení a projekty nejsou nutné k vývoji aplikací v sadě Visual Studio. Můžete také jen otevřít kód, který jste naklonovali z Gitu nebo stáhli jinam. Další informace naleznete [v tématu Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Vytvoření projektu ze šablony projektu

Informace o vytvoření nového projektu ze šablony naleznete v [tématu Vytvoření nového projektu v sadě Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Vytvoření projektu z existujících souborů kódu

Pokud máte kolekci zdrojových souborů kódu, můžete je snadno přidat do projektu.

1. V nabídce zvolte **Soubor** > **nového** > **projektu z existujícího kódu**.

1. V **průvodci Vytvořit projekt z existujících souborů kódu** vyberte požadovaný typ projektu v rozevíracím seznamu Jaký typ **Next** projektu chcete **vytvořit?**

1. V průvodci vyhledejte umístění souborů a zadejte název nového projektu do pole **Název.** Až budete hotovi, zvolte tlačítko **Dokončit.**

> [!NOTE]
> Tato možnost je nejvhodnější pro relativně jednoduchou kolekci souborů. V současné době jsou podporovány pouze typy projektů C++, Apache Cordova, Visual Basic a C#.

## <a name="add-files-to-a-solution"></a>Přidání souborů do řešení

Pokud máte soubor, který se vztahuje na více projektů, jako je například soubor readme pro řešení nebo jiné soubory, které logicky patří na úrovni řešení, nikoli v rámci konkrétního projektu, můžete je přidat do samotného řešení. Chcete-li přidat položku do řešení, v nabídce kontext (klepnutí pravým tlačítkem myši) uzlu řešení v **Průzkumníku řešení**zvolte **Přidat** > **novou položku**nebo **Přidat** > **existující položku**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Vytvoření projektu .NET, který cílí na určitou verzi rozhraní .NET Framework

Při vytváření projektu rozhraní .NET Framework můžete zadat konkrétní verzi rozhraní .NET Framework, kterou má projekt používat. (Při vytváření projektu .NET Core nezadáte verzi architektury.)

::: moniker range="vs-2017"

Chcete-li určit verzi rozhraní .NET Framework, zvolte rozevírací nabídku **Rozhraní** v dialogovém okně **Nový projekt.**

![Rozevírací informace o rozhraní Framework v dialogovém okně Nový projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Chcete-li získat přístup k verzím rozhraní .NET Framework starším než rozhraní .NET Framework 4, musíte mít v systému nainstalovanou rozhraní .NET Framework 3.5.

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li zadat verzi rozhraní .NET Framework, zvolte rozevírací nabídku **Rozhraní** na stránce **Vytvořit nový projekt.**

![Volič architektury v konfiguraci nového projektu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Vytvoření prázdných řešení

Můžete také vytvořit prázdná řešení, která nemají žádné projekty. To může být vhodnější v případech, kdy chcete vytvořit řešení a projekty od začátku.

### <a name="to-create-an-empty-solution"></a>Vytvoření prázdného řešení

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

::: moniker range="vs-2017"

2. V levém podokně **(Šablony)** zvolte v rozbaleném seznamu řešení **Visual Studio Solutions** **jiné typy** > projektů.

3. Ve středním podokně zvolte **Prázdné řešení**.

4. Zadejte hodnoty **Název** a **umístění** řešení a pak zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **Vytvořit nový projekt** zadejte **řešení** do vyhledávacího pole.

3. Vyberte šablonu **Prázdné řešení** a klepněte na tlačítko **Další**.

4. Zadejte hodnoty **Název** a **umístění** řešení a pak zvolte **Vytvořit**.

::: moniker-end

Po vytvoření prázdného řešení do něj můžete přidat nové nebo existující projekty nebo položky tak, že v nabídce **Projekt** zvolíte **Přidat novou položku** nebo **Přidat existující položku.**

Jak již bylo zmíněno dříve, můžete také otevřít soubory kódu bez nutnosti projektu nebo řešení. Další informace o vývoji kódu tímto způsobem naleznete v [tématu Vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Vytvoření dočasného projektu

(pouze c# a visual basic)

Pokud vytvoříte . Net-based project bez zadání umístění disku, je dočasný projekt. Dočasné projekty umožňují experimentovat s projekty .NET. Kdykoli během práce s dočasným projektem můžete zvolit jeho uložení nebo jeho zahození.

Chcete-li**General**vytvořit dočasný projekt, přejděte nejprve do části**Projekty a obecně řešení** > **možnosti** >  **nástroje** > a odškrtnout políčko **Uložit nové projekty při vytvoření.** Pak otevřete dialogové okno **Nový projekt** obvyklým způsobem.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Odstranění řešení, projektu nebo položky

Řešení a jejich obsah můžete odstranit trvale, ale ne pomocí ide Sady Visual Studio. Odstranění položek v rámci sady Visual Studio pouze odebere z aktuálního řešení nebo projektu. Chcete-li trvale odstranit řešení nebo jinou součást ze systému, odstraňte pomocí Průzkumníka souborů složku obsahující soubory řešení *.sln* a *.suo.* Před trvalým odstraněním řešení je však doporučeno zálohovat všechny projekty nebo soubory v případě, že je budete znovu potřebovat.

> [!NOTE]
> Soubor *.suo* je skrytý soubor, který se nezobrazuje v výchozím nastavení Průzkumníka souborů. Chcete-li zobrazit skryté soubory, zaškrtněte v nabídce **Zobrazení** v Průzkumníkovi souborů **políčko Skryté položky.**

### <a name="permanently-delete-a-solution"></a>Trvalé odstranění řešení

1. V **Průzkumníku řešení**v nabídce řešení, které chcete odstranit, v nabídce pravým tlačítkem myši (kontextová nabídka) zvolte **Otevřít složku v Průzkumníku souborů**.

1. V Průzkumníku souborů přejděte o jednu úroveň výše.

1. Zvolte složku obsahující řešení a stiskněte klávesu **Delete.**

## <a name="see-also"></a>Viz také

- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Open source repozitáře Microsoftu na GitHubu](https://github.com/Microsoft)
- [Ukázky kódu vývojáře](https://code.msdn.microsoft.com/)
- [Vytváření projektů (Visual Studio pro Mac)](/visualstudio/mac/create-new-projects)
