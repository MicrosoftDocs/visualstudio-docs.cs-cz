---
title: Využití RDT_ReadLock | Microsoft Docs
description: Přečtěte si o _VSRDTFLAGS. Příznak RDT_ReadLock, který poskytuje logiku pro uzamykání dokumentu v běžící tabulce dokumentů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6add02e763c9664c19fe21b1cfc37dd29b3010b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060832"
---
# <a name="rdt_readlock-usage"></a>Využití RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) je příznak, který poskytuje logiku pro uzamykání dokumentu v běžící tabulce dokumentů (RDT), což je seznam všech dokumentů, které jsou aktuálně otevřeny v integrovaném vývojovém prostředí sady Visual Studio. Tento příznak určuje, kdy jsou otevřeny dokumenty a zda je dokument viditelný v uživatelském rozhraní nebo je držen v paměti.

Obecně se používá [_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) , pokud je splněna jedna z následujících podmínek:

- Chcete otevřít dokument, který je v neviditelném a jen pro čtení, ale ještě není vytvořený, což <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> by měl být vlastní.

- Požadujete, aby se uživateli zobrazila výzva k uložení dokumentu, který byl neviditelně otevřen předtím, než ho uživatel zobrazil v uživatelském rozhraní, a pak se pokusil jej zavřít.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Správa viditelných a neviditelných dokumentů

Když uživatel otevře dokument v uživatelském rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> musí být vytvořen vlastník dokumentu a [_VSRDTFLAGS. ](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) Musí být nastaven příznak RDT_EditLock. Pokud není <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> možné navázat žádného vlastníka, dokument se neuloží, když uživatel klikne na **Uložit vše** nebo zavře IDE. To znamená, že pokud je dokument otevřený v paměti, kde je upravený, a uživatel se zobrazí výzva k uložení dokumentu při vypnutí nebo uložení, pokud je zvolena možnost **Uložit vše** , `RDT_ReadLock` nelze použít. Místo toho je nutné `RDT_EditLock` při __VSREGDOCLOCKHOLDER použít a registrovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> [. Příznak RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) .

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock a úpravy dokumentu

Výše zmíněný příznak indikuje, že neviditelné otevření dokumentu vrátí, když ho `RDT_EditLock` uživatel otevře v viditelném **DocumentWindow**. Pokud k tomu dojde, zobrazí se uživateli při zavření viditelného **DocumentWindow** výzvy k **uložení** . `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` implementace, které používají <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> službu jako první, v případě `RDT_ReadLock` , že je provedena pouze operace (tj. když je dokument otevřen pro analýzu informací). Později, pokud je potřeba dokument upravit, zámek se upgraduje na slabý **RDT_EditLock**. Pokud uživatel potom otevře dokument v viditelném **DocumentWindow**, `CodeModel` je jeho vydání slabé `RDT_EditLock` .

Pokud uživatel potom zavře **DocumentWindow** a při zobrazení výzvy k uložení otevřeného dokumentu zvolí možnost **ne** , pak implementace uvolní `CodeModel` všechny informace v dokumentu a znovu ho otevře z disku, a to i příště, než se další informace pro dokument vyžadují. Subtlety tohoto chování je instance, ve které uživatel otevře **DocumentWindow** neviditelného otevřeného dokumentu, změní ho, zavře ho a po zobrazení výzvy k uložení dokumentu vybere **ne** . V takovém případě, pokud dokument má `RDT_ReadLock` , dokument ve skutečnosti nebude zavřen a upravený dokument zůstane otevřený v paměti, i když uživatel neuloží dokument.

Pokud neviditelné otevření dokumentu používá slabý `RDT_EditLock` , pak vrátí jeho zámek, když uživatel otevře dokument viditelně a žádné další zámky nebudou uloženy. Když uživatel zavře **DocumentWindow** a při zobrazení výzvy k uložení dokumentu zvolí **ne** , musí být dokument uzavřený z paměti. To znamená, že neviditelný klient musí naslouchat událostem RDT, aby mohl sledovat tento výskyt. Při dalším požadavku dokumentu musí být dokument znovu otevřen.
