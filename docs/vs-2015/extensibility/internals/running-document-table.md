---
title: Spuštění tabulky dokumentů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd7b8cd44c72ea058f71575bdd1774efafa86731
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746304"
---
# <a name="running-document-table"></a>Spuštění tabulky dokumentů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozhraní IDE udržuje seznam všech aktuálně otevřených dokumentů v vnitřní struktury nazvané spuštěnou tabulku dokumentů (r...). Tento seznam obsahuje všechny otevřené dokumenty v paměti, bez ohledu na to, zda tyto dokumenty jsou právě upravována. Dokument je všechny položky, které se ukládají, včetně souborů v projektu nebo souboru hlavního projektu (například soubor .vcxproj).  
  
## <a name="elements-of-the-running-document-table"></a>Prvky spuštěná tabulka dokumentů  
 Spuštění tabulky dokumentů obsahuje následující položky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Zástupný název dokumentu|Řetězec, který jednoznačně identifikuje datový objekt dokumentu. To může být absolutní cestu k souboru pro projekt systému, který spravuje soubory (například C:\MyProject\MyFile). Tento řetězec se používá také pro projekty, které jsou uloženy v jiných úložišť než systémy souborů, jako jsou uložené procedury v databázi. V takovém případě systém projektu díky jedinečný řetězec, který může rozpoznat a pravděpodobně analyzovat určit, jak má dokument uložit.|  
|Hierarchie vlastníka|Objekt hierarchie, která vlastní dokumentu, reprezentovaný hodnotou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní.|  
|ID položky|Identifikátor položky pro konkrétní položky v rámci hierarchie. Tato hodnota je jedinečný mezi všechny dokumenty v hierarchii, který vlastní tento dokument, ale tato hodnota nemusí být jedinečný v rámci jiné hierarchie.|  
|Datový objekt dokumentu|Na minimum a jde `IUnknown`<br /><br /> objekt. Rozhraní IDE nevyžaduje žádné konkrétní rozhraní nad rámec `IUnknown` rozhraní pro vlastní editor dokumentu datový objekt. Ale pro standardní editor editoru provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> rozhraní je vyžadován ke zpracování volání trvalého souboru z projektu. Další informace najdete v tématu [ukládání standardní dokumentu](../../extensibility/internals/saving-a-standard-document.md).|  
|Příznaky|Položky jsou přidány do rámcový lze zadat příznaky, které řídí, jestli je dokument uložen, zda použít zámek pro čtení nebo úpravy a tak dále. Další informace najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> výčtu.|  
|Upravit počet zámků|Počet úprav, které se uzamkne. Upravit Zámek znamená, že některé editor má dokument otevřený pro úpravy. Když počet zámků úpravy převede na hodnotu nula, bude uživatel vyzván k uložení dokumentu, pokud byl změněn. Například pokaždé, když se dokument otevřít v editoru pomocí **nové okno** příkazu, přidá se úpravy zámku pro tohoto dokumentu r.... Uzamčení zařízení upravit nastavení, dokument musí mít hierarchii nebo položky ID.|  
|Počet zámků pro čtení|Počet čtení zámků. Zámek pro čtení znamená, že dokument je čten pomocí některé mechanismus, jako je průvodce. Zámek pro čtení obsahuje dokument zachován v rámcový při označující, že dokument nelze upravit. Můžete nastavit zámek pro čtení i v případě, že dokument neobsahuje hierarchii nebo položky ID. Tato funkce umožňuje dokument otevřít v paměti a zadejte ho na rámcový bez dokumentu vlastněné žádné hierarchie. Tato funkce slouží jen zřídka.|  
|Vlastník zámku|Instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Vlastník zámku implementují funkce, jako jsou průvodci, které otevírat a upravovat dokumenty mimo editor. Vlastník zámku umožňuje funkci Přidat uzamčení úpravy dokumentu, který má zabránit zavírá, zatímco je stále upravovaný dokumentu. Za normálních okolností upravit zámky jsou přidány pouze okna dokumentu (to znamená, editory).|  
  
 Každá položka r... má jedinečný hierarchie nebo ID položky související s ním, která obvykle odpovídá na jeden uzel v projektu. Všechny dokumenty, které jsou k dispozici pro úpravy jsou obvykle vlastní hierarchii. Zápisy rámcový řídit kterého projektu nebo – přesněji – které hierarchie aktuálně vlastníkem datový objekt dokumentu, který právě upravujete. Pomocí informací v rámcový, integrovaném vývojovém prostředí můžete zabránit dokumentu otevírání ve více než jeden projekt současně.  
  
 Hierarchie také určuje trvalost dat a používá rámcový aktualizovat **Uložit** a **uložit jako** dialogových oknech. Když uživatelům upravit dokumentu a klikněte na tlačítko **ukončovací** příkaz **souboru** nabídka, rozhraní IDE zobrazí výzvu pomocí **uložit změny** dialogové okno se budou zobrazovat všechny projekty a položky projektu, které jsou aktuálně upravit. To umožňuje uživatelům vybrat, které dokumenty, které se uložit. Seznam dokumentů uložte (to znamená, že tyto dokumenty, které obsahují změny) rámcový nevygeneruje. Všechny položky, které byste měli vidět v **uložit změny** dialogové okno ukončením aplikace musí mít v r... záznamy. Rámcový koordinuje dokumenty, které se uloží a určuje, zda uživatel je vyzván o uložení operace s použitím hodnoty zadané v položce příznaky pro každý dokument. Další informace o rámcový příznaky, najdete v článku <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> výčtu.  
  
## <a name="edit-locks-and-read-locks"></a>Upravit zámky a zámky pro čtení  
 Upravit zámky a zámky pro čtení se nacházejí v rámcový. Dokument okno inkrementuje a dekrementuje úpravy zamknout. Proto když uživatel otevře nové okno dokumentu, upravit počet zámků zvýší o jedna. Když počet uzamčení úpravy dosáhne nuly, hierarchie signalizace zachována nebo uložit data přidružený dokument. Hierarchie můžete pak zachovat data žádným způsobem, včetně uložením jako soubor nebo jako položka v úložišti. Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> rozhraní přidat zámky pro úpravy a čtení zámků a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metoda ohledně odebrání těchto zámků.  
  
 Za normálních okolností při vytváření instance okno dokumentu pro editor rám okna automaticky přidá uzamčení úpravy dokumentu v r.... Nicméně pokud vytvoříte vlastní zobrazení dokumentu, který nepoužívá okna dokumentu standardu (to znamená, neimplementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> rozhraní), pak je nutné nastavit vlastní úpravy zámku. Například v průvodci, je dokument upravovat bez otevření v editoru. V pořadí pro uzamčení dokumentu k otevření průvodce a podobně jako entity, musí implementovat tyto entity <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Chcete-li zaregistrovat váš držitel zámku dokumentu, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metoda a předejte jí váš <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementace. Tím se přidají váš držitel zámku dokumentu na r.... Další možností pro implementaci vlastník zámku dokumentu je-li otevřít dokument prostřednictvím speciální nástrojů. V takovém případě nemůžete mít dokument pro zavření okna nástroje. Když si zaregistrujete jako držitel zámku dokumentu v rámcový, však integrovaného vývojového prostředí může volat vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metoda vyzvat k zavření dokumentu.  
  
## <a name="other-uses-of-the-running-document-table"></a>Jiné účely spuštěná tabulka dokumentů  
 Ostatní entity v integrovaném vývojovém prostředí použít r... k získání informací o dokumenty. Správce řízení zdroje například používá rámcový říct systému k opětovnému načtení dokumentu v editoru po získá nejnovější verzi souboru. K tomuto účelu správce řízení zdroje vyhledá soubory v r... zobrazíte, pokud některý z nich jsou otevřené. Pokud jsou pak správce řízení zdroje nejprve zkontroluje, že hierarchii implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metody. Pokud projekt neimplementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metoda a pak zdrojový ovládací prvek správce kontroly pro implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metodu na datový objekt dokumentu přímo.  
  
 Integrované vývojové prostředí rámcový používá také k resurface (přenést do popředí) otevřený dokument, pokud si uživatel vyžádá tohoto dokumentu. Další informace najdete v tématu [zobrazení souborů pomocí příkazu Otevřít soubor](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Pokud chcete zjistit, zda je soubor otevřen v r..., proveďte následující.  
  
-   Dotaz na dokument moniker (to znamená, že cesta celého dokumentu) a zjistěte, zda je položka otevřít.  
  
-   ID hierarchie nebo položky můžete klást projektový systém pro celý dokument cestu a potom vyhledat položku v r....  
  
## <a name="see-also"></a>Viz také  
 [Využití RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Trvalost a spuštěná tabulka dokumentů](../../extensibility/internals/persistence-and-the-running-document-table.md)

