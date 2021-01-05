---
title: Běžící tabulka dokumentů | Microsoft Docs
description: Přečtěte si, jak IDE sady Visual Studio udržuje spuštěnou tabulku dokumentů, která zahrnuje všechny otevřené dokumenty v paměti.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bd166626d6043da4ac94658bdd35219efc7a37c2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875645"
---
# <a name="running-document-table"></a>Spuštění tabulky dokumentů
Rozhraní IDE udržuje seznam všech aktuálně otevřených dokumentů ve vnitřní struktuře nazvané spuštěná tabulka dokumentů (RDT). Tento seznam obsahuje všechny otevřené dokumenty v paměti bez ohledu na to, zda jsou tyto dokumenty právě upravovány. Dokument je libovolná položka, která je trvalá, včetně souborů v projektu nebo v souboru hlavního projektu (například soubor. vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementy běžící tabulky dokumentů
 Tabulka spouštěného dokumentu obsahuje následující položky.

|Element|Popis|
|-------------|-----------------|
|Moniker dokumentu|Řetězec, který jednoznačně identifikuje datový objekt dokumentu. Toto je absolutní cesta k souboru pro systém projektu, který spravuje soubory (například C:\MyProject\MyFile). Tento řetězec se používá také pro projekty uložené v jiných úložištích než souborové systémy, jako jsou například uložené procedury v databázi. V tomto případě systém projektu může zásobovat jedinečný řetězec, který může rozpoznat a případně analyzovat, a určit tak, jak dokument uložit.|
|Vlastník hierarchie|Objekt hierarchie, který je vlastníkem dokumentu, jak je znázorněno v <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> rozhraní.|
|ID položky|Identifikátor položky pro konkrétní položku v rámci hierarchie. Tato hodnota je jedinečná mezi všemi dokumenty v hierarchii, které vlastní tento dokument, ale nezaručujeme, že tato hodnota nebude v různých hierarchiích jedinečná.|
|Datový objekt dokumentu|Minimální je to `IUnknown`<br /><br /> předmětů. Rozhraní IDE nevyžaduje žádné konkrétní rozhraní nad rámec `IUnknown` rozhraní pro objekt dat dokumentu vlastního editoru. Nicméně pro standardní editor je implementována implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> rozhraní editoru pro zpracování volání trvalosti souborů z projektu. Další informace najdete v tématu [uložení standardního dokumentu](../../extensibility/internals/saving-a-standard-document.md).|
|Příznaky|Příznaky, které řídí, zda je dokument uložen, zda je použit zámek pro čtení nebo úpravy a tak dále, lze zadat při přidání položek do RDT. Další informace najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> výčet.|
|Upravit počet zámků|Počet zámků pro úpravy Zámek pro úpravy označuje, že má některý Editor otevřený dokument pro úpravy. Když se počet zámků pro úpravy změní na nula, uživateli se zobrazí výzva k uložení dokumentu, pokud byl upraven. Například pokaždé, když otevřete dokument v editoru pomocí příkazu **Nový okno** , přidá se pro tento dokument do RDT zámek pro úpravy. Aby bylo možné nastavit zámek pro úpravy, musí mít dokument hierarchii nebo ID položky.|
|Čtení – počet zámků|Počet zámků pro čtení Zámek pro čtení indikuje, že se dokument čte prostřednictvím určitého mechanismu, jako je například Průvodce. Zámek pro čtení uchovává v RDT dokument aktivní a zároveň indikuje, že dokument nelze upravovat. Zámek pro čtení můžete nastavit i v případě, že dokument neobsahuje ID hierarchie nebo položky. Tato funkce umožňuje otevřít dokument v paměti a zadat ho do RDT, aniž by byl dokument vlastněn žádnou hierarchií. Tato funkce se používá zřídka.|
|Držitel zámku|Instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Držitel zámku je implementován funkcemi, jako jsou průvodci, kteří otevírají a upravují dokumenty mimo editor. Držitel zámku umožňuje funkci přidat zámek úprav do dokumentu, aby se zabránilo jeho zavření v době, kdy je stále upravován. V normálním případě se zámky úprav přidávají pouze v oknech dokumentů (tj. editory).|

 Každá položka v RDT má přidruženou jedinečnou hierarchii nebo ID položky, což obvykle odpovídá jednomu uzlu v projektu. Všechny dokumenty, které jsou k dispozici pro úpravy, jsou obvykle vlastněny hierarchií. Položky provedené v ovládacím prvku RDT, který projekt nebo – přesněji – která hierarchie, aktuálně vlastní upravovaný objekt dat dokumentu. Pomocí informací v RDT může rozhraní IDE zabránit otevření dokumentu více než jedním projektem najednou.

 Hierarchie také řídí persistenci dat a používá informace v RDT k aktualizaci dialogových oken **Uložit** a **Uložit jako** . Když uživatel upraví dokument a pak v nabídce **soubor** vybere příkaz **Exit** , rozhraní IDE je vyzve k zobrazení všech projektů  a položek projektu, které jsou aktuálně upravovány. To umožňuje uživatelům zvolit, které dokumenty se mají uložit. Seznam dokumentů, které se mají uložit (tj. tyto dokumenty, které mají změny), se generuje z RDT. Všechny položky, které očekáváte, se zobrazí v dialogovém okně **Uložit změny** po ukončení aplikace by měly mít záznamy v RDT. RDT koordinuje, které dokumenty jsou uloženy a zda je uživatel vyzván k uložení operace s použitím hodnot zadaných v položce Flags pro každý dokument. Další informace o příznacích RDT naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> výčet.

## <a name="edit-locks-and-read-locks"></a>Upravit zámky a číst zámky
 Upravit zámky a zámky pro čtení jsou uloženy v RDT. Okno dokumentu zvýší a sníží zámek úprav. Proto když uživatel otevře nové okno dokumentu, počet zámků úpravy se zvýší o jeden. Když počet zámků úpravy dosáhne nuly, hierarchie se zablokuje, aby zachovala nebo uložila data přidruženého dokumentu. Hierarchie pak může uchovávat data jakýmkoli způsobem, včetně uchování jako souboru nebo jako položky v úložišti. Pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metody v <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> rozhraní můžete přidat zámky úprav a zámky pro čtení a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodu pro odebrání těchto zámků.

 Normálně, když je vytvořena instance okna dokumentu pro Editor, rámec okna automaticky přidá zámek úprav pro dokument v RDT. Pokud však vytvoříte vlastní zobrazení dokumentu, který nepoužívá standardní okno dokumentu (tj. neimplementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> rozhraní), je nutné nastavit vlastní zámek úprav. Například v průvodci je dokument upravován bez otevření v editoru. Aby bylo možné otevírat zámky dokumentů pomocí průvodců a podobných entit, musí tyto entity implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> rozhraní. Chcete-li zaregistrovat svého držitele zámku dokumentu, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodu a předejte svou <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementaci. Tím se do RDT přidá držitel zámku dokumentu. Dalším scénářem implementace držitele zámku dokumentu je otevření dokumentu prostřednictvím speciálního okna nástroje. V této instanci nemůžete nechat okno nástroje zavřít dokument. Nicméně registrací jako držitel zámku dokumentu v RDT může rozhraní IDE zavolat vaší implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metody, aby se zobrazila výzva k uzavření dokumentu.

## <a name="other-uses-of-the-running-document-table"></a>Další použití tabulky spuštěných dokumentů
 Další entity v integrovaném vývojovém prostředí používají RDT k získání informací o dokumentech. Správce řízení zdrojů například používá RDT k tomu, aby systém mohl znovu načíst dokument v editoru, jakmile získá nejnovější verzi souboru. Za tímto účelem správce řízení zdrojů vyhledá soubory v RDT a zjistí, jestli je některý z nich otevřený. Pokud jsou, pak správce řízení zdrojů nejprve zkontroluje, zda hierarchie implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodu. Pokud projekt neimplementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodu, pak správce řízení zdrojů kontroluje implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metody přímo v objektu dat dokumentu.

 Rozhraní IDE také používá RDT k překrytí otevřeného dokumentu (přenést do popředí), pokud si ho uživatel požádá. Další informace naleznete v tématu [zobrazení souborů pomocí příkazu otevřít soubor](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Chcete-li zjistit, zda je soubor otevřen v RDT, proveďte jednu z následujících akcí.

- Dotaz na moniker dokumentu (tj. na úplnou cestu k dokumentu), abyste zjistili, jestli je položka otevřená

- Pomocí ID hierarchie nebo položky požádejte systém projektu o úplnou cestu k dokumentu a pak položku vyhledejte v RDT.

## <a name="see-also"></a>Viz také
- [Využití RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Trvalost a spuštěná tabulka dokumentů](../../extensibility/internals/persistence-and-the-running-document-table.md)
