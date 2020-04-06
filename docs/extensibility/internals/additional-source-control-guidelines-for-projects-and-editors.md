---
title: Další pokyny pro řízení zdrojového kódu pro projekty a editory | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710112"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Další pokyny pro směřač zdroje pro projekty a editory
Existuje celá řada pokynů, které by projekty a editory měly dodržovat, aby podporovaly správě zdrojového kódu.

## <a name="guidelines"></a>Pokyny
 Projekt nebo editor by měl také provést následující akce pro podporu správy zdrojového kódu:

|Oblast|Project|Editor|Podrobnosti|
|----------|-------------|------------|-------------|
|Soukromé kopie souborů|×||Prostředí podporuje soukromé kopie souborů. To znamená, že každá osoba zařazená do projektu má svou vlastní soukromou kopii souborů v tomto projektu.|
|Přetrvávání ansi/unicode|×|×|Pokud píšete kód trvalosti, uchovávejte soubory ve formuláři ANSI, protože většina programů správy zdrojového kódu aktuálně nepodporuje kódování Unicode.|
|Výčet souborů|×||Projekt musí obsahovat konkrétní seznam všech souborů v něm a musí být schopen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> vytvořit <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> výčet seznamu souborů pomocí nebo (VSH_PROPID_First_Child/Next_Sibling). Projekt by měl také vystavit <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> názvy položek prostřednictvím jeho provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> a podporu vyhledávání názvů (včetně speciálních souborů) prostřednictvím jeho implementace.|
|Formát textu|×|×|Pokud je to možné, soubory by měly být v textovém formátu pro podporu slučování různých verzí. Soubory, které nejsou v textovém formátu, nelze později sloučit s jinými verzemi souboru. Upřednostňovaný textový formát je XML.|
|Na základě odkazu|×||Projekty založené na odkazech jsou snadno podporovány ve správě zdrojového kódu. Projekty založené na adresáři jsou však také podporovány správy zdrojového kódu tak dlouho, dokud projekt může vytvořit seznam svých souborů na vyžádání, bez ohledu na to, zda tyto soubory existují na disku. Při otevírání projektu ze správy zdrojového kódu je soubor projektu nejprve přenesen před všechny jeho soubory.|
|Zachovat objekty a vlastnosti v předvídatelném pořadí|×|×|Uchovávejte soubory v předvídatelném pořadí, například v abecedním pořadí, abyste usnadnili slučování.|
|Načíst znovu|×|×|Při změně souboru na disku musí být editor schopen jej znovu načíst. Když se účastníte správy zdrojového kódu, prostředí znovu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> načte data za vás voláním implementace. Nejtěžší případ opětovného načtení je, když dojde k pokladně, když jste<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> zavolali IVsQueryEditQuerySave:: a zpracováváte informace. Však znovu načíst kód musí být možné spustit v této situaci.<br /><br /> Prostředí automaticky znovu načte soubory projektu. Projekt však musí <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> implementovat, pokud má vnořené hierarchie pro podporu opětovného načtení vnořených souborů projektu.|

## <a name="see-also"></a>Viz také
- [Podpora správy zdrojového kódu](../../extensibility/internals/supporting-source-control.md)
