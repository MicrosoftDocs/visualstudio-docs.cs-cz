---
title: Pracovní prostory a jazykové služby v aplikaci Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952693"
---
# <a name="workspaces-and-language-services"></a>Pracovní prostory a jazykové služby

Služba Language Services může uživatelům poskytnout [otevřené složky](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) stejné funkce, které jsou používány při práci s řešeními a projekty. Služba jazyka může být samoobslužně aktivována v závislosti na příponě souboru nebo obsahu otevřeného dokumentu, i když je tato služba jazyka "volný soubor" omezena na zvýrazňování syntaxe. Další informace jsou vyžadovány k zajištění rozsáhlejšího prostředí při úpravách nebo kontrole zdrojového kódu. Každá služba jazyka má své vlastní rozhraní API pro inicializaci pomocí těchto dalších kontextových dat pro dokument. To je obvykle spravováno systémem projektu, který je pevně spojený s jazykovou službou a systémem sestavení.

## <a name="initialization"></a>Inicializace

V [pracovním prostoru](workspaces.md)jsou jazykové služby inicializovány <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> bodem rozšíření, který se specializuje pouze na tuto jazykovou službu a ví, že vytváření sestavení není žádné. Tímto způsobem může vlastník jazykové služby zachovat jedinou příponu otevřené složky bez ohledu na to, kolik vzorů existuje ve složkách a souborech pro spuštění kompilátoru během sestavování (například MSBuild, soubory pravidel atd.). Když se na disku změní soubory, ze kterých se vytvořil kontext souboru, a kontext souboru se aktualizuje, poskytovatel jazykové služby se oznámí aktualizované sadě kontextů souborů. Poskytovatel jazykové služby může následně aktualizovat svůj model.

Když je dokument otevřen v editoru, Visual Studio bere v úvahu pouze poskytovatele jazykové služby, které vyžadují typy kontextu souboru, pro které je možné najít odpovídajícího poskytovatele kontextu souboru. Poté předává kontexty souborů od odpovídajícího zprostředkovatele k vybranému poskytovateli jazykové služby prostřednictvím `ILanguageServiceProvider.InitializeAsync` . Jaký má poskytovatel jazykové služby s tímto souborem kontextová data, jsou podrobné informace o implementaci poskytovatele jazykové služby, ale očekávané uživatelské prostředí je bohatší jazyková služba pro daný otevřený dokument.

## <a name="using-ilanguageserviceprovider"></a>Použití ILanguageServiceProvider

Služba jazyka bude upozorněna, když je vytvořen kontext souboru `ContextType` , který odpovídá jedné z `SupportedContextTypes` hodnot atributu export jazykového serveru.

Pro podporu jazykové služby bude rozšíření potřebovat:

- Jedinečné `Guid` . Tento parametr bude použit pro `SupportedContextTypes` argumenty atributů a v `FileContext` objektu.
- Kontext souboru jazyka
  - Továrna poskytovatele
    - `ExportFileContextProviderAttribute` atribut s výše uvedeným jednoznačně generovaným `Guid` v `SupportedContextTypes`
    - Implementace `IWorkspaceProviderFactory<IFileContextProvider>`
  - Implementace poskytovatele pro `IFileContextProvider.GetContextsForFileAsync`
    - Vytvoří nový `FileContext` s `contextType` argumentem konstruktoru jako jedinečně generovanou. `Guid`
    - Použijte `Context` vlastnost `FileContext` k poskytnutí dalších dat `ILanguageServiceProvider`
- Služba jazyka
  - Továrna poskytovatele
    - `ExportLanguageServiceProvider` atribut s výše uvedeným jednoznačně generovaným `Guid` v `SupportedContextTypes`
    - Implementace `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Poskytovatel
    - Implementace `ILanguageServiceProvider`
    - Slouží `ILanguageServiceProvider.InitializeAsync` k povolení jazykových služeb pro zadané argumenty při otevření souboru.
    - Slouží `ILanguageServiceProvider.UninitializeAsync` k zakázání jazykových služeb pro zadané argumenty při zavření souboru.

>[!WARNING]
>`ILanguageServiceProvider`Metody mohou být vyvolány pracovním prostorem v hlavním vlákně. Zvažte plánování práce v jiném vlákně, abyste se vyhnuli zavedením prodlev uživatelského rozhraní.

## <a name="language-server-protocol"></a>Protokol jazyka serveru

`Microsoft.VisualStudio.Workspace.*`Rozhraní API nejsou jediným způsobem, jak povolit službu jazyka v otevřené složce. Další možností je použití jazykového serveru. Další informace najdete v tématu o [protokolu pro jazykovém serveru](language-server-protocol.md).

## <a name="related-interfaces"></a>Související rozhraní

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> je vyvolána při otevření nebo zavření souboru odpovídajícího typu souboru pro úpravy.

## <a name="next-steps"></a>Další kroky

* [Sestavení pracovního prostoru](workspace-build.md) – otevřená složka podporuje systémy sestavení, jako jsou MSBuild a soubory pravidel.