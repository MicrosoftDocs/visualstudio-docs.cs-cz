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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589744"
---
# <a name="create-solutions-and-projects"></a>Vytváření řešení a projektů

*Projekty* uchovávají položky potřebné k sestavení vaší aplikace v aplikaci Visual Studio, jako jsou soubory zdrojového kódu, rastrové obrázky, ikony a odkazy na komponenty a služby. Když vytvoříte nový projekt, vytvoří Visual Studio *řešení* tak, aby obsahovala projektu. Pokud chcete, můžete přidat pak dalších nových nebo existujících projektů do řešení. Řešení může také obsahovat soubory, které nejsou připojené do žádného konkrétního projektu.

![Hierarchie řešení nebo projektu](./media/vside-proj-soln.png)

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [vytvářet projekty v sadě Visual Studio pro Mac](/visualstudio/mac/create-new-projects).

Řešení a projekty můžete zobrazit v okně nástroje **Průzkumníka řešení**. Následující snímek obrazovky ukazuje příklad řešení v **Průzkumníka řešení** (**BikeSharing.Xamarin UPW**), který obsahuje dva projekty: **BikeSharing.Clients.Core** a **BikeSharing.Clients.Windows**. Každý projekt obsahuje více souborů, složek a odkazy. Je název projektu tučným písmem *spouštěný projekt*; to znamená, že projekt, který se spustí při spuštění aplikace. Můžete určit, který projekt je projekt po spuštění.

![Průzkumník řešení s projekty](./media/vside-solution-explorer-projects.png)

Přestože lze vytvořit projekt sami tak, že přidáte soubory potřebné k němu, Visual Studio nabízí škály projektových šablon vám začít. Vytvoření nového projektu z šablony máte projekt se základy pro daný typ projektu, a můžete přejmenovat soubory nebo k němu podle potřeby přidat nový nebo existující kód a další prostředky.

