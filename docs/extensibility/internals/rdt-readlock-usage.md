---
title: RDT_ReadLock použití | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705920"
---
# <a name="rdt_readlock-usage"></a>Využití RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) je příznak, který poskytuje logiku pro uzamčení dokumentu v tabulce spuštěných dokumentů (RDT), což je seznam všech dokumentů, které jsou aktuálně otevřeny v ide sady Visual Studio. Tento příznak určuje, kdy jsou dokumenty otevřeny a zda je dokument viditelný v uživatelském rozhraní nebo držen neviditelně v paměti.

Obecně platí, že používáte [_VSRDTFLAGS. RDT_ReadLock,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) pokud platí jedna z následujících podmínek:

- Chcete otevřít dokument neviditelně a jen pro čtení, ale ještě <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> není stanoven, který by měl vlastnit.

- Chcete, aby byl uživatel vyzván k uložení dokumentu, který byl neviditelně otevřen, než jej uživatel zobrazil v uživatelském rozhraní a poté se jej pokusil zavřít.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Správa viditelných a neviditelných dokumentů

Když uživatel otevře dokument v uživatelském <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní, musí být vytvořen vlastník dokumentu a [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) příznak musí být nastaven. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nelze vytvořit žádného vlastníka, nebude dokument uložen, když uživatel klepne na tlačítko **Uložit vše** nebo zavře rozhraní IDE. To znamená, že pokud je dokument otevřen neviditelně tam, kde je upraven v paměti, a uživatel je vyzván `RDT_ReadLock` k uložení dokumentu při vypnutí nebo uložení, pokud je vybrána možnost **Uložit vše,** nelze použít. Místo toho je `RDT_EditLock` nutné použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> a zaregistrovat při [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) vlajka.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock a úpravy dokumentu

Předchozí příznak uvedené označuje, že neviditelné otevření `RDT_EditLock` dokumentu přinese jeho při otevření dokumentu uživatelem do viditelné **DocumentWindow**. V takovém případě je uživateli zobrazí výzva **Uložit** při zavření **viditelnédocumentwindow.** `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`implementace, které <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> používají službu zpočátku pracovat, když je přijata `RDT_ReadLock` pouze (tj. při otevření dokumentu neviditelně analyzovat informace). Později pokud dokument musí být změněn, pak zámek je upgradován na slabé **RDT_EditLock**. Pokud uživatel pak otevře dokument ve viditelném `CodeModel` **DocumentWindow**, 's slabé `RDT_EditLock` je uvolněna.

Pokud uživatel potom zavře **DocumentWindow** a zvolí **Ne** po zobrazení výzvy `CodeModel` k uložení otevřeného dokumentu, pak implementace naloží všechny informace v dokumentu a znovu otevře dokument z disku neviditelně příště další informace je požadováno pro dokument. Jemnost tohoto chování je instance, kde uživatel otevře **DocumentWindow** neviditelného otevřeného dokumentu, upraví jej, zavře a pak zvolí **Ne,** když se zobrazí výzva k uložení dokumentu. V tomto případě, pokud `RDT_ReadLock`dokument má , pak dokument nebude ve skutečnosti uzavřen a upravený dokument zůstane otevřený neviditelně v paměti, i když se uživatel rozhodl dokument neukládat.

Pokud neviditelné otevření dokumentu používá `RDT_EditLock`slabé , pak dává svůj zámek, když uživatel otevře dokument viditelně a žádné jiné zámky jsou drženy. Když uživatel zavře **DocumentWindow** a zvolí **Ne** po zobrazení výzvy k uložení dokumentu, pak dokument musí být uzavřen z paměti. To znamená, že neviditelný klient musí naslouchat událostem RDT ke sledování tohoto výskytu. Při příštím požadování musí být dokument znovu otevřen.
