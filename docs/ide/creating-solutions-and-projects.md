---
title: Vytváření řešení a projektů
description: Přečtěte si o rozdílech mezi řešeními a projekty a o jejich použití v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/06/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bd893c06da9bc2c2c8d95fc4c085affa815edd2
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006442"
---
# <a name="create-solutions-and-projects"></a>Vytváření řešení a projektů

*Projekty* uchovávají položky potřebné k sestavení vaší aplikace v aplikaci Visual Studio, jako jsou soubory zdrojového kódu, rastrové obrázky, ikony a odkazy na komponenty a služby. Při vytváření nového projektu vytvoří Visual Studio *řešení* , které obsahuje projekt. V případě potřeby můžete do řešení přidat další nové nebo existující projekty. Řešení mohou také obsahovat soubory, které nejsou připojeny k žádnému konkrétnímu projektu.

![Hierarchie řešení nebo projektu](./media/vside-proj-soln.png)

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [vytvoření projektů v Visual Studio pro Mac](/visualstudio/mac/create-new-projects).

Vaše řešení a projekty můžete zobrazit v okně nástroje s názvem **Průzkumník řešení**. Následující snímek obrazovky ukazuje ukázkové řešení v **Průzkumník řešení** (**BikeSharing. Xamarin-UWP**), které obsahuje dva projekty: **BikeSharing. clients. Core** a **BikeSharing. clients. Windows**. Každý projekt obsahuje několik souborů, složek a odkazů. Název projektu tučně je *projekt po spuštění*. To znamená, že projekt, který se spustí při spuštění aplikace. Můžete určit, který projekt je spouštěný projekt.

![Průzkumník řešení s projekty](./media/vside-solution-explorer-projects.png)

I když můžete sestavit projekt sami přidáním potřebných souborů, Visual Studio nabídne výběr šablon projektu, které vám umožní začít. Vytvořením nového projektu z šablony získáte projekt se základy pro daný typ projektu a v případě potřeby můžete přejmenovat soubory nebo do něj přidat nový nebo existující kód a další prostředky.

