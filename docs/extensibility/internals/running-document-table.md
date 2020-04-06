---
title: Spuštění tabulky dokumentů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705556"
---
# <a name="running-document-table"></a>Spuštění tabulky dokumentů
IDE udržuje seznam všech aktuálně otevřených dokumentů v interní struktuře nazývané spuštěná tabulka dokumentů (RDT). Tento seznam obsahuje všechny otevřené dokumenty v paměti bez ohledu na to, zda jsou tyto dokumenty právě upravovány. Dokument je libovolná položka, která je trvalá, včetně souborů v projektu nebo v hlavním souboru projektu (například soubor .vcxproj).

## <a name="elements-of-the-running-document-table"></a>Prvky tabulky běžícího dokumentu
 Průběžná tabulka dokladů obsahuje následující položky.

|Element|Popis|
|-------------|-----------------|
|Zástupné název dokumentu|Řetězec, který jednoznačně identifikuje datový objekt dokumentu. Jednalo by se o absolutní cestu k souboru pro systém projektu, který spravuje soubory (například C:\MyProject\MyFile). Tento řetězec se také používá pro projekty uložené v jiných úložištích než v systémech souborů, jako jsou uložené procedury v databázi. V tomto případě systém projektu můžete vymyslet jedinečný řetězec, který může rozpoznat a případně analyzovat určit, jak uložit dokument.|
|Vlastník hierarchie|Objekt hierarchie, který vlastní dokument, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> reprezentované rozhraní.|
|ID položky|Identifikátor položky pro konkrétní položku v rámci hierarchie. Tato hodnota je jedinečná mezi všemi dokumenty v hierarchii, která tento dokument vlastní, ale není zaručeno, že tato hodnota bude jedinečná v různých hierarchiích.|
|Datový objekt dokumentu|Minimálně se jedná o`IUnknown`<br /><br /> Objekt. IDE nevyžaduje žádné konkrétní rozhraní `IUnknown` mimo rozhraní pro datový objekt dokumentu vlastního editoru. Pro standardní editor editoru implementace rozhraní editoru <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> je však nutné pro zpracování volání trvalosti souborů z projektu. Další informace naleznete [v tématu Ukládání standardního dokumentu](../../extensibility/internals/saving-a-standard-document.md).|
|Příznaky|Příznaky, které řídí, zda je dokument uložen, zda je použit zámek pro čtení nebo úpravy a tak dále, lze zadat při přidání položek do RDT. Další informace naleznete <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> ve výčtu.|
|Upravit počet zámků|Počet upravit zámky. Zámek úprav označuje, že některý editor má dokument otevřený pro úpravy. Když počet úprav zamkne přechody na nulu, uživatel je vyzván k uložení dokumentu, pokud byl změněn. Například při každém otevření dokumentu v editoru pomocí příkazu **Nové okno** je pro tento dokument v RDT přidán zámek úprav. Aby bylo možné nastavit zámek úprav, musí mít dokument hierarchii nebo ID položky.|
|Číst počet zámků|Počet čtecích zámků. Zámek pro čtení označuje, že dokument je čten prostřednictvím některého mechanismu, jako je například průvodce. Zámek pro čtení obsahuje dokument aktivní v RDT a zároveň označuje, že dokument nelze upravit. Zámek pro čtení můžete nastavit i v případě, že dokument nemá hierarchii nebo ID položky. Tato funkce umožňuje otevřít dokument v paměti a zadat jej do RDT, aniž by dokument byl vlastněn libovolnou hierarchií. Tato funkce se používá zřídka.|
|Držák zámku|Instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Držák zámku je implementován funkcemi, jako jsou průvodci, kteří otevírají a upravují dokumenty mimo editor. Držák zámku umožňuje funkci přidat zámek úprav do dokumentu, aby se zabránilo zavření dokumentu, zatímco je stále upravován. Za normálních okolností jsou zámky úprav přidávány pouze okny dokumentu (to znamená editory).|

 Každá položka v RDT má jedinečnou hierarchii nebo ID položky s ním spojené, což obvykle odpovídá jednomu uzlu v projektu. Všechny dokumenty, které jsou k dispozici pro úpravy, jsou obvykle vlastněny hierarchií. Položky provedené v RDT řídí, který projekt nebo přesněji – která hierarchie, která aktuálně vlastní upravovaný datový objekt dokumentu. Pomocí informací v RDT ide můžete zabránit otevření dokumentu více než jeden projekt najednou.

 Hierarchie také řídí trvalost dat a používá informace v RDT k aktualizaci dialogových oken **Uložit** a **Uložit jako.** Když uživatelé změní dokument a pak zvolte příkaz **Ukončit** z nabídky **Soubor,** ide vyzve je pomocí dialogového okna **Uložit změny,** aby jim zobrazilvšechny projekty a položky projektu, které jsou aktuálně změněny. To umožňuje uživatelům zvolit, které z dokumentů chcete uložit. Seznam dokumentů, které chcete uložit (to znamená ty dokumenty, které mají změny) je generován z RDT. Všechny položky, které očekáváte, že se zobrazí v dialogovém okně **Uložit změny** při ukončení aplikace, by měly mít záznamy v RDT. RDT souřadnice, které dokumenty jsou uloženy a zda je uživatel vyzván k operaci uložení pomocí hodnot zadaných v flags položky pro každý dokument. Další informace o rdt příznaky <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> naleznete ve výčtu.

