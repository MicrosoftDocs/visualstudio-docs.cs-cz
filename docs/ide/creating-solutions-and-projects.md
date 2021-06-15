---
title: Vytváření &amp; řešení pro Visual Studio projektů &amp;
description: Přečtěte si o rozdílech mezi řešeními a projekty a o tom, jak je používat v Visual Studio.
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 06/14/2021
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f253492e5c1b3bf0c27448d59d754260e9e70912
ms.sourcegitcommit: 529e1716924c3e1ac8a750550b996ad3c79f353b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/14/2021
ms.locfileid: "112066940"
---
# <a name="create-work-with-and-delete-visual-studio-projects-and-solutions"></a>Vytváření, práce a odstraňování Visual Studio projekty a řešení

V tomto článku se dozvíte, jak vytvářet a používat Visual Studio od začátku k ukládání artefaktů, které potřebujete k vytváření aplikací.  Pokud nejste obeznámeni s projekty v Visual Studio, podívejte se na tento přehled [projektů a řešení.](solutions-and-projects-in-visual-studio.md)  Informace o tom, jak rychle vytvořit projekt ze šablony, najdete v tématu [Vytvoření projektu ze šablony](create-new-project.md).

*Projekty* uchová položky potřebné k sestavení aplikace v Visual Studio, jako jsou soubory zdrojového kódu, rastrové obrázky, ikony a odkazy na komponenty a služby. Když vytvoříte nový projekt, Visual Studio *řešení, které* bude projekt obsahovat. Pokud chcete, můžete do řešení přidat další nové nebo existující projekty. Řešení mohou také obsahovat soubory, které nejsou připojené k žádnému konkrétnímu projektu.

![Diagram znázorňující hierarchii řešení a projektu](./media/vside-proj-soln.png)

> [!NOTE]
> Toto téma se týká Visual Studio ve Windows. Další Visual Studio pro Mac v tématu [Vytváření projektů v Visual Studio pro Mac](/visualstudio/mac/create-new-projects).

Řešení a projekty můžete zobrazit v okně nástrojů s názvem **Průzkumník řešení**. Následující snímek obrazovky ukazuje příklad řešení v **Průzkumník řešení** (**BikeSharing.Xamarin-UPW),** které obsahuje dva projekty: **BikeSharing.Clients.Core** a **BikeSharing.Clients.Windows**. Každý projekt obsahuje více souborů, složek a odkazů. Tučný název projektu je *spouštěný projekt*. To znamená projekt, který se spustí při spuštění aplikace. Můžete určit, který projekt je spouštěný projekt.

![Snímek obrazovky Průzkumník řešení se dvěma projekty](./media/vside-solution-explorer-projects.png)

Projekt můžete vytvořit sami přidáním potřebných souborů, ale Visual Studio nabízí výběr šablon projektů, které vám podají náskok. Vytvoření nového projektu ze šablony vám poskytne projekt se základy pro tento typ projektu a můžete je podle potřeby přejmenovat nebo přidat nový nebo existující kód a další prostředky.