Pro vývoj aplikací v aplikaci Visual Studio se tyto řešení a projekty nevyžadují. Můžete taky otevřít jenom kód, který jste naklonoval z Gitu nebo stáhnout jinde. Další informace naleznete v tématu [vývoj kódu v aplikaci Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="create-a-project-from-a-project-template"></a>Vytvoření projektu ze šablony projektu

Informace o vytvoření nového projektu ze šablony naleznete v tématu [Vytvoření nového projektu v aplikaci Visual Studio](create-new-project.md).

## <a name="create-a-project-from-existing-code-files"></a>Vytvořit projekt z existujících souborů kódu

Pokud máte kolekci zdrojových souborů kódu, můžete je snadno přidat do projektu.

1. V nabídce vyberte možnost **soubor**  >  **Nový**  >  **projekt z existujícího kódu**.

1. V průvodci **vytvořením projektu z existujících souborů kódu** zvolte požadovaný typ projektu v poli **jaký typ projektu chcete vytvořit?** rozevírací seznam a poté klikněte na tlačítko **Další** .

1. V průvodci přejděte do umístění souborů a potom do pole **název** zadejte název nového projektu. Až skončíte, klikněte na tlačítko **Dokončit** .

> [!NOTE]
> Tato možnost funguje nejlépe pro relativně jednoduchou kolekci souborů. V současné době jsou podporovány pouze typy projektů C++, Apache Cordova, Visual Basic a C#.

## <a name="add-files-to-a-solution"></a>Přidat soubory do řešení

Pokud máte soubor, který se vztahuje na více projektů, jako je soubor Readme pro řešení nebo jiné soubory, které logicky náležejí na úrovni řešení, nikoli v rámci konkrétního projektu, můžete je přidat do samotného řešení. Chcete-li přidat položku do řešení, v nabídce kontext (klikněte pravým tlačítkem myši) uzlu řešení v **Průzkumník řešení**, vyberte možnost **Přidat**  >  **novou položku** nebo **Přidat**  >  **existující položku**.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Vytvořte projekt .NET, který se zaměřuje na konkrétní verzi .NET Framework

Při vytváření projektu .NET Framework můžete zadat konkrétní verzi .NET Framework, kterou má projekt používat. (Při vytváření projektu .NET Core nezadáte verzi Frameworku.)

::: moniker range="vs-2017"

Chcete-li určit .NET Framework verzi, zvolte rozevírací nabídku **rozhraní** v dialogovém okně **Nový projekt** .

![Rozevírací seznam rozhraní v dialogovém okně Nový projekt](./media/vside-newproject-framework.png)

> [!NOTE]
> Aby bylo možné získat přístup k .NET Framework verzím starším než .NET Framework 4, musíte mít v systému nainstalované .NET Framework 3,5.

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li určit .NET Framework verzi, zvolte rozevírací nabídku **rozhraní** na stránce **vytvořit nový projekt** .

![Selektor architektury v konfiguraci nového projektu](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>Vytvořit prázdná řešení

Můžete také vytvořit prázdná řešení, která neobsahují žádné projekty. To může být vhodnější v případech, kdy chcete vytvořit své řešení a projekty úplně od začátku.

### <a name="to-create-an-empty-solution"></a>Vytvoření prázdného řešení

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

::: moniker range="vs-2017"

2. V levém podokně (**šablony**) v rozbaleném seznamu vyberte **jiné typy projektů** > **řešení sady Visual Studio** .

3. V prostředním podokně vyberte **prázdné řešení**.

4. Zadejte **název** a hodnoty **umístění** pro vaše řešení a pak zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **řešení** .

3. Vyberte šablonu **prázdného řešení** a potom klikněte na tlačítko **Další**.

4. Zadejte **název** a hodnoty **umístění** pro vaše řešení a pak zvolte **vytvořit**.

::: moniker-end

Po vytvoření prázdného řešení můžete do něj přidat nové nebo existující projekty nebo položky výběrem možnosti **Přidat novou položku** nebo **Přidat existující položku** v nabídce **projekt** .

Jak bylo zmíněno dříve, můžete také otevřít soubory kódu bez potřeby projektu nebo řešení. Další informace o vývoji kódu tímto způsobem naleznete v tématu [vývoj kódu v aplikaci Visual Studio bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>Vytvořit dočasný projekt

(Pouze C# a Visual Basic)

Pokud vytvoříte. Projekt založený na síti bez určení umístění na disku, jedná se o dočasný projekt. Dočasné projekty umožňují experimentovat s projekty .NET. Kdykoli při práci s dočasným projektem, můžete ho uložit nebo zahodit.

Chcete-li vytvořit dočasný projekt, nejprve přejít na **nástroje**  >  **Možnosti**  >  **projekty a řešení**  >  **Obecné** a zrušte zaškrtnutí políčka **Uložit nové projekty, pokud je vytvořeno** . Pak otevřete dialogové okno **Nový projekt** obvyklým způsobem.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>Odstranění řešení, projektu nebo položky

Řešení a jejich obsah můžete trvale odstranit, ale ne pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio. Odstraněním položek v sadě Visual Studio dojde pouze k jejich odebrání z aktuálního řešení nebo projektu. Chcete-li trvale odstranit řešení nebo jinou komponentu ze systému, pomocí Průzkumníka souborů odstraňte složku, která obsahuje soubory řešení *. sln* a *. suo* . Před odstraněním řešení ale doporučujeme, abyste všechny projekty nebo soubory zazálohovali v případě, že je budete potřebovat znovu.

> [!NOTE]
> Soubor *. suo* je skrytý soubor, který není zobrazen pod výchozím nastavením Průzkumníka souborů. Skryté soubory zobrazíte tak, že v nabídce **Zobrazit** v Průzkumníkovi souborů zaškrtnete políčko **skryté položky** .

### <a name="permanently-delete-a-solution"></a>Trvalé odstranění řešení

1. V **Průzkumník řešení** v nabídce kliknutím pravým tlačítkem (kontextová nabídka) řešení, které chcete odstranit, vyberte **Otevřít složku v Průzkumníkovi souborů**.

1. V Průzkumníku souborů přejděte o jednu úroveň výše.

1. Zvolte složku, která obsahuje řešení, a potom stiskněte klávesu **Delete** .

## <a name="see-also"></a>Viz také

- [Řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Open Source úložiště Microsoftu na GitHubu](https://github.com/Microsoft)
- [Ukázky kódu pro vývojáře](https://code.msdn.microsoft.com/)
- [Vytváření projektů (Visual Studio pro Mac)](/visualstudio/mac/create-new-projects)