## <a name="edit-locks-and-read-locks"></a>Úpravy zámků a zámků čtení
 Upravit zámky a číst zámky jsou umístěny v RDT. Okno dokumentu se zpřísní a sníží zámek úprav. Proto když uživatel otevře nové okno dokumentu, počet upravit zámek se zpřípěje o jeden. Když počet zámků úprav dosáhne nuly, hierarchie je signalizována k zachování nebo uložení dat pro přidružený dokument. Hierarchie pak může zachovat data jakýmkoli způsobem, včetně uchování jako soubor nebo jako položka v úložišti. Můžete použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> v rozhraní přidat upravit zámky a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> číst zámky a metodu k odebrání těchto zámků.

 Za normálních okolností, když je vytvoření instance okna dokumentu pro editor, rámeček okna automaticky přidá zámek úprav pro dokument v RDT. Pokud však vytvoříte vlastní zobrazení dokumentu, který nepoužívá standardní okno dokumentu (to <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> znamená, že rozhraní neimplementuje), je třeba nastavit vlastní zámek úprav. Například v průvodci je dokument upraven bez otevření v editoru. Aby zámky dokumentů byly otevřeny průvodci a podobnými entitami, musí tyto entity implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Chcete-li zaregistrovat držitele <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> zámku dokumentu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> zavolejte metodu a předat v implementaci. Tím přidáte držák zámku dokumentu do RDT. Jiný scénář pro implementaci držitele zámku dokumentu je, pokud otevřete dokument prostřednictvím okna speciální nástroj. V tomto případě nelze nechat okno nástroje zavřít dokument. Však registrací jako držitele zámku dokumentu v RDT, ide <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> můžete volat implementaci metody vyzvat uzavření dokumentu.

## <a name="other-uses-of-the-running-document-table"></a>Další použití tabulky běžícího dokumentu
 Jiné entity v ide použít RDT získat informace o dokumentech. Například správce správy zdrojového kódu používá RDT sdělit systému znovu načíst dokument v editoru, poté, co získá nejnovější verzi souboru. Chcete-li to provést, správce správy zdrojového kódu vyhledá soubory v RDT a zjistí, zda jsou některé z nich otevřené. Pokud ano, pak správce správy zdrojového kódu nejprve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> zkontroluje, zda hierarchie implementuje metodu. Pokud projekt neimplementuje metodu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> potom správce správy zdrojového kódu zkontroluje implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metody na datovém objektu dokumentu přímo.

 IDE také používá RDT znovu vynořovat (přenést na přední) otevřený dokument, pokud uživatel požaduje tento dokument. Další informace naleznete [v tématu Zobrazení souborů pomocí příkazu Otevřít soubor](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Chcete-li zjistit, zda je soubor otevřen v RDT, proveďte jeden následující postup.

- Dotaz na zástupné skupiny dokumentu (to znamená úplnou cestu dokumentu) a zjistěte, zda je položka otevřená.

- Pomocí hierarchie nebo ID položky požádejte systém projektu o úplnou cestu dokumentu a pak položku vyhledejte v rdt.

## <a name="see-also"></a>Viz také
- [Využití RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Trvalost a spuštěná tabulka dokumentů](../../extensibility/internals/persistence-and-the-running-document-table.md)
