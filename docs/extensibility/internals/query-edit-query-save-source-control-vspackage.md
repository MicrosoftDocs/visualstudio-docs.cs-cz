---
title: Dotaz upravit dotaz uložte (Zdroj ovládacího prvku VSPackage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf4fd74544e0646a84e4fdc37f35ba84b301f693
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131514"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Dotaz upravit dotaz uložte (Zdroj ovládacího prvku VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editory můžete vysílání události dotazu upravit dotaz uložit (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zdroj ovládacího prvku se zakázaným inzerováním implementuje službu QEQS tak, aby se příjemce událostí QEQS. Tyto události jsou pak přeneseny na aktuálně aktivní zdrojového kódu VSPackage. Implementuje VSPackage active zdrojového kódu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> a její metody. Metody `IVsQueryEditQuerySave2` rozhraní se běžně označují jako bezprostředně před první a bezprostředně před uložení dokumentu úpravy dokumentu.  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave události  
 Správa zdrojového kódu VSPackage musí zpracování událostí QEQS implementací `IVsQueryEditQuerySave2` rozhraní a nezbytné metody. Níže je stručný popis dvě metody, které VSPackage musí implementovat minimálně. Skutečná implementace musí být v souladu s logiku ovládacího prvku modelu zdroje.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles – metoda  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> Je volána, když každý projekt nebo editor chce změnit soubor. V ideálním případě by tato metoda je volána *před* úpravy souboru a při uložení souboru. Po vyvolání `IVsQueryEditQuerySave2::QueryEditFiles` metoda ověří, zda jsou dané soubory ve správě zdrojového kódu, jestli budou muset rezervovat a jestli můžete znovu. Pokud okolností zabránit soubory upravovat, `IVsQueryEditQuerySave2::QueryEditFiles` metoda informuje volací program zrušit úpravy. Je také možné pro volajícímu zadat vyvolání režimu. V režimu "bezobslužná" Tato metoda přebírá akce jenom v případě, že nezpůsobí žádné uživatelské rozhraní zobrazit. Pokud uživatelského rozhraní je nevyhnutelné použít, musí být vrácen příznak indikovat problém.  
  
 Metoda chová transakční způsobem; To znamená pokud úpravy je zrušeno při jeden soubor, je zrušená upravit pro všechny soubory. Naopak pokud je povolena úpravy, je povolená pro všechny soubory. Pokud tato metoda umožňuje úpravy jednou pro danou sadu souborů, musí vždy povolit úpravy na následující volání pro stejnou sadu souborů. Povolit úpravy smyčky pokračuje, dokud soubory jsou uzavřen, uložit a znovu načíst; dokud změnit jejich atributů (Vlastnosti); nebo dokud se nezmění zdrojový balíček ovládacího prvku. Případech vzít v úvahu při provádění `IVsQueryEditQuerySave2::QueryEditFiles` metoda zahrnují několik souborů, speciální soubory, zrušte z uživatelů a úpravy v paměti.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles – metoda  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Je volána, když každý projekt nebo editor potřebuje k uložení určitou sadu souborů. Po vyvolání `IVsQueryEditQuerySave2::QuerySaveFiles` metoda prověří, pokud jsou dané soubory jen pro čtení, zda jsou v části Správa zdrojového kódu. Pokud soubory nutné přidělit licenci, volání je delegovaný jako zdrojový balíček ovládacího prvku. Pokud okolností zabránit soubory uloženy, `IVsQueryEditQuerySave2::QuerySaveFiles` metoda musí zjistit editoru ukládání. Stejně jako u `IVsQueryEditQuerySave2::QueryEditFiles` metoda, je možné, volajícímu zadat vyvolání režimu. V režimu "bezobslužná" Tato metoda přebírá akce jenom v případě, že nezpůsobí žádné uživatelské rozhraní zobrazit. Pokud uživatelského rozhraní je nevyhnutelné použít, musí být vrácen příznak indikovat problém.  
  
 Tato metoda musí chovat transakční způsobem; To znamená pokud uložení byla zrušena na jeden soubor, je zrušená uložit všechny soubory. Naopak pokud je povolen uložení, musí být povoleno pro všechny soubory. Stejně jako u `IVsQueryEditQuerySave2::QueryEditFiles` metoda, případech vzít v úvahu při provádění `IVsQueryEditQuerySave2::QuerySaveFiles` metoda zahrnují několik souborů, speciální soubory, zrušte z uživatelů a úpravy v paměti.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>