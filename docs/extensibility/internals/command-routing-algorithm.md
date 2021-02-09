---
title: Algoritmus směrování příkazů | Microsoft Docs
description: Přečtěte si o pořadí řešení příkazů v aplikaci Visual Studio, protože příkazy jsou zpracovávány různými komponentami a směrovány z nejvnitřnějšího kontextu do nejvzdálenějšího kontextu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47991a3d1140893c4695e4edb7b76b808ab2917a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907726"
---
# <a name="command-routing-algorithm"></a>Algoritmus směrování příkazů
Příkazy v aplikaci Visual Studio jsou zpracovávány řadou různých komponent. Příkazy jsou směrovány z nejvnitřnějšího kontextu, který je založen na aktuálním výběru, na nejvzdálenější kontext (označovaný také jako globální). Další informace najdete v tématu [dostupnost příkazu](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Pořadí řešení příkazů
 Příkazy jsou předávány prostřednictvím následujících úrovní kontextu příkazu:

1. Doplňky: prostředí nejprve nabídne příkaz všem doplňkům, které jsou k dispozici.

2. Příkazy priority: tyto příkazy jsou zaregistrované pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Jsou volány pro každý příkaz v aplikaci Visual Studio a jsou volány v pořadí, ve kterém byly registrovány.

3. Příkazy kontextové nabídky: příkaz umístěný v místní nabídce se nejprve nabídne cílovému příkazu, který je k dispozici v místní nabídce, a poté pro obvyklé směrování.

4. Cíle příkazů sady nástrojů na příkazy: tyto cíle příkazů jsou registrovány při volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . `pCmdTarget`Parametr může být `null` . Pokud tomu tak není `null` , bude tento cíl příkazu použit k aktualizaci příkazů umístěných na panelu nástrojů, který nastavujete. Pokud prostředí nastavilo panel nástrojů, pak předá rámec okna jako, aby byly `pCmdTarget` všechny aktualizace příkazů na panelu nástrojů v toku okna, i když není zaostření.

5. Panel nástrojů: okna nástrojů, která obvykle implementují <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> rozhraní, by měla také implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, aby Visual Studio mohl získat cíl příkazu, když je okno nástroje aktivní okno. Pokud je však okno nástroje, které má fokus, okno **projektu** , pak je příkaz směrován do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> rozhraní, které je společné nadřazené položky vybraných položek. Pokud tento výběr zahrnuje více projektů, je příkaz směrován do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hierarchie. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Rozhraní obsahuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metody a, které jsou analogické k odpovídajícím příkazům v <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní.

6. Okno dokumentu: Pokud příkaz má `RouteToDocs` příznak nastavený v souboru *. vsct* , sada Visual Studio hledá cíl příkazu v objektu zobrazení dokumentu, což je buď instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> rozhraní, nebo instance objektu dokumentu (obvykle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> rozhraní nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> rozhraní). Pokud objekt zobrazení dokumentu nepodporuje příkaz, aplikace Visual Studio směruje příkaz na <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, které je vráceno. (Toto je volitelné rozhraní pro datové objekty dokumentu.)

7. Aktuální hierarchie: Aktuální hierarchie může být projekt, který je vlastníkem okna aktivního dokumentu, nebo hierarchie, která je vybrána v **Průzkumník řešení**. Visual Studio hledá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, které je implementováno v aktuální nebo aktivní hierarchii. Hierarchie by měla podporovat příkazy, které jsou platné vždy, když je hierarchie aktivní, a to i v případě, že okno dokumentu položky projektu má fokus. Nicméně příkazy, které platí pouze v případě, že **Průzkumník řešení** má fokus, musí být podporovány pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> rozhraní a jeho <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metod a.

     Příkazy **Vyjmout**, **Kopírovat**, **Vložit**, **Odstranit**, **Přejmenovat**, **ENTER** a **DoubleClick** vyžadují speciální zpracování. Informace o tom, jak zpracovávat příkazy **Delete** a **Remove** v hierarchiích, najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> rozhraní.

8. Global: Pokud příkaz nebyl zpracován dříve uvedenými kontexty, Visual Studio se pokusí ho směrovat do VSPackage, který vlastní příkaz, který implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní. Pokud rozhraní VSPackage již nebylo načteno, není načteno, když aplikace Visual Studio zavolá <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodu. VSPackage je načten pouze v případě, že <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> je volána metoda.

## <a name="see-also"></a>Viz také
- [Návrh příkazu](../../extensibility/internals/command-design.md)
