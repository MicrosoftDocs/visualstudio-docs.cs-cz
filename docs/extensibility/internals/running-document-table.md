---
title: Spuštění tabulky dokumentů | Microsoft Docs
description: Zjistěte, jak Visual Studio IDE udržuje spuštěnou tabulku dokumentů, která zahrnuje všechny otevřené dokumenty v paměti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d260534d58853afc6b84ba484eb3a806250e2aa6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900405"
---
# <a name="running-document-table"></a>Spuštění tabulky dokumentů
Integrované vývojové prostředí udržuje seznam všech aktuálně otevřených dokumentů v interní struktuře, která se nazývá spuštěná tabulka dokumentů (RDT). Tento seznam obsahuje všechny otevřené dokumenty v paměti bez ohledu na to, jestli se tyto dokumenty právě upravuje. Dokument je libovolná uložená položka, včetně souborů v projektu nebo hlavního souboru projektu (například souboru .vcxproj).

## <a name="elements-of-the-running-document-table"></a>Prvky tabulky spuštěného dokumentu
 Spuštěná tabulka dokumentů obsahuje následující položky.

|Element|Popis|
|-------------|-----------------|
|Moniker dokumentu|Řetězec, který jednoznačně identifikuje datový objekt dokumentu. To by byla absolutní cesta k souboru pro systém projektu, který spravuje soubory (například C:\MyProject\MyFile). Tento řetězec se používá také pro projekty uložené v jiných obchodech než v systémech souborů, jako jsou například uložené procedury v databázi. V tomto případě může systém projektu vymyslet jedinečný řetězec, který dokáže rozpoznat a případně analyzovat, aby určil, jak dokument uložit.|
|Vlastník hierarchie|Objekt hierarchie, který je vlastnit dokument, jak je reprezentován <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraním.|
|ID položky|Identifikátor položky pro konkrétní položku v hierarchii. Tato hodnota je jedinečná mezi všemi dokumenty v hierarchii, které tento dokument vlastní, ale není zaručeno, že tato hodnota bude jedinečná v různých hierarchiích.|
|Datový objekt dokumentu|Minimálně se jedná o `IUnknown`<br /><br /> Objekt. Integrované vývojové prostředí nevyžaduje kromě rozhraní žádné konkrétní rozhraní pro objekt dat `IUnknown` dokumentu vlastního editoru. Pro standardní editor je však implementace rozhraní editoru nutná ke zpracování volání trvalosti <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> souborů z projektu. Další informace najdete v tématu [Uložení standardního dokumentu.](../../extensibility/internals/saving-a-standard-document.md)|
|Příznaky|Příznaky, které řídí, jestli se dokument uloží, jestli se použije zámek pro čtení nebo úpravy atd., je možné zadat při přidání položek do RDT. Další informace najdete ve <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> výčtu.|
|Upravit počet zámků|Počet zámků úprav Zámek pro úpravy označuje, že v některém editoru je dokument otevřený pro úpravy. Při přechodu počtu zámků úprav na nulu se uživateli zobrazí výzva k uložení dokumentu, pokud byl změněn. Například při každém otevření dokumentu v editoru pomocí příkazu New **Window** (Nové okno) se pro tento dokument přidá zámek pro úpravy v rdt. Aby bylo možné zámek pro úpravy nastavit, musí mít dokument hierarchii nebo ID položky.|
|Počet zámků čtení|Počet zámků čtení Zámek pro čtení označuje, že se dokument čte některými mechanismy, jako je průvodce. Zámek pro čtení obsahuje dokument, který je v RDT živý, a současně indikuje, že dokument není možné upravit. Zámek pro čtení můžete nastavit i v případě, že dokument nemá hierarchii nebo ID položky. Tato funkce umožňuje otevřít dokument v paměti a zadat ho do RDT, aniž by dokument vlastnila jakákoli hierarchie. Tato funkce se používá zřídka.|
|Držitel zámku|Instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Držitel zámku je implementován pomocí funkcí, jako jsou průvodci, které otevírají a upravuje dokumenty mimo editor. Držitel zámku umožňuje funkci přidat do dokumentu zámek pro úpravy, aby se zabránilo zavření dokumentu během jeho úprav. Zámky pro úpravy obvykle přidávají jenom okna dokumentů (to znamená editory).|

 Každá položka v uzlu RDT má přidruženou jedinečnou hierarchii nebo ID položky, která obecně odpovídá jednomu uzlu v projektu. Všechny dokumenty, které jsou k dispozici pro úpravy, obvykle vlastní hierarchie. Položky provedené v ovládacího prvku RDT řídí, který projekt nebo která hierarchie aktuálně vlastní upravovaný objekt dat dokumentu. Pomocí informací v kanálu RDT může integrované vývojové prostředí (IDE) bránit otevření dokumentu více než jedním projektem najednou.

 Hierarchie také řídí trvalost dat a používá informace v rdt k aktualizaci dialogových oken **Uložit** a Uložit jako.  Když uživatelé upraví dokument a  pak v  nabídce Soubor zvolí příkaz Ukončit, zobrazí se jim v integrovaném vývojovém prostředí (IDE) dialogové okno Save **Changes** (Uložit změny), ve které se zobrazí všechny projekty a položky projektu, které jsou aktuálně změněné. To umožňuje uživatelům zvolit, který z dokumentů se má uložit. Ze sady RDT se vygeneruje seznam dokumentů, které se mají uložit (to znamená dokumenty, které mají změny). Všechny položky, které očekáváte  v dialogovém okně Uložit změny po ukončení aplikace, by měly mít záznamy v sadě RDT. RDT koordinuje, které dokumenty jsou uložené a jestli se uživateli zobrazí výzva k operaci uložení, pomocí hodnot zadaných v položce Příznaky pro každý dokument. Další informace o příznakech RDT najdete ve <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> výčtu.

