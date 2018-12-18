---
title: Využití RDT_ReadLock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fda2fbb4a4b03dff9d677d9c7581a4138d9fcf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131678"
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock využití

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> je příznak, který obsahuje logiku pro zámek dokumentu v spuštění dokumentu tabulky (r...), což je seznam všech dokumentů, které jsou právě otevřeny v prostředí Visual Studio IDE. Tento příznak určuje, kdy jsou otevřené dokumenty, a jestli je dokument viditelné v uživatelském rozhraní nebo pevné tedy bez zásahu uživatele v paměti.

Obecně byste použili <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> když je splněna jedna z následujících:

- Pokud chcete otevřít dokument, tedy bez zásahu uživatele a jen pro čtení, ale je ještě není vytvořeno, který <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> by měl vlastní.

- Když chcete uživateli výzva k uložení dokumentu, kterou jste otevřeli tedy bez zásahu uživatele předtím, než uživatel zobrazí v uživatelském rozhraní a pak pokus o zavřete ho.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Jak spravovat viditelné a neviditelná dokumenty

Když uživatel otevře dokument v uživatelském rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> vlastníka dokumentu je nutné vytvořit a <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> musí být nastaven příznak. Pokud žádné <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> by bylo možné navázat vlastníka a potom dokument se neuloží, když uživatel klikne **Uložit vše** nebo ukončí rozhraní IDE. To znamená, že pokud dokument je otevřený tedy bez zásahu uživatele tam, kde se mění v paměti a uživatel je vyzván k uložení dokumentu na vypnutí nebo uloženy v případě, **Uložit vše** jste vybrali, pak `RDT_ReadLock` nelze použít. Místo toho musíte použít `RDT_EditLock` a zaregistrujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> při <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> příznak.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock a úpravy dokumentu

Příznak předchozí uvedených označuje, že neviditelná otevření dokumentu předá jeho `RDT_EditLock` při otevření dokumentu uživatel do viditelné **DocumentWindow**. Pokud k tomu dojde, zobrazí se uživateli **Uložit** výzvu, při viditelných **DocumentWindow** je uzavřený. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` implementace, které používají <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> služby zpočátku fungovat, když pouze `RDT_ReadLock` je provedená (tj. při otevření dokumentu tedy bez zásahu uživatele analyzovat informace). Později, pokud je třeba upravit dokumentu, pak zámek inovována na weak **RDT_EditLock**. Pokud uživatel potom otevře dokument viditelné **DocumentWindow**, `CodeModel`je slabé `RDT_EditLock` vydání.

Pokud uživatel poté uzavře **DocumentWindow** a vybere **ne** při zobrazení výzvy k uložení otevřít dokument, pak se `CodeModel` implementaci uvolní všechny informace v dokumentu a znovu otevře dokument z disku tedy bez zásahu uživatele při příštím Další informace jsou nezbytné pro dokument. Subtlety toto chování je instanci, kde uživatel otevře **DocumentWindow** neviditelná otevřít dokument, ho změní, zavře se a potom vybere **ne** po zobrazení výzvy k uložení dokumentu. V tomto případě, pokud má dokument `RDT_ReadLock`, dokument nebude ve skutečnosti je třeba ukončit a změněný dokument zůstanou otevřené v paměti, tedy bez zásahu uživatele, i když se uživatel rozhodl není k uložení dokumentu.

Pokud neviditelná otevření dokumentu se používá weak `RDT_EditLock`, pak vypočítá jeho zámek, když uživatel otevře dokument viditelně a žádné jiné zámky. Když uživatel nezavře **DocumentWindow** a vybere **ne** po zobrazení výzvy k uložení dokumentu, pak dokumentu musí být uzavřeny z paměti. To znamená, že klient neviditelná musí naslouchat událostem r... sledovat tento výskyt. Při příštím dokumentu je požadováno, dokumentu musí být znovu otevřít.