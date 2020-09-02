---
title: Kontexty souborů pracovních prostorů v aplikaci Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952809"
---
# <a name="workspace-file-contexts"></a>Kontexty souborů pracovních prostorů

Všechny přehledy o pracovních prostorech [otevřené složky](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) jsou vytvářeny pomocí "zprostředkovatelů kontextu souborů", které implementují <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> rozhraní. Tato rozšíření mohou hledat vzory ve složkách nebo souborech, číst soubory a soubory nástroje MSBuild, zjišťovat závislosti balíčků atd., aby bylo možné shromáždit přehledy, které potřebují k definování kontextu souboru. Samotný kontext souboru neprovádí žádnou akci, ale místo toho poskytuje data, na kterých může další rozšíření pracovat.

Každá <xref:Microsoft.VisualStudio.Workspace.FileContext> z nich má `Guid` přidruženou hodnotu, která identifikuje typ dat, která zanáší. Pracovní prostor `Guid` ho později používá k tomu, aby se shodoval s rozšířeními, která data využívají prostřednictvím <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> Vlastnosti. Zprostředkovatel kontextu souboru je exportován s metadaty, které určují kontext souboru `Guid` s, pro který může vytvořit data.

Po definování může být kontext souboru přidružen k libovolnému počtu souborů nebo složek v pracovním prostoru. Daný soubor nebo složka mohou být přidruženy k libovolnému počtu kontextů souborů. Je to relace m:n.

Nejběžnější scénáře pro kontexty souborů souvisejí s vytvářením, laděním a jazykovými službami. Další informace najdete v dalších tématech týkajících se těchto scénářů.

## <a name="file-context-lifecycle"></a>Životní cyklus kontextu souboru

Životní cykly pro a `FileContext` jsou nedeterministické. Komponenta může kdykoli asynchronně vyžádat určitou sadu typů kontextu. Budou dotazováni poskytovatelé, kteří podporují určitou podmnožinu typů kontextu požadavku. `IWorkspace`Instance funguje jako střední muž mezi spotřebitelem a poskytovateli prostřednictvím <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> metody. Příjemci si můžou vyžádat kontext a udělat nějakou krátkodobou akci založenou na kontextu, zatímco ostatní si můžou vyžádat kontext a udržovat dlouhodobé nedlouhodobé reference.

Změny se mohou projevit u souborů, které způsobují zastaralou kontext souboru. Poskytovatel může vyvolat událost na, `FileContext` aby upozornil uživatele na aktualizace. Například pokud je k dispozici kontext sestavení pro určitý soubor, ale změna na disku zruší platnost tohoto kontextu, pak původní producent může událost vyvolat. Všichni příjemci stále odkazují na to, že se `FileContext` pak můžou znovu dotazovat na nové `FileContext` .

>[!NOTE]
>Neexistuje žádný model nabízených oznámení pro příjemce. Po jejich žádosti se příjemci nebudou informovat o novém poskytovateli `FileContext` .

## <a name="expensive-file-context-computations"></a>Nákladné výpočty kontextů souborů

Čtení obsahu souboru z disku může být nákladné, zejména v případě, že poskytovatel potřebuje vyřešit vztah mezi soubory. Například poskytovatel může být dotazován pro nějaký kontext souboru zdrojového souboru, ale kontext souboru závisí na metadatech ze souboru projektu. Analýza souboru projektu nebo jeho vyhodnocení pomocí nástroje MSBuild je náročná. Místo toho může rozšíření exportovat `IFileScanner` a vytvořit `FileDataValue` data během indexování pracovního prostoru. Nyní když se zobrazí výzva k kontextům souborů, `IFileContextProvider` může se rychle dotazovat na tato indexovaná data. Další informace o indexování najdete v tématu [indexování pracovního prostoru](workspace-indexing.md) .

>[!WARNING]
>Buďte opatrní i na to, jak vám `FileContext` může být náročné na výpočetní výkon. Některé interakce uživatelského rozhraní jsou synchronní a spoléhají na velké množství `FileContext` požadavků. Mezi příklady patří otevření karty editoru a otevření kontextové nabídky **Průzkumník řešení** . Tyto akce provedou počet požadavků na typ kontextu sestavení.

## <a name="file-context-related-apis"></a>Rozhraní API související s kontextem souborů

- <xref:Microsoft.VisualStudio.Workspace.FileContext> obsahuje data a metadata.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> a <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> vytvořte kontext souboru.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Exportuje zprostředkovatele kontextu souboru.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> slouží k získání kontextů souborů pro příjemce.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> definuje typy kontextu sestavení, které budou využívat otevřené složky.

## <a name="file-context-actions"></a>Akce kontextu souboru

I když `FileContext` se jedná o pouze data o některých souborech, <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> představuje způsob, jak tato data vyjádřit a pracovat s nimi. `IFileContextAction` je flexibilní v používání. Dva z nejběžnějších případů jsou sestavování a ladění.

## <a name="reporting-progress"></a>Průběh generování sestav

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>Metoda je předána `IProgress<IFileContextActionProgressUpdate>` , ale argument by neměl být použit jako tento typ. `IFileContextActionProgressUpdate` je prázdné rozhraní a volání `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` může vyvolat `NotImplementedException` . Místo toho `IFileContextAction` musí přetypování argumentu na jiný typ podle potřeby pro scénář.

Informace o typech poskytovaných aplikací Visual Studio najdete v dokumentaci k příslušnému scénáři.

## <a name="file-context-action-related-apis"></a>Rozhraní API související s akcemi kontextu souboru

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> spustí některé chování založené na `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> Vytvoří instance `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Exportuje typ `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Sledování souborů

Pracovní prostor naslouchá oznámením o změnách souborů a poskytuje <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> prostřednictvím <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Soubory, které odpovídají nastavení "ExcludedItems", nebudou poskytovat události pro oznamování souborů. Prahová hodnota mezi událostmi se používá pro zjednodušení oznámení a při duplicitním zmenšování. Pokud potřebujete reagovat na změnu souboru, měli byste se přihlásit k odběru této služby.

>[!TIP]
>[Služba indexování](workspace-indexing.md) pracovního prostoru se ve výchozím nastavení přihlašuje k odběru událostí souborů. Přidání a úpravy souborů způsobí vyvolání relevantních `IFileScanner` událostí pro nová data pro daný soubor. Odstraněním souborů dojde k odebrání indexovaných dat. Nemusíte přihlašovat `IFileScanner` službu sledovacích procesů souborů.

## <a name="next-steps"></a>Další kroky

* [Indexování](workspace-indexing.md) – indexování pracovních prostorů shromažďuje a uchovává informace o pracovním prostoru.
* [Pracovní prostory](workspaces.md) – kontrola konceptů pracovního prostoru a úložiště nastavení.