## <a name="edit-locks-and-read-locks"></a>Úprava zámků a zámků pro čtení
 Zámky pro úpravy a zámky čtení se nacházejí v rdt. Okno dokumentu zvýší a sníží zámek pro úpravy. Proto když uživatel otevře nové okno dokumentu, počet zámků pro úpravy se zvýší o 1. Pokud počet zámků pro úpravy dosáhne nuly, je v hierarchii signalizováno zachování nebo uložení dat pro přidružený dokument. Hierarchie pak může data zachovat libovolným způsobem, včetně trvalého uchování jako souboru nebo jako položky v úložišti. Pomocí metody v rozhraní můžete přidat zámky úprav a zámky čtení a metodu k <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> odebrání těchto <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> zámků.

 Při vytvoření instance okna dokumentu pro editor obvykle rámec okna automaticky přidá zámek pro úpravy dokumentu v rdt. Pokud ale vytvoříte vlastní zobrazení dokumentu, které nevyu iotuje standardní okno dokumentu (to znamená, že rozhraní neimplementuje), budete si muset nastavit vlastní <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> zámek pro úpravy. Například v průvodci se dokument upravuje bez otevření v editoru. Aby bylo možné zámky dokumentů otevřít pomocí průvodců a podobných entit, musí tyto entity implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Pokud chcete zaregistrovat vlastníka zámku dokumentu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> zavolejte metodu a předejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementaci. Tím se do RDT přidá váš držitel zámku dokumentu. Dalším scénářem implementace držitele zámku dokumentu je otevření dokumentu prostřednictvím speciálního okna nástroje. V tomto případě nemůžete mít okno nástroje k zavření dokumentu. Registrací jako držitele zámku dokumentu v kanálu RDT však může integrované vývojové prostředí (IDE) volat vaši implementaci metody a zobrazit tak výzvu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> k zavření dokumentu.

## <a name="other-uses-of-the-running-document-table"></a>Další použití spuštěné tabulky dokumentů
 Ostatní entity v integrovaném vývojovém prostředí používají RDT k získání informací o dokumentech. Správce správy zdrojového kódu například pomocí sady RDT sděluje systému, že má po získání nejnovější verze souboru znovu načíst dokument v editoru. Správce správy zdrojového kódu proto vyhledá soubory v rdt a podívá se, jestli je některý z nich otevřený. Pokud tomu tak je, správce správy zdrojového kódu nejprve zkontroluje, zda hierarchie implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodu . Pokud projekt metodu neimplementuje, správce správy zdrojového kódu kontroluje implementaci metody přímo na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> datovém objektu dokumentu.

 Pokud si uživatel vyžádá tento dokument, použije integrované vývojové prostředí (IDE) také k opětovnému připojení k otevřenému dokumentu (přenést na frontu). Další informace najdete v tématu [Zobrazení souborů pomocí příkazu Otevřít soubor.](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md) Pokud chcete zjistit, jestli je soubor v rdt otevřený, proveďte jednu z následujících akcí.

- Zadejte dotaz na moniker dokumentu (to znamená úplnou cestu k dokumentu), abyste zjistili, jestli je položka otevřená.

- Pomocí ID hierarchie nebo položky požádejte systém projektu o úplnou cestu k dokumentu a pak vyhledejte položku v rdt.

## <a name="see-also"></a>Viz také
- [Využití RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Trvalost a spuštěná tabulka dokumentů](../../extensibility/internals/persistence-and-the-running-document-table.md)