Který říká, řešení a projekty není nutné pro vývoj aplikací v sadě Visual Studio. Můžete otevřít také pouze kód, který jste naklonovali z Gitu nebo stáhli jinde. Další informace najdete v tématu [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Vytvoření projektu ze šablony projektu

Informace o vytvoření nového projektu ze šablony naleznete v tématu [Vytvoření nového projektu v aplikaci Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Vytvoření projektu z existujících souborů kódu

Pokud máte kolekci souborů zdrojového kódu, můžete je snadno přidat do projektu.

1. V nabídce zvolte **souboru** > **nový** > **projekt z existujícího kódu**.

1. V **vytvořit projekt z existujících souborů kódu** průvodce, zvolte typ projektu chcete **jaký typ projektu chcete vytvořit?** rozevíracího seznamu pole a klikněte na tlačítko **další**  tlačítko.

1. V průvodci, přejděte do umístění souborů a potom zadejte název nového projektu v **název** pole. Jakmile budete hotovi, zvolte **Dokončit** tlačítko.

> [!NOTE]
> Tato možnost je nejlepší pro poměrně jednoduchá kolekce souborů. V současné době C++jsou podporovány pouze typy Apache Cordova, C# Visual Basic a projektů.

## <a name="add-files-to-a-solution"></a>Přidání souborů do řešení

Pokud máte soubor, který platí pro více projektů, jako je například soubor readme pro řešení, nebo jiné soubory, které logicky patří na úrovni řešení, spíše než v rámci určitého projektu, pak můžete přidat je do vlastním řešením. Postup přidání položky do řešení, v nabídce kontextu (klikněte pravým tlačítkem) uzel řešení v **Průzkumníka řešení**, zvolte **přidat** > **nová položka**, nebo **Přidat** > **existující položku**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Vytvořit projekt .NET, který cílí na konkrétní verzi rozhraní .NET Framework

Při vytváření projektu .NET Framework můžete zadat konkrétní verzi .NET Framework, kterou má projekt používat. (Při vytváření projektu .NET Core nezadáte verzi Frameworku.)

::: moniker range="vs-2017"

Chcete-li určit .NET Framework verzi, zvolte rozevírací nabídku **rozhraní** v dialogovém okně **Nový projekt** .

![Rozhraní Framework rozevírací seznam v dialogovém okně Nový projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Musíte mít rozhraní .NET Framework 3.5 v systému nainstalovány pro přístup k rozhraní .NET Framework verze starší než .NET Framework 4.

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li určit .NET Framework verzi, zvolte rozevírací nabídku **rozhraní** na stránce **vytvořit nový projekt** .

![Selektor architektury v konfiguraci nového projektu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Vytvoření prázdných řešení

Můžete také vytvořit prázdné řešení, které mají žádné projekty. To může být vhodnější v případech, kde chcete vytvořit řešení a projekty úplně od začátku.

### <a name="to-create-an-empty-solution"></a>Vytvoření prázdného řešení

1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

::: moniker range="vs-2017"

2. V levém podokně (**šablony**) vyberte **jiné typy projektů** > řešení sady **Visual Studio** v rozbaleném seznamu.

3. V prostředním podokně vyberte **prázdné řešení**.

4. Zadejte **název** a hodnoty **umístění** pro vaše řešení a pak zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **řešení** .

3. Vyberte šablonu **prázdného řešení** a potom klikněte na tlačítko **Další**.

4. Zadejte **název** a hodnoty **umístění** pro vaše řešení a pak zvolte **vytvořit**.

::: moniker-end

Po vytvoření prázdného řešení můžete přidat nové nebo existující projekty nebo položky k němu výběrem **přidat novou položku** nebo **přidat existující položku** na **projektu** nabídky.

Jak už bylo zmíněno dříve, můžete také otevřít soubory kódu bez nutnosti projekt nebo řešení. Další informace o vývoji kódu tímto způsobem, najdete v článku [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Vytvořit dočasný projekt

(C# jenom Visual Basic)

Pokud vytvoříte. Na základě NET projektu bez zadání umístění na disku, je dočasný projekt. Dočasné projekty umožňují snadno experimentovat s projekty .NET. Kdykoli při práci s projektem dočasné můžete uložit nebo zahodit.

Chcete-li vytvořit dočasný projekt, nejprve přejděte na **nástroje** > **možnosti** > **projekty a řešení**  >   **Obecné**a zrušte zaškrtnutí políčka **uložit nové projekty při vytvoření** zaškrtávací políčko. Otevřete **nový projekt** dialogovém jako obvykle.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Odstranění řešení, projektu nebo položky

Řešení a jejich obsah můžete odstranit trvale, ale nikoli pomocí integrovaného vývojového prostředí sady Visual Studio. Odstraňování položek v sadě Visual Studio pouze odebere z aktuální řešení nebo projektu. Pokud chcete trvale odstranit z vašeho systému řešení nebo jiné součásti, pomocí Průzkumníka souborů můžete odstranit složku obsahující *.sln* a *.suo* soubory řešení. Před odstraněním trvale řešení, ale doporučuje zálohovat všechny projekty nebo souborů v případě potřeby znovu.

> [!NOTE]
> *.Suo* souboru je skrytý soubor, který není zobrazen ve výchozím nastavení Průzkumníku souborů. Chcete-li zobrazit skryté soubory na **zobrazení** nabídky v Průzkumníku souborů vyberte **skryté položky** zaškrtávací políčko.

### <a name="permanently-delete-a-solution"></a>Trvalé odstranění řešení

1. V **Průzkumník řešení**v nabídce kliknutím pravým tlačítkem (kontextová nabídka) řešení, které chcete odstranit, vyberte **Otevřít složku v Průzkumníkovi souborů**.

1. V Průzkumníku souborů přejděte o jednu úroveň výše.

1. Zvolte složku, která obsahuje řešení, a potom stiskněte klávesu **Delete** .

## <a name="see-also"></a>Viz také:

- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Otevřít zdroj úložiště Microsoftu na Githubu](https://github.com/Microsoft)
- [Ukázky kódu vývojáře](https://code.msdn.microsoft.com/)
- [Vytváření projektů (Visual Studio for Mac)](/visualstudio/mac/create-new-projects)
