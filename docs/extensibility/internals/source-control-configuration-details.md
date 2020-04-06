---
title: Podrobnosti konfigurace správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705284"
---
# <a name="source-control-configuration-details"></a>Podrobnosti konfigurace správy zdrojového kódu
Chcete-li implementovat správou zdrojového kódu, je třeba správně nakonfigurovat systém nebo editor projektu takto:

- Požádat o povolení k přechodu do změněného stavu

- Žádost o oprávnění k uložení souboru

- Žádost o oprávnění k přidání, odebrání nebo přejmenování souborů v projektu

## <a name="request-permission-to-transition-to-changed-state"></a>Požádat o oprávnění k přechodu do změněného stavu
 Projekt nebo editor musí požádat o oprávnění k přechodu do změněného (dirty) stavu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Každý editor, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> který <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> implementuje musí volat a přijímat schválení `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>změnit dokument z prostředí před návratem pro . Projekt je v podstatě editor pro soubor projektu a jako výsledek má stejnou odpovědnost za implementaci sledování změněného stavu pro soubor projektu jako textový editor pro jeho soubory. Prostředí zpracovává změněný stav řešení, ale je nutné zpracovat změněný stav libovolného objektu, na který řešení odkazuje, ale neukládá, jako je soubor projektu nebo jeho položky. Obecně platí, že pokud váš projekt nebo editor je zodpovědný za správu trvalosti pro položku, pak je zodpovědný za implementaci sledování změněného stavu.

 V reakci `IVsQueryEditQuerySave2::QueryEditFiles` na volání prostředí může provést následující:

- Odmítnout volání změnit, v takovém případě editor nebo projekt musí zůstat v nezměněném (čistém) stavu.

- Označte, že data dokumentu by měla být znovu načtena. Pro projekt prostředí znovu načte data pro projekt. Editor musí znovu načíst data <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> z disku prostřednictvím jeho implementace. V obou případech kontext v projektu nebo editoru můžete změnit při opětovném načtení dat.

  Jedná se o složitý a obtížný `IVsQueryEditQuerySave2::QueryEditFiles` úkol dovybavit odpovídající volání na existující základ kódu. V důsledku toho by tyto výzvy měly být integrovány při vytváření projektu nebo editoru.

## <a name="request-permission-to-save-a-file"></a>Žádost o oprávnění k uložení souboru
 Před uložením souboru musí projekt nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>editor volat nebo . U souborů projektu jsou tato volání automaticky dokončena řešením, které ví, kdy uložit soubor projektu. Editory jsou odpovědné za provádění těchto `IVsPersistDocData2` volání, pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>editor implementace používá pomocnou funkci . Pokud váš editor `IVsPersistDocData2` implementuje tímto `IVsQueryEditQuerySave2::QuerySaveFile` způsobem, pak volání nebo `IVsQueryEditQuerySave2::QuerySaveFiles` je za vás.

> [!NOTE]
> Vždy uskutečujte tato volání preventivně – to znamená v době, kdy editor může přijímat zrušení.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Žádost o oprávnění k přidání, odebrání nebo přejmenování souborů v projektu
 Před přidáním, přejmenováním nebo odebráním souboru nebo adresáře musí projekt zavolat příslušnou `IVsTrackProjectDocuments2::OnQuery*` metodu a požádat o oprávnění z prostředí. Pokud je uděleno oprávnění, pak projekt musí dokončit `IVsTrackProjectDocuments2::OnAfter*` operaci a potom volání příslušné metody upozornit prostředí, že operace je dokončena. Projekt musí volat metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> rozhraní pro všechny soubory (například speciální soubory) a nikoli pouze nadřazené soubory. Volání souborů jsou povinná, ale volání adresáře jsou volitelná. Pokud projekt obsahuje informace o adresáři, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> měl by volat příslušné metody, ale pokud tyto informace nemá, bude prostředí odvodit informace o adresáři.

 Projekt by neměl volat `IVsTrackProjectDocuments2` metody při otevření nebo zavření projektu. Naslouchací procesy, které <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> chtějí tyto informace při spuštění můžete čekat na událost a iterovat prostřednictvím řešení najít informace, které potřebují. Při vypnutí nejsou tyto informace potřeba. `IVsTrackProjectDocuments2`je poskytována <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>z .

 Pro každou akci přidání, přejmenování a `OnQuery*` odebrání existuje `OnAfter*` metoda a metoda. Volání `OnQuery*` maješku požádat o oprávnění k přidání, přejmenování nebo odebrání souboru nebo adresáře. Volání `OnAfter*` metody po souboru nebo adresáře byla přidána, přejmenována nebo odebrána a stav projektu odráží nový stav.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
