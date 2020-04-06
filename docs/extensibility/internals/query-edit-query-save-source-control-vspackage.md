---
title: Soubor Query Edit Query Save (Source Control VSPackage) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705963"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Události QEQS (Query Edit Query Save) (balíček VSPackage správy zdrojového kódu)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]redakce mohou vysílat události query edit query save (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Správce dat se zakázaným inzerováním implementuje službu QEQS tak, aby byla příjemcem událostí QEQS. Tyto události jsou pak delegovány na aktuálně aktivní zdrojový prvek VSPackage. Aktivní zdrojový prvek VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> implementuje a jeho metody. Metody `IVsQueryEditQuerySave2` rozhraní jsou obvykle volány bezprostředně před úpravou dokumentu poprvé a bezprostředně před uložením dokumentu.

## <a name="queryeditquerysave-events"></a>Události QueryEditQuerySave
 Zdroj ovládacího prvku VSPackage musí zpracovat qeqs události implementací `IVsQueryEditQuerySave2` rozhraní a nezbytné metody. Níže je stručný popis dvou metod, které VSPackage musí implementovat minimálně. Skutečná implementace musí být v souladu s logikou modelu správy zdrojového kódu.

### <a name="queryeditfiles-method"></a>Metoda QueryEditFiles
 Je <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> volána, když jakýkoli projekt nebo editor chce upravit soubor. V ideálním případě je tato metoda volána *před* změnou souboru a při uložení souboru. Při vyvolání `IVsQueryEditQuerySave2::QueryEditFiles` metoda zkontroluje, zda jsou dané soubory pod správou zdrojového kódu, zda je třeba je rezervovat a zda je lze znovu načíst. Pokud okolnosti brání upravovat soubory, `IVsQueryEditQuerySave2::QueryEditFiles` metoda sděluje volajícímu programu zrušit úpravy. Je také možné pro volajícího zadat režim vyvolání. V režimu "tichý" tato metoda provede akci pouze v případě, že nezpůsobí žádné ui se zobrazí. Pokud je ui nevyhnutelné, příznak musí být vrácena k označení problému.

 Metoda se chová transakčním způsobem; to znamená, že pokud je úprava zrušena u jednoho souboru, je úprava zrušena pro všechny soubory. Naopak, pokud je úprava povolena, je povolena pro všechny soubory. Pokud tato metoda umožňuje úpravy jednou pro danou sadu souborů, musí vždy povolit úpravy na následné volání pro stejnou sadu souborů. Smyčka pro úpravy povolení pokračuje, dokud nejsou soubory uzavřeny, uloženy a znovu načteny; dokud se nezmění jejich atributy (vlastnosti); nebo dokud nebude změněn balíček správy zdrojového kódu. Případy, které je `IVsQueryEditQuerySave2::QueryEditFiles` třeba zvážit při implementaci metody, zahrnují více souborů, speciální soubory, zrušení od uživatele a úpravy v paměti.

### <a name="querysavefiles-method"></a>Metoda QuerySaveFiles
 Je <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> volána, když jakýkoli projekt nebo editor potřebuje uložit sadu souborů. Při vyvolání `IVsQueryEditQuerySave2::QuerySaveFiles` metoda zkontroluje, zda jsou dané soubory jen pro čtení a zda jsou pod smytí zdrojového kódu. Pokud soubory je třeba rezervovat, volání je delegována na balíček správy zdrojového kódu. Pokud okolnosti brání ukládání souborů, `IVsQueryEditQuerySave2::QuerySaveFiles` musí metoda sdělit editoru, aby zrušil uložení. Stejně `IVsQueryEditQuerySave2::QueryEditFiles` jako u metody je možné pro volajícího určit režim vyvolání. V režimu "tichý" tato metoda provede akci pouze v případě, že nezpůsobí žádné ui se zobrazí. Pokud je ui nevyhnutelné, příznak musí být vrácena k označení problému.

 Tato metoda se musí chovat transakčním způsobem; to znamená, že pokud je uložení zrušeno u jednoho souboru, je uložení zrušeno pro všechny soubory. Naopak, pokud je uložení povoleno, musí být povoleno pro všechny soubory. Stejně `IVsQueryEditQuerySave2::QueryEditFiles` jako u metody, případy, `IVsQueryEditQuerySave2::QuerySaveFiles` které je třeba zvážit při implementaci metody, zahrnují více souborů, speciální soubory, zrušení od uživatele a úpravy v paměti.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
