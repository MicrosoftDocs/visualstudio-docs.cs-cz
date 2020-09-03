---
title: Uložení dotazu na úpravu dotazu (VSPackage správy zdrojového kódu) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705963"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Události QEQS (Query Edit Query Save) (balíček VSPackage správy zdrojového kódu)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editory můžou vysílat události pro úpravu dotazů QEQS (Query Query Save). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zástupný kód správy zdrojového kódu implementuje službu QEQS, aby byla příjemcem událostí QEQS. Tyto události jsou následně delegovány na aktuálně aktivní správu zdrojového kódu VSPackage. Prvek VSPackage aktivního správy zdrojového kódu implementuje rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> a jeho metody. Metody `IVsQueryEditQuerySave2` rozhraní jsou obvykle volány bezprostředně před první úpravou dokumentu a bezprostředně před uložením dokumentu.

## <a name="queryeditquerysave-events"></a>Události QueryEditQuerySave
 Prvek VSPackage správy zdrojového kódu musí zpracovávat události QEQS implementací `IVsQueryEditQuerySave2` rozhraní a nezbytných metod. Níže je uveden stručný popis dvou metod, které musí VSPackage implementovat minimálně. Skutečná implementace musí být v souladu s logikou modelu správy zdrojového kódu.

### <a name="queryeditfiles-method"></a>Metoda QueryEditFiles
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>Je volána, když kterýkoli projekt nebo editor chce upravit soubor. V ideálním případě je tato metoda volána *před* úpravou souboru a při uložení souboru. Při vyvolání `IVsQueryEditQuerySave2::QueryEditFiles` Metoda zkontroluje, zda jsou zadané soubory pod správou zdrojových kódů, zda je třeba je rezervovat a zda je lze znovu načíst. Pokud okolnosti zabraňují úpravám souborů, `IVsQueryEditQuerySave2::QueryEditFiles` Metoda sdělí volajícímu programu, aby zrušil úpravy. Volající je také možné zadat režim vyvolání. V režimu ticha Tato metoda provádí akci pouze v případě, že nezpůsobí zobrazení uživatelského rozhraní. Pokud je uživatelské rozhraní nenevyhnutelné, musí být vrácen příznak pro indikaci problému.

 Metoda se chová transakčním způsobem; To znamená, že pokud se úprava zruší v jednom souboru, úpravy se zruší pro všechny soubory. Naopak, pokud je povolená úprava, je povolená pro všechny soubory. Pokud tato metoda umožňuje úpravy pro danou sadu souborů, musí vždy povolit úpravy při dalších voláních stejné sady souborů. Cyklus povolených úprav pokračuje, dokud nebudou soubory zavřeny, uloženy a znovu načteny. dokud se nezmění jejich atributy (vlastnosti); nebo dokud se nezmění balíček správy zdrojového kódu. Případy, které je třeba vzít v úvahu při implementaci `IVsQueryEditQuerySave2::QueryEditFiles` metody, zahrnují více souborů, speciální soubory, zrušení od uživatele a úpravy v paměti.

### <a name="querysavefiles-method"></a>Metoda QuerySaveFiles
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>Je volána, když kterýkoli projekt nebo editor potřebuje uložit sadu souborů. Při vyvolání `IVsQueryEditQuerySave2::QuerySaveFiles` Metoda zkontroluje, zda jsou zadané soubory jen pro čtení a zda jsou pod správou zdrojových kódů. Pokud je nutné soubory rezervovat, volání je delegováno do balíčku správy zdrojového kódu. Pokud okolnosti zabraňují ukládání souborů, `IVsQueryEditQuerySave2::QuerySaveFiles` musí metoda sdělit editoru, aby se uložilo. Stejně jako u `IVsQueryEditQuerySave2::QueryEditFiles` metody je možné, aby volající určil režim vyvolání. V režimu ticha Tato metoda provádí akci pouze v případě, že nezpůsobí zobrazení uživatelského rozhraní. Pokud je uživatelské rozhraní nenevyhnutelné, musí být vrácen příznak pro indikaci problému.

 Tato metoda se musí chovat transakčním způsobem; To znamená, že pokud se uložení zruší v jednom souboru, uložení se zruší pro všechny soubory. Naopak, pokud je ukládání povoleno, musí být povoleno pro všechny soubory. Stejně jako u `IVsQueryEditQuerySave2::QueryEditFiles` metody by případy, které je třeba vzít v úvahu při implementaci `IVsQueryEditQuerySave2::QuerySaveFiles` metody, zahrnovaly více souborů, speciální soubory, zrušit od uživatele a úpravy v paměti.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
