---
title: Pokyny pro správu zdrojového kódu pro projekty a editory
description: Seznamte se s pokyny, které by projekty a editory měly dodržovat, aby bylo možné podporovat správu zdrojového kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdd7e23840701981eaea46b44355c34b55b37a33
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190132"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Další pokyny pro správu zdrojového kódu pro projekty a editory
K dispozici je řada zásad, které by projekty a editory měly dodržovat, aby bylo možné podporovat správu zdrojového kódu.

## <a name="guidelines"></a>Pokyny
 Pro podporu správy zdrojového kódu by měl váš projekt nebo Editor také provádět následující akce:

|Oblast|Project|Editor|Podrobnosti|
|----------|-------------|------------|-------------|
|Soukromé kopie souborů|X||Prostředí podporuje soukromé kopie souborů. To znamená, že každá osoba zařazená v projektu má svou vlastní soukromou kopii souborů v tomto projektu.|
|Trvalost ANSI/Unicode|X|X|Zapíšete-li kód trvalosti, zachovejte soubory ve formátu ANSI, protože většina programů pro správu zdrojového kódu aktuálně nepodporuje kódování Unicode.|
|Zobrazení výčtu souborů|X||Projekt musí obsahovat konkrétní seznam všech souborů, které jsou v něm obsaženy, a musí být schopný vytvořit výčet seznamu souborů pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Projekt by měl také vystavovat názvy položek prostřednictvím jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> implementace a hledání názvu podpory (včetně speciálních souborů) prostřednictvím jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> implementace.|
|Formát textu|X|X|Pokud je to možné, měly by být soubory v textovém formátu, aby podporovaly slučování různých verzí. Soubory, které nejsou ve formátu textu, nelze sloučit s jinými verzemi souboru později. Upřednostňovaný textový formát je XML.|
|Založené na odkazech|X||Projekty založené na odkazech jsou ve správě zdrojového kódu snadno podporovány. Nicméně projekty založené na adresářích jsou podporovány také správou zdrojového kódu, pokud projekt může vytvořit seznam svých souborů na vyžádání bez ohledu na to, zda tyto soubory existují na disku. Při otevírání projektu ze správy zdrojového kódu je soubor projektu před jakýmkoli z jeho souborů nejprve vydaný.|
|Zachovat objekty a vlastnosti v předvídatelném pořadí|X|X|Zachovejte soubory v předvídatelném pořadí, například v abecedním pořadí, abyste usnadnili sloučení.|
|Načíst znovu|X|X|Při změně souboru na disku musí být Editor schopný ho znovu načíst. Při účasti na správě zdrojového kódu prostředí znovu načte data za vás voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implementace. Nejobtížnějším případem opakovaného načtení je situace, kdy k rezervaci dojde, když jste volali IVsQueryEditQuerySave:: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a jsou zpracovávány informace. Váš kód pro opětovné načtení ale musí být schopný v této situaci spustit.<br /><br /> Prostředí automaticky znovu načte soubory projektu. Projekt však musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> , pokud má vnořené hierarchie pro podporu opětovného načtení vnořených souborů projektu.|

## <a name="see-also"></a>Viz také
- [Podpora správy zdrojů](../../extensibility/internals/supporting-source-control.md)
