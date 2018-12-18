---
title: Kontexty souboru pracovního prostoru v sadě Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146348"
---
# <a name="workspace-file-contexts"></a>Kontexty souboru pracovního prostoru

Všechny přehledy [otevřít složku](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) "soubor kontextu zprostředkovatelé" které implementují vytváří pracovní prostory <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> rozhraní. Tato rozšíření může vypadat vzorů ve složkách nebo souborů, číst soubory nástroje MSBuild a soubory pravidel, zjištění závislosti balíčků, atd. Chcete-li hromadit statistiky, že které potřebují k definovat kontext souboru. Kontext souboru sám o sobě neprovede žádnou akci, ale spíš poskytuje data, která může jinou příponu pak fungovat na.

Každý <xref:Microsoft.VisualStudio.Workspace.FileContext> má `Guid` přidruženo označující typ dat se má u sebe. Toto nastavení použije pracovního prostoru `Guid` později na spárujte ho s rozšířeními, která využívají data pomocí <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> vlastnost. Kontext zprostředkovatele souboru je exportovaný s metadata, která identifikuje které kontext souboru `Guid`s ji může vytvořit data.

Po definování kontext souboru lze přidružit libovolný počet soubory nebo složky v pracovním prostoru. Daný soubor nebo složka může být přidružen libovolný počet kontexty souboru. Je relace m: n.

Nejběžnější scénáře pro kontexty soubor souvisí s sestavení, ladění a jazyk služby. Další informace najdete v tématu na další témata týkající se těchto scénářů.

## <a name="file-context-lifecycle"></a>Životní cyklus kontextu souboru

Časově omezené `FileContext` jsou není deterministický. Kdykoli můžete komponentu asynchronně žádost pro některé sadu kontextové typy. Zprostředkovatelé, kteří podporují určitou podmnožinu typy kontext požadavku bude dotaz. `IWorkspace` Instance funguje jako střední man mezi příjemce a poskytovatelé prostřednictvím <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> metoda. Příjemce může kontext požadavku a provedení některých krátkodobé akce na základě kontextu, zatímco ostatní může kontext požadavku a udržování dlouho povahy odkazů. 

Změny, může dojít k souborům, které způsobí kontext souboru k začnou být zastaralé. Zprostředkovatel můžete aktivovat událost na `FileContext` oznámení příjemci aktualizací. Například pokud kontext sestavení je k dispozici pro některé soubor ale o změnu na disku by způsobila neplatnost tohoto kontextu, pak původní producent vyvolat událost. Nějaké příjemce, který stále odkazuje `FileContext` pak opakovat dotaz pro novou `FileContext`.

>[!NOTE]
>Neexistuje žádný model push k příjemce. Příjemci nebudete nijak upozorněni zprostředkovatele nové `FileContext` po jeho žádost.

## <a name="expensive-file-context-computations"></a>Výpočty kontextu nákladné souboru

Obsah souboru čtení z disku může být náročné, zejména v případě, že zprostředkovatel je nutné přeložit vztah mezi soubory. Například zprostředkovatele může být dotazována pro kontext souboru některé zdrojový soubor, ale soubor kontextu je závislá na metadat ze souboru projektu. Analýza souboru projektu nebo vyhodnocení pomocí nástroje MSBuild je nákladné. Místo toho můžete exportovat rozšíření `IFileScanner` k vytvoření `FileDataValue` dat během indexování pracovního prostoru. Nyní když se zobrazí dotaz pro soubor kontexty `IFileContextProvider` můžete rychle vyhledat indexované data. Další informace o indexování, najdete v článku [prostoru indexování](workspace-indexing.md) tématu.

>[!WARNING]
>Buďte opatrní další způsoby, vaše `FileContext` může být nákladné k výpočtu. Některé interakce uživatelského rozhraní jsou synchronní a využívají k velkému počtu `FileContext` požadavky. Mezi příklady patří otevírání karta editoru a otevírání **Průzkumníku řešení** kontextové nabídky. Tyto akce zkontrolujte mnoho sestavení kontextu, zadejte požadavky.

## <a name="file-context-related-apis"></a>Rozhraní API související s kontext souboru

- <xref:Microsoft.VisualStudio.Workspace.FileContext> obsahuje data a metadata.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> a <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> vytvořit soubor kontext.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> Exportuje zprostředkovatele kontextu souboru.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> slouží k příjemce získat soubor kontexty.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Definuje sestavení kontextové typy, které bude využívat otevřít složku.

## <a name="file-context-actions"></a>Soubor kontext akce

Když `FileContext` sám o sobě představuje jen data o některých souborů <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> je způsob, jak express a provádění akcí na tato data. `IFileContextAction` je flexibilní v jeho použití. Dva z jeho nejběžnější případy jsou sestavování a ladění.

## <a name="reporting-progress"></a>Vytvoření sestavy průběhu

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> Metodě se předává `IProgress<IFileContextActionProgressUpdate>`, ale argument nesmí se používat jako typu. `IFileContextActionProgressUpdate` je prázdný rozhraní a vyvolání `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` může vyvolat `NotImplementedException`. Místo toho `IFileContextAction` musíte vysílat argumentem k jinému typu podle potřeby pro scénář.

Informace o typech poskytl Visual Studio najdete v dokumentaci k příslušné scénář.

## <a name="file-context-action-related-apis"></a>Rozhraní API související s souboru kontext akce

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> provádí některé chování na základě `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> vytváří instance `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> Exportuje typ `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Sledování souborů

Pracovní prostor naslouchá na oznámení změn v souboru a poskytuje <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> prostřednictvím <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. Soubory odpovídající nastavení "ExcludedItems" nebude vytvořit soubor oznámení události. Prahová hodnota mezi události se používá pro zjednodušení oznámení a snížení duplicitní. Když potřebujete reagovat na změnu souboru, by se přihlásíte k této službě.

>[!TIP]
>Pracovní prostor [indexování služby](workspace-indexing.md) přihlásí k událostem soubor ve výchozím nastavení. Přidání souborů a úpravy způsobí relevantní `IFileScanner`s události zavolat pro nová data pro tento soubor. Odstranění souboru odebere indexovaná data. Nemusíte přihlášení k odběru vaší `IFileScanner` ke službě souboru sledovacích procesů.

## <a name="next-steps"></a>Další kroky

* [Indexování](workspace-indexing.md) -prostoru indexování shromažďuje a udržuje informace o pracovní prostor.
* [Pracovní prostory](workspaces.md) – prostudujte si koncepty prostoru a nastavení úložiště.
