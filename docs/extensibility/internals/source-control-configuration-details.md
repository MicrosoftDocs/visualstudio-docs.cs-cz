---
title: Podrobnosti o konfiguraci správy zdrojového kódu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a6c51dfe4ad9378af04da61dbd7e9011c4678f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723799"
---
# <a name="source-control-configuration-details"></a>Podrobnosti konfigurace správy zdrojového kódu
Aby bylo možné implementovat správu zdrojového kódu, je nutné správně nakonfigurovat systém projektu nebo editor, aby bylo možné provést následující akce:

- Požádat o oprávnění k přechodu na změněný stav

- Požádat o oprávnění k uložení souboru

- Požádat o oprávnění k přidání, odebrání nebo přejmenování souborů v projektu

## <a name="request-permission-to-transition-to-changed-state"></a>Požádat o oprávnění k přechodu na změněný stav
 Projekt nebo editor musí požádat o oprávnění k přechodu do změněného (nečistého) stavu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Každý editor, který implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> musí volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a přijmout schválení pro změnu dokumentu z prostředí před vrácením `True` pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Projekt je v podstatě editor pro soubor projektu a výsledkem je stejná zodpovědnost za implementaci sledování změny stavu projektu jako textový editor pro jeho soubory. Prostředí zpracovává změněný stav řešení, ale je nutné zpracovat změněný stav libovolného objektu, který řešení odkazuje, ale neukládá, jako soubor projektu nebo jeho položky. Obecně platí, že pokud je váš projekt nebo editor zodpovědný za správu trvalosti položky, zodpovídá za implementaci sledování stavu změny.

 V reakci na volání `IVsQueryEditQuerySave2::QueryEditFiles` může prostředí provádět následující akce:

- Zamítnout volání ke změně. v takovém případě musí Editor nebo projekt zůstat ve stavu Unchanged (Clean).

- Označuje, že se data dokumentu mají znovu načíst. V případě projektu prostředí znovu nasadí data projektu. Editor musí znovu načíst data z disku prostřednictvím implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>. V obou případech se kontext v projektu nebo editoru může změnit, když jsou data znovu načtena.

  Je to složitá a obtížná úloha pro zpětnému pozměněníí příslušných `IVsQueryEditQuerySave2::QueryEditFiles` volání do stávající základny kódu. V důsledku toho by tato volání měla být integrována během vytváření projektu nebo editoru.

## <a name="request-permission-to-save-a-file"></a>Požádat o oprávnění k uložení souboru
 Před tím, než projekt nebo editor uloží soubor, musí volat <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Pro soubory projektu jsou tato volání automaticky dokončena řešením, které ví, kdy uložit soubor projektu. Editory jsou zodpovědné za provedení těchto volání, pokud Editor implementace `IVsPersistDocData2` nepoužívá pomocnou funkci <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Pokud editor implementuje `IVsPersistDocData2` tímto způsobem, pak volání `IVsQueryEditQuerySave2::QuerySaveFile` nebo `IVsQueryEditQuerySave2::QuerySaveFiles` je provedeno za vás.

> [!NOTE]
> Tyto výzvy vždy provedete bez přerušení – tedy v době, kdy je váš Editor schopný přijmout zrušení.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Požádat o oprávnění k přidání, odebrání nebo přejmenování souborů v projektu
 Předtím, než projekt může přidat, přejmenovat nebo odebrat soubor nebo adresář, musí volat příslušnou metodu `IVsTrackProjectDocuments2::OnQuery*` pro vyžádání oprávnění z prostředí. Pokud je uděleno oprávnění, projekt musí dokončit operaci a poté zavolat příslušnou metodu `IVsTrackProjectDocuments2::OnAfter*` pro informování prostředí, že operace byla dokončena. Projekt musí volat metody rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> pro všechny soubory (například speciální soubory) a ne pouze nadřazené soubory. Volání souborů jsou povinná, ale volání adresáře jsou volitelná. Pokud má váš projekt informace o adresáři, pak by měl volat příslušné <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> metody, ale pokud tyto informace neobsahuje, bude prostředí odvodit informace o adresáři.

 Projekt by neměl volat metody `IVsTrackProjectDocuments2` v projektu otevřít nebo zavřít. Naslouchací procesy, které chtějí tyto informace při spuštění, můžou počkat na událost <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> a iterovat přes řešení, aby našli informace, které potřebují. Při vypnutí se tyto informace nevyžadují. `IVsTrackProjectDocuments2` k dispozici z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Pro každou akci přidání, přejmenování a odebrání je k dispozici `OnQuery*` metoda a metoda `OnAfter*`. Voláním metody `OnQuery*` můžete požádat o oprávnění k přidání, přejmenování nebo odebrání souboru nebo adresáře. Po přidání, přejmenování nebo odebrání souboru nebo adresáře volejte metodu `OnAfter*` a stav projektu odpovídá novému stavu.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)