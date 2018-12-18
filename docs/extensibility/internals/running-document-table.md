---
title: Spuštění dokumentu tabulky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a49a5267fcccbde60e194e3fc58b0f6b6ea7552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134090"
---
# <a name="running-document-table"></a>Spuštěné tabulce dokumentu
Prostředí IDE udržuje seznam všechny aktuálně otevřené dokumenty v interní strukturu názvem spuštěné tabulce dokumentu (r...). Tento seznam obsahuje všechny otevřené dokumenty v paměti, bez ohledu na to, jestli tyto dokumenty jsou aktuálně Upravovaný. Dokument je libovolnou položku, která je trvalý, včetně souborů v projektu nebo hlavní soubor projektu (například soubor VCXPROJ).  
  
## <a name="elements-of-the-running-document-table"></a>Elementy tabulky spuštěná dokumentů  
 Spuštěné tabulce dokument obsahuje následující položky.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Přezdívka dokumentu|Řetězec, který jednoznačně identifikuje datový objekt dokumentu. To může být absolutní cestu k souboru projektu systému, který spravuje soubory (například C:\MyProject\MyFile). Tento řetězec se používá také pro projekty, které jsou uloženy v úložištích než systémy souborů, jako je například uložené procedury v databázi. V takovém případě může systém projektu skladová jedinečného řetězce, který může rozpoznat a pravděpodobně analyzovat určit, jak k uložení dokumentů.|  
|Vlastník hierarchie|Objekt hierarchie, který vlastní dokumentu, reprezentovaná <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní.|  
|ID položky|Identifikátor položky pro konkrétní položku v hierarchii. Tato hodnota je jedinečný mezi všechny dokumenty v hierarchii, které vlastní tento dokument, ale tato hodnota nemusí být jedinečný v rámci různých hierarchiích.|  
|Datový objekt dokumentu|Minimálně, jedná se `IUnknown`<br /><br /> objekt. Prostředí IDE nevyžaduje žádné konkrétní rozhraní nad rámec `IUnknown` rozhraní pro vlastní editor dokumentu datový objekt. Pro standardní editor, ale editoru provádění <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> rozhraní vyžadovaná ke zpracování souborů trvalost volání z projektu. Další informace najdete v tématu [ukládání standardní dokumentu](../../extensibility/internals/saving-a-standard-document.md).|  
|Příznaky|Příznaky, které řídí, zda je uložen v dokumentu, zda je použita zámek pro čtení nebo úpravy a tak dále, lze zadat po přidání položek r.... Další informace najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> výčtu.|  
|Upravit počet zámků|Počet upravit zamkne. Zámek upravit znamená, že některé editor má dokument otevřít pro úpravy. Pokud počet zámků upravit přejde na hodnotu nula, bude uživatel vyzván k uložení dokumentu, pokud se změnila. Například při každém otevření dokumentu v editoru pomocí **nové okno** příkaz, přidá se pro tento dokument v r... zámek upravit. Aby zámek upravit nastavení musí mít hierarchii nebo položky ID dokumentu|  
|Počet zámek pro čtení|Počet čtení zámky. Zámek pro čtení označuje, že dokument je načítán přes některé mechanismus například Průvodce. Zámek pro čtení obsahuje dokument v r... živá při indikující, že dokument nelze upravit. Zámek pro čtení můžete nastavit i v případě, že dokument nemá hierarchii nebo položky ID. Tato funkce umožňuje otevření dokumentu v paměti a zadejte ho r... bez dokumentu se vlastníkem žádné hierarchie. Tato funkce slouží jen zřídka.|  
|Vlastníka zámku|Instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Držitel uzamknutí je implementováno modulem funkce, jako je průvodců, které otevírat a upravovat dokumenty mimo editoru. Vlastníka zámku umožňuje funkci tak, aby do dokumentu zabránit dochází k uzavření při je stále upravována dokumentu přidejte zámek upravit. Za normálních okolností upravit zámky jsou přidány pouze v dokumentu systému windows (editory).|  
  
 Každá položka v r... má jedinečný hierarchie nebo ID položky související s, která obvykle odpovídá jeden uzel v projektu. Všechny dokumenty, které jsou k dispozici pro úpravy jsou obvykle vlastníkem hierarchie. Položky vytvořené v r... řídit, které projektu nebo – přesněji – které hierarchie aktuálně vlastníkem upravovaný objekt dat dokumentu. Pomocí informací v r..., rozhraní IDE zabránit v dokumentu otevíráte ve více projektů současně.  
  
 Hierarchii také řídí trvalost dat a používá r... aktualizovat **Uložit** a **uložit jako** dialogová okna. Když uživatelé upravit dokument a potom vyberte **ukončení** příkaz **soubor** nabídce prostředí IDE zobrazí výzvu s **uložit změny** dialogové okno je chcete zobrazit všechny projekty a položky projektu, které jsou aktuálně upraveny. To umožňuje uživatelům zvolit, která pro uložení dokumentů. Seznam dokumentů pro uložení (to znamená, tyto dokumenty, které mají změny) se generují z r.... Všechny položky, které byste měli vidět v **uložit změny** dialogové okno při ukončení aplikace by měla mít v r.... R... koordinuje dokumenty, které jsou uloženy a jestli je uživatel vyzván, o uložení operace pomocí hodnoty zadané v položce příznaky pro každý dokument. Další informace o příznaky r... najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> výčtu.  
  
## <a name="edit-locks-and-read-locks"></a>Upravit zámků a zámky pro čtení  
 Upravit zámků a čtení zámky nacházet v r.... Okna dokumentu se zvýší a sníží úpravy uzamčení. Proto když uživatel otevře nové okno dokumentu, zámek upravit počet se zvýší o jednu. Pokud počet upravit uzamčení hodnota nula, hierarchii signalizace zachována nebo ukládání dat pro přidružené dokumentu. V hierarchii můžete pak zachovat data žádným způsobem, včetně uložením jako soubor nebo položky v úložišti. Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metoda v <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> rozhraní umožňuje přidat zámky úpravy a číst zámků a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metoda odebrat tyto zámky.  
  
 Za normálních okolností při vytváření instance okna dokumentu pro editor rámce okna automaticky přidá zámek upravit pro dokument v r.... Však-li vytvořit vlastní zobrazení dokumentu, který nepoužívá okna standardní dokumentu (to znamená, neimplementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> rozhraní), pak je nutné nastavit vlastní úpravy zámku. V průvodci, je například dokument upravit bez otevíráte v editoru. Aby zámky dokument k otevření průvodce a podobné entity, musí implementovat tyto entity <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Chcete-li zaregistrovat váš držitel zámek dokumentu, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metoda a předejte jí vaší <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementace. Díky tomu přidá váš držitel zámek dokumentu r.... Další možností pro implementaci vlastníka zámku dokumentu je, pokud otevření dokumentu prostřednictvím okno speciální nástroje. V této instanci nebudete moci mít okno nástroje zavřete dokument. Tím, že zaregistrujete jako vlastníka zámku dokumentu v r..., ale integrovaného vývojového prostředí můžete volat vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metoda k ukončení dokumentu.  
  
## <a name="other-uses-of-the-running-document-table"></a>Jiné účely tabulky spuštěná dokumentů  
 Ostatní entity v prostředí IDE pomocí r... můžete získat informace o dokumenty. Například správce řízení zdrojů používá r... říct systému načtením dokumentu v editoru po získá nejnovější verzi souboru. K tomuto účelu správce řízení zdrojů vyhledá soubory v r... Chcete zobrazit, pokud některý z nich jsou otevřené. Pokud jsou pak správce řízení zdrojů nejdřív zkontroluje, že hierarchii implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metoda. Pokud projekt neimplementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metoda pak zdroj řízení manager kontroluje implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metoda na datový objekt dokument přímo.  
  
 Prostředí IDE r... používá také k resurface (přenést do popředí) otevřete dokument, pokud uživatel požádá o tomto dokumentu. Další informace najdete v tématu [zobrazení souborů pomocí příkazu otevřete soubor](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Určení, zda je soubor otevřít v r..., se postupujte takto.  
  
-   Dotaz na dokument Přezdívka (to znamená, cesta celého dokumentu) a zjistěte, zda položka je otevřený.  
  
-   Pomocí ID hierarchie nebo položky požádejte systému projektu pro cestu celého dokumentu a pak vyhledat položku v r....  
  
## <a name="see-also"></a>Viz také  
 [RDT_ReadLock využití](../../extensibility/internals/rdt-readlock-usage.md)   
 [Trvalost a spuštěná tabulka dokumentů](../../extensibility/internals/persistence-and-the-running-document-table.md)