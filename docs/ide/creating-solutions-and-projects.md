---
title: Vytváření řešení a projektů
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06696ca975fb80eaa97cd265c9d45e6174d3b053
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348534"
---
# <a name="create-solutions-and-projects"></a>Vytváření řešení a projektů

*Projekty* uložení položky, které jsou potřebné k sestavení aplikace v sadě Visual Studio, jako jsou soubory zdrojového kódu, rastrové obrázky, ikony a odkazy na komponent a služeb. Když vytvoříte nový projekt, vytvoří Visual Studio *řešení* tak, aby obsahovala projektu. Pokud chcete, můžete přidat pak dalších nových nebo existujících projektů do řešení. Řešení může také obsahovat soubory, které nejsou připojené do žádného konkrétního projektu.

![Hierarchie řešení nebo projektu](./media/vside-proj-soln.png)

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [vytvářet projekty v sadě Visual Studio pro Mac](/visualstudio/mac/create-new-projects).

Řešení a projekty můžete zobrazit v okně nástroje **Průzkumníka řešení**. Následující snímek obrazovky ukazuje příklad řešení v **Průzkumníka řešení** (**BikeSharing.Xamarin UPW**), který obsahuje dva projekty: **BikeSharing.Clients.Core** a **BikeSharing.Clients.Windows**. Každý projekt obsahuje více souborů, složek a odkazy. Je název projektu tučným písmem *spouštěný projekt*; to znamená, že projekt, který se spustí při spuštění aplikace. Můžete určit, který projekt je projekt po spuštění.

![Průzkumník řešení s projekty](./media/vside-solution-explorer-projects.png)

Přestože lze vytvořit projekt sami tak, že přidáte soubory potřebné k němu, Visual Studio nabízí škály projektových šablon vám začít. Vytvoření nového projektu z šablony máte projekt se základy pro daný typ projektu, a můžete přejmenovat soubory nebo k němu podle potřeby přidat nový nebo existující kód a další prostředky.

