---
title: 'Návod: Přidání funkcí do vlastního editoru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b145dd4d82887122009553afd883abb6cade849e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697794"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Návod: Přidání funkcí do vlastního editoru
Po vytvoření vlastního editoru do něj můžete přidat další funkce.

## <a name="to-create-an-editor-for-a-vspackage"></a>Vytvoření editoru pro balíček VSPackage

1. Vytvořte vlastní editor pomocí šablony projektu Balíček Visual Studio.

     Další informace naleznete [v tématu Návod: Vytvoření vlastního editoru](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Rozhodněte se, zda má editor podporovat jedno zobrazení nebo více zobrazení.

     Editor, který podporuje příkaz **Nové okno** nebo má zobrazení formuláře a zobrazení kódu, vyžaduje samostatné objekty dat dokumentu a objekty zobrazení dokumentu. V editoru, který podporuje pouze jedno zobrazení, lze datový objekt dokumentu a objekt zobrazení dokumentu implementovat na stejném objektu.

     Příklad více zobrazení najdete v tématu [Podpora více zobrazení dokumentu](../extensibility/supporting-multiple-document-views.md).

3. Implementujte továrnu editoru <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> nastavením rozhraní.

     Další informace naleznete v [tématu Editor factories](../extensibility/editor-factories.md).

4. Rozhodněte se, zda chcete, aby editor ke správě okna objektu zobrazení dokumentu používal aktivaci na místě nebo zjednodušené vkládání.

     Zjednodušené okno editoru vkládání je hostitelem standardního zobrazení dokumentu, zatímco okno editoru aktivace na místě je hostitelem ovládacího prvku ActiveX nebo jiného aktivního objektu jako jeho zobrazení dokumentu. Další informace naleznete v [tématu Zjednodušené vkládání](../extensibility/simplified-embedding.md) a [aktivace na místě](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní pro zpracování příkazů.

6. Zadejte trvalost dokumentu a odpověď na změny externích souborů:

    1. Chcete-li soubor <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> zachovat, implementujte a <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> na datovém objektu dokumentu editoru.

    2. Chcete-li reagovat na <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> změny externích souborů, implementujte a na datovém objektu dokumentu editoru.

        > [!NOTE]
        > Volání `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> na získání ukazatele `IVsFileChangeEx`na .

7. Směřujte události úprav dokumentu pomocí správy zdrojového kódu. Postupujte následovně:

    1. Na nástroj `IVsQueryEditQuerySave2` najeďte <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>myší na . `QueryService`

    2. Když dojde k první události <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> úprav, zavolejte metodu.

         Tato metoda vyzve uživatele k rezervování souboru, pokud ještě není rezervován. Ujistěte se, že zpracování "soubor není rezervován" podmínku odvrátit chyby.

    3. Podobně před uložením souboru <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> volání metody.

         Tato metoda vyzve uživatele k uložení souboru, pokud nebyl uložen nebo pokud se změnil od posledního uložení.

8. Povolte okno **Vlastnosti,** aby se zobrazily vlastnosti textu vybraného v editoru. Postupujte následovně:

    1. Volání <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> pokaždé, když se změní výběr <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>textu, předávání v implementaci .

    2. Volání `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> služby získat ukazatel <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>na .

9. Umožněte uživatelům přetahovat položky mezi editorem a **panelem nástrojů**nebo mezi externími editory (například microsoft word) a **panelem nástrojů**. Postupujte následovně:

    1. Implementujte `IDropTarget` na editoru upozornit rozhraní IDE, že váš editor je cíl přetažení.

    2. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> rozhraní v zobrazení, aby editor mohl povolit a zakázat položky v **panelu nástrojů**.

    3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> Implementovat `QueryService` a <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> volat na službu <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> získat ukazatel na rozhraní a.

         Tyto kroky umožňují vspackage přidat nové položky **do panelu nástrojů**.

10. Rozhodněte se, zda chcete pro editor u sebe získat další volitelné funkce.

    - Pokud chcete, aby editor podporoval příkazy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>pro hledání a nahrazování, implementujte aplikaci .

    - Pokud chcete v editoru použít okno nástroje `IVsDocOutlineProvider`osnovy dokumentu, implementujte aplikaci .

    - Pokud chcete použít stavový řádek v <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> editoru, <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> implementujte a `IVsStatusBar`zavolejte `QueryService` pro získání ukazatele na .

         Například editor může zobrazit informace o řádcích / sloupcích, režim výběru (stream / box) a režim vkládání (vložení / přeškrtnutí).

    - Pokud chcete, aby editor `Undo` podporoval příkaz, doporučujeme použít model správce undo OLE. Jako alternativu můžete mít editor `Undo` zpracování příkazu přímo.

11. Vytvořte informace registru, včetně identifikátorů GUID pro vspackage, nabídky, editor a další funkce.

     Následuje obecný příklad kódu, který byste vložili do skriptu souboru *RGS,* abyste ukázali, jak správně zaregistrovat editor.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. Implementujte kontextovou podporu nápovědy.

     Tento krok umožňuje poskytnout podporu nápovědy f1 a dynamické nápovědy pro položky v editoru. Další informace naleznete v [tématu How to: Provide context for editors](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Vystavit objektový model automatizace z `IDispatch` editoru implementací rozhraní.

     Další informace naleznete [v tématu Přispívání k modelu automatizace](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Robustní programování

- Instance editoru je vytvořena, když <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> ide volá metodu. Pokud editor podporuje více `CreateEditorInstance` zobrazení, vytvoří data dokumentu i objekty zobrazení dokumentu. Pokud je datový objekt dokumentu již otevřen, je předána hodnota bez hodnoty null `punkDocDataExisting` `IVsEditorFactory::CreateEditorInstance`. Implementace editoru factory musí určit, zda je existující datový objekt dokumentu kompatibilní dotazováním na příslušná rozhraní. Další informace naleznete [v tématu Podpora více zobrazení dokumentu](../extensibility/supporting-multiple-document-views.md).

- Pokud použijete zjednodušený přístup vkládání, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> rozhraní.

- Pokud se rozhodnete použít aktivaci na místě, implementujte následující rozhraní:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Rozhraní `IOleInPlaceComponent` se používá k zabránění slučování nabídky OLE 2.

   Implementace `IOleCommandTarget` zpracovává příkazy, jako je **vyjmutí**, **kopírování**a **vkládání**. Při implementaci `IOleCommandTarget`se rozhodněte, zda editor vyžaduje vlastní soubor *.vsct* k definování vlastní struktury [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]příkazové nabídky nebo zda může implementovat standardní příkazy definované uživatelem . Editory obvykle používají a rozšiřují nabídky rozhraní IDE a definují vlastní panely nástrojů. Často je však nutné, aby editor definoval své vlastní specifické příkazy kromě použití standardní sady příkazů rozhraní IDE. Editor musí deklarovat standardní příkazy, které používá, a poté definovat všechny nové příkazy, kontextové nabídky, nabídky nejvyšší úrovně a panely nástrojů v souboru *.vsct.* Pokud vytvoříte editor aktivace na <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> místě, implementujte a definujte nabídky a panely nástrojů pro editor v souboru *.vsct* namísto použití slučování nabídek OLE 2.

- Chcete-li zabránit vysunutí příkazu nabídky v ui, měli byste použít existující příkazy v ide před vynalézání nové příkazy. Sdílené příkazy jsou definovány v *souborech SharedCmdDef.vsct* a *ShellCmdDef.vsct*. Tyto soubory jsou ve výchozím nastavení nainstalovány v podadresáři [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalace VisualStudioIntegration\Common\Inc.

- `ISelectionContainer`vyjadřuje jeden i více výběrů. Každý vybraný objekt je `IDispatch` implementován jako objekt.

- IDE implementuje `IOleUndoManager` jako službu <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> přístupnou z nebo jako objekt, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>který lze vytvořit instanci prostřednictvím . Editor implementuje `IOleUndoUnit` rozhraní `Undo` pro každou akci.

- Vlastní editor může vystavit objekty automatizace na dvou místech:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Viz také

- [Přispějte k modelu automatizace](../extensibility/internals/contributing-to-the-automation-model.md)