Řešení a projekty ale nejsou potřeba k vývoji aplikací v Visual Studio. Můžete také otevřít kód, který jste naklonovali z Gitu nebo stáhli jinam. Další informace najdete v tématu [Vývoj kódu v Visual Studio bez projektů nebo řešení.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="create-a-project-from-a-project-template"></a>Vytvoření projektu ze šablony projektu

Informace o tom, jak vybrat šablonu pro vytvoření nového projektu, najdete v tématu Vytvoření [nového projektu](create-new-project.md)v Visual Studio . A příklad projektu a řešení, které je vytvořené od začátku, s podrobnými pokyny a ukázkovým kódem najdete v tématu Úvod do projektů a [řešení.](../get-started/tutorial-projects-solutions.md)

## <a name="create-a-project-from-existing-code-files"></a>Vytvoření projektu z existujících souborů kódu

Pokud máte kolekci zdrojových souborů kódu, můžete je snadno přidat do projektu.

1. V nabídce vyberte **File** New Project From Existing Code (Soubor  >  **nového**  >  **projektu z existujícího kódu).**

1. V **průvodci Create Project from Existing Code Files** (Vytvořit projekt z existujících souborů kódu) vyberte v rozevíracím seznamu What type of project would you like to create? (Jaký typ projektu chcete **vytvořit?)** typ projektu, a pak vyberte **tlačítko Next** (Další).

1. V průvodci přejděte do umístění souborů a do pole Název zadejte **název** nového projektu. Až budete hotovi, vyberte **tlačítko** Dokončit.

> [!NOTE]
> Tato možnost je nejlepší pro poměrně jednoduchou kolekci souborů. V současné době jsou podporovány pouze typy projektů C++, Apache Cordova, Visual Basic a C#.

## <a name="add-files-to-a-solution"></a>Přidání souborů do řešení

Pokud máte soubor, který se vztahuje na více projektů, například soubor readme pro řešení nebo jiné soubory, které logicky patří na úroveň řešení, nikoli do konkrétního projektu, můžete je přidat do samotného řešení. Pokud chcete přidat položku do řešení, vyberte v místní nabídce (kliknutím pravým tlačítkem) uzlu řešení v **Průzkumník řešení** možnost Přidat novou položku nebo Přidat existující   >     >  **položku**.

> [!TIP]
> Soubor řešení je struktura pro uspořádání projektů v Visual Studio. Obsahuje stav těchto informací ve dvou souborech: soubor *.sln* (textový, sdílený) a *soubor .suo* (binární, skryté možnosti řešení specifické pro uživatele). Proto řešení není něco, co by se mělo zkopírovat a přejmenovat. Místo toho je nejlepší vytvořit nové řešení a pak do něj přidat existující položky.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Vytvoření projektu .NET, který cílí na konkrétní verzi .NET Framework

Při vytváření .NET Framework můžete zadat konkrétní verzi aplikace, .NET Framework má projekt používat. (Při vytváření projektu .NET Core nezadáte verzi architektury.)

::: moniker range="vs-2017"

Pokud chcete .NET Framework verzi, vyberte **v** dialogovém okně Nový projekt rozevírací **nabídku** Rozhraní.

![Snímek obrazovky s rozevíracím seznamem Framework v dialogovém okně Nový projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Pro přístup k .NET Framework verzím starším než .NET Framework 4 musíte mít v systému nainstalovanou .NET Framework verzi 3.5.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud chcete zadat .NET Framework, vyberte rozevírací nabídku **Framework** (Rozhraní) na **stránce Create a new project (Vytvořit nový** projekt).

![Snímek obrazovky selektorem architektury v dialogovém okně Konfigurovat nový projekt](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Vytváření prázdných řešení

Můžete také vytvořit prázdná řešení, která nemají žádné projekty. To může být vhodnější v případech, kdy chcete vytvořit řešení a projekty od začátku.

### <a name="to-create-an-empty-solution"></a>Vytvoření prázdného řešení

1. V řádku nabídek vyberte **File** New Project  >  **(Soubor nový**  >  **projekt).**

::: moniker range="vs-2017"

2. V levém podokně (**Šablony)** **vyberte** v rozbaleném seznamu Visual Studio typy projektů > **a** řešení.

3. V prostředním podokně vyberte **Prázdné řešení.**

4. Zadejte **hodnoty** **Name (Název)** a Location (Umístění) pro vaše řešení a pak vyberte **OK.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Na **stránce Vytvořit nový projekt** zadejte **do vyhledávacího** pole solution.

3. Vyberte šablonu **Prázdné řešení** a pak klikněte na **Další.**

4. Zadejte **hodnoty** **Name (Název)** a Location (Umístění) pro vaše řešení a pak vyberte **Create (Vytvořit).**

::: moniker-end

Po vytvoření prázdného řešení můžete do něj přidat nové nebo  existující projekty  nebo položky tak, že v nabídce Projekt zvolíte Přidat novou položku nebo **Přidat** existující položku.

Jak už bylo zmíněno dříve, můžete také otevírat soubory kódu, aniž byste potřebovali projekt nebo řešení. Další informace o vývoji kódu tímto způsobem najdete v tématu Vývoj kódu [v Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Vytvoření dočasného projektu

(Pouze C# a Visual Basic))

Pokud vytvoříte . Jedná se o dočasný projekt bez určení umístění disku. Dočasné projekty umožňují experimentovat s projekty .NET. Kdykoli při práci s dočasným projektem můžete zvolit jeho uložení nebo jeho zahození.

Pokud chcete vytvořit dočasný projekt, nejprve přejděte na **Nástroje** Možnosti Projekty a řešení Obecné a zrušte zaškrtnutí políčka Při vytváření ukládat  >    >    >   **nové projekty.** Pak jako **obvykle otevřete** dialogové okno Nový projekt.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Odstranění řešení, projektu nebo položky

Místní nabídku po kliknutí pravým tlačítkem můžete použít k odstranění nebo odebrání řešení, projektů nebo položek v Visual Studio, ale tím se odeberou jenom z aktuálního řešení nebo projektu.

Pokud chcete trvale odstranit řešení nebo jiné součásti ze systému, pomocí nástroje **Průzkumník souborů** ve Windows odstraňte složku, která obsahuje soubory řešení *.sln* a *.suo.* (Než řešení odstraníte, možná budete chtít zálohovat projekty a soubory pro případ, že je budete znovu potřebovat.)

> [!NOTE]
> Soubor *.suo* je skrytý soubor, který se nezobrazuje ve výchozím nastavení Průzkumník souborů souboru. Pokud chcete zobrazit skryté soubory, v **nabídce Zobrazení** v Průzkumník souborů zaškrtněte **políčko Skryté** položky.

### <a name="permanently-delete-a-solution"></a>Trvalé odstranění řešení

Přístup k Průzkumník souborů ve Windows můžete získat pomocí Průzkumník řešení v Visual Studio. Jak na to:

1. V **Průzkumník řešení** klikněte pravým tlačítkem na nabídku (místní nabídku) řešení, které chcete odstranit, vyberte Otevřít složku **v Průzkumník souborů**.

1. V Průzkumníku souborů přejděte o jednu úroveň výše.

1. Vyberte složku, která obsahuje řešení, a stiskněte **klávesu Delete.**

## <a name="see-also"></a>Viz také

- [Úvod do projektů a řešení](../get-started/tutorial-projects-solutions.md)
- [Správa vlastností projektu a řešení](managing-project-and-solution-properties.md)
- [Filtrovaná řešení v Visual Studio](filtered-solutions.md)
- [Úložiště open source Microsoftu na GitHubu](https://github.com/Microsoft)
- [Ukázky kódu pro vývojáře](https://code.msdn.microsoft.com/)
- [Zdroje informací pro řešení Visual Studio chyb integrovaného vývojového prostředí](./reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