Který říká, řešení a projekty není nutné pro vývoj aplikací v sadě Visual Studio. Můžete otevřít také pouze kód, který jste naklonovali z Gitu nebo stáhli jinde. Další informace najdete v tématu [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

> [!NOTE]
> Popisy v tomto tématu jsou založeny na Visual Studio Community edition. Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch zde popsaných v závislosti na vašem nastavení nebo verzi systému Visual Studio. Chcete-li změnit nastavení, například k **Obecné** nebo **Visual C++** nastavení, zvolte **nástroje** > **nastavení importu a exportu**a klikněte na tlačítko **obnovit všechna nastavení**.

## <a name="to-create-a-project-from-a-project-template"></a>Vytvoření projektu ze šablony projektu

1. Vytvoření nového projektu v sadě Visual Studio několika způsoby. Na **úvodní stránka**, zadejte název šablony projektu v **Hledat šablony projektů** nebo klikněte **vytvořit nový projekt** odkaz k otevření **nový Projekt** dialogové okno. Můžete také zvolit **souboru** > **nový** > **projektu** v nabídce panelu, nebo zvolte **nový projekt** tlačítko na panelu nástrojů.

   ![Úvodní stránka](./media/vside-newproject1.png)

   V **nový projekt** dialogovém okně dostupných šablon projektu se zobrazí v seznamu v části **šablony** kategorie. Šablony jsou uspořádané podle programovacího jazyka a projekt typu, jako je vizuál C#, JavaScript a Azure Data Lake.

   ![Dialogové okno Nový projekt](./media/vside-newproject-templates-list.png)

   > [!NOTE]
   > Seznam dostupných jazyků a šablony projektů, které se zobrazí, závisí na verzi sady Visual Studio spustíte a úlohy, které jsou nainstalovány. Další informace o tom, jak nainstalovat další úlohy, naleznete v tématu [upravit Visual Studio 2017 přidáním nebo odebráním úlohy a komponenty](../install/modify-visual-studio.md).

2. Zobrazit seznam šablon pro programovací jazyk, který chcete použít výběrem trojúhelníku vedle názvu jazyka a pak zvolte typ projektu.

   Následující příklad ukazuje dostupné šablony projektů pro vizuál C# projekty .NET Core.

   ![Šablony projektů](./media/new-project-dialog-net-core.png)

3. Zadejte název nového projektu v **název** pole. Můžete zvolit uložení projektu ve výchozím umístění ve vašem systému, nebo **Procházet** tlačítko a vyhledejte jiné umístění.

   Také v případě potřeby můžete změnit název řešení nebo přidat nový projekt do úložiště Git výběrem **přidat do správy zdrojových kódů**.

4. Zvolte **OK** pro vytvoření řešení a projektu.

5. Pokud chcete přidat další projekt do řešení, vyberte uzel řešení v **Průzkumníka řešení**a pak na panelu nabídek zvolte **projektu** > **přidat novou položku**.

## <a name="create-a-project-from-existing-code-files"></a>Vytvoření projektu z existujících souborů kódu

Pokud máte kolekci souborů zdrojového kódu, můžete je snadno přidat do projektu.

1. V nabídce zvolte **souboru** > **nový** > **projekt z existujícího kódu**.

1. V **vytvořit projekt z existujících souborů kódu** průvodce, zvolte typ projektu chcete **jaký typ projektu chcete vytvořit?** rozevíracího seznamu pole a klikněte na tlačítko **další**  tlačítko.

1. V průvodci, přejděte do umístění souborů a potom zadejte název nového projektu v **název** pole. Jakmile budete hotovi, zvolte **Dokončit** tlačítko.

> [!NOTE]
> Tato možnost je nejlepší pro poměrně jednoduchá kolekce souborů. V současné době pouze Visual C++, Apache Cordova v jazyce Visual Basic a C# jsou podporovány typy projektů.

## <a name="add-files-to-a-solution"></a>Přidání souborů do řešení

Pokud máte soubor, který platí pro více projektů, jako je například soubor readme pro řešení, nebo jiné soubory, které logicky patří na úrovni řešení, spíše než v rámci určitého projektu, pak můžete přidat je do vlastním řešením. Postup přidání položky do řešení, v nabídce kontextu (klikněte pravým tlačítkem) uzel řešení v **Průzkumníka řešení**, zvolte **přidat** > **nová položka**, nebo **Přidat** > **existující položku**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Vytvořit projekt .NET, který cílí na konkrétní verzi rozhraní .NET Framework

Když vytvoříte projekt, můžete zadat konkrétní verzi rozhraní .NET Framework, který chcete projekt, který používá. Chcete-li určit verzi rozhraní .NET framework, zvolte **Framework** v rozevírací nabídce **nový projekt** dialogové okno.

![Rozhraní Framework rozevírací seznam v dialogovém okně Nový projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Musíte mít rozhraní .NET Framework 3.5 v systému nainstalovány pro přístup k rozhraní .NET Framework verze starší než .NET Framework 4.

## <a name="create-empty-solutions"></a>Vytvoření prázdných řešení

Můžete také vytvořit prázdné řešení, které mají žádné projekty. To může být vhodnější v případech, kde chcete vytvořit řešení a projekty úplně od začátku.

### <a name="to-create-an-empty-solution"></a>Vytvoření prázdného řešení

1. V nabídce zvolte **souboru** > **nový** > **projektu**.

1. V levém (**šablony**) podokně zvolte **ostatní typy projektů** > **řešení sady Visual Studio** z rozbaleného seznamu.

1. V prostředním podokně vyberte **prázdné řešení**.

1. Zadejte **název** a **umístění** hodnoty pro vaše řešení, klikněte na tlačítko **OK**.

Po vytvoření prázdného řešení můžete přidat nové nebo existující projekty nebo položky k němu výběrem **přidat novou položku** nebo **přidat existující položku** na **projektu** nabídky.

Jak už bylo zmíněno dříve, můžete také otevřít soubory kódu bez nutnosti projekt nebo řešení. Další informace o vývoji kódu tímto způsobem, najdete v článku [vývoj kódu v sadě Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-temporary-project-c-and-visual-basic"></a>Vytvoření dočasného projektu (C# a Visual Basic)

Pokud vytvoříte. Na základě NET projektu bez zadání umístění na disku, je dočasný projekt. Dočasné projekty umožňují snadno experimentovat s projekty .NET. Kdykoli při práci s projektem dočasné můžete uložit nebo zahodit.

Chcete-li vytvořit dočasný projekt, nejprve přejděte na **nástroje** > **možnosti** > **projekty a řešení**  >   **Obecné**a zrušte zaškrtnutí políčka **uložit nové projekty při vytvoření** zaškrtávací políčko. Otevřete **nový projekt** dialogovém jako obvykle.

## <a name="delete-a-solution-project-or-item"></a>Odstranění řešení, projektu nebo položky

Řešení a jejich obsah můžete odstranit trvale, ale nikoli pomocí integrovaného vývojového prostředí sady Visual Studio. Odstraňování položek v sadě Visual Studio pouze odebere z aktuální řešení nebo projektu. Pokud chcete trvale odstranit z vašeho systému řešení nebo jiné součásti, pomocí Průzkumníka souborů můžete odstranit složku obsahující *.sln* a *.suo* soubory řešení. Před odstraněním trvale řešení, ale doporučuje zálohovat všechny projekty nebo souborů v případě potřeby znovu.

> [!NOTE]
> *.Suo* souboru je skrytý soubor, který není zobrazen ve výchozím nastavení Průzkumníku souborů. Chcete-li zobrazit skryté soubory na **zobrazení** nabídky v Průzkumníku souborů vyberte **skryté položky** zaškrtávací políčko.

### <a name="to-permanently-delete-a-solution"></a>Trvale odstranit řešení

1. V **Průzkumníka řešení**, v kontextové nabídce řešení, které chcete odstranit, zvolte **otevřít složku v Průzkumníku souborů**.

1. V Průzkumníku souborů přejděte o jednu úroveň výše.

1. Zvolte složku, která obsahuje řešení a klikněte na tlačítko **odstranit** klíč.

## <a name="see-also"></a>Viz také:

- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Otevřít zdroj úložiště Microsoftu na Githubu](https://github.com/Microsoft)
- [Ukázky kódu vývojáře](https://code.msdn.microsoft.com/)
- [Vytváření projektů (Visual Studio for Mac)](/visualstudio/mac/create-new-projects)