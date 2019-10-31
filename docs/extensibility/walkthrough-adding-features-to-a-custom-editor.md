---
title: 'Návod: Přidání funkcí do vlastního editoru | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5ea1c1bfa34399f4a2428aec2f51f97c9884216
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189057"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Návod: Přidání funkcí do vlastního editoru
Po vytvoření vlastního editoru můžete do něj přidat další funkce.

## <a name="to-create-an-editor-for-a-vspackage"></a>Vytvoření editoru pro VSPackage

1. Vytvořte vlastní editor pomocí šablony projektu balíčku sady Visual Studio.

     Další informace najdete v tématu [Návod: Vytvoření vlastního editoru](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Rozhodněte, zda chcete, aby Editor podporoval jedno nebo více zobrazení.

     Editor, který podporuje **Nový příkaz okna** , nebo zobrazení formuláře a zobrazení kódu, vyžaduje samostatné objekty dokumentu dat a objekty zobrazení dokumentu. V editoru, který podporuje pouze jedno zobrazení, lze objekt dat dokumentu a objekt zobrazení dokumentu implementovat na stejný objekt.

     Příklad více zobrazení najdete v tématu [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md).

3. Implementaci objektu pro vytváření editoru pomocí nastavení rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>.

     Další informace najdete v tématu [objekty pro vytváření editorů](../extensibility/editor-factories.md).

4. Rozhodněte, zda chcete, aby Editor používal místní aktivaci nebo zjednodušené vložení pro správu okna zobrazení dokumentu.

     Zjednodušené okno editoru vkládání je hostitelem standardního zobrazení dokumentu, zatímco místní okno editoru aktivace hostuje ovládací prvek ActiveX nebo jiný aktivní objekt jako jeho zobrazení dokumentu. Další informace najdete v tématu [zjednodušené vkládání](../extensibility/simplified-embedding.md) a [místní aktivace](../extensibility/in-place-activation.md).

5. Implementujte rozhraní <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pro zpracování příkazů.

6. Poskytněte trvalá a odezva dokumentu na změny externích souborů:

    1. Chcete-li zachovat soubor, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> a <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> v objektu dokumentu data editoru.

    2. Chcete-li reagovat na změny v externích souborech, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> v objektu dokumentu data editoru.

        > [!NOTE]
        > Chcete-li získat ukazatel na `IVsFileChangeEx`, zavolejte `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>.

7. Koordinuje události úprav dokumentu pomocí správy zdrojového kódu. Postupujte podle těchto kroků:

    1. Získejte ukazatel na `IVsQueryEditQuerySave2` voláním `QueryService` na <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.

    2. Když dojde k první události Edit, zavolejte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>.

         Tato metoda vyzve uživatele k rezervaci souboru, pokud již není rezervován. Ujistěte se, že je pro chyby AVERT zapracovaná podmínka "soubor nebyl zaregistrován".

    3. Podobně před uložením souboru volejte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>.

         Tato metoda vyzve uživatele k uložení souboru, pokud nebyl uložen nebo byl od posledního uložení změněn.

8. V okně **vlastnosti** povolte zobrazení vlastností textu vybraného v editoru. Postupujte podle těchto kroků:

    1. Volejte <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> pokaždé, když se změní výběr textu, který předává implementaci <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.

    2. Chcete-li získat ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>, zavolejte `QueryService` ve službě <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.

9. Umožňuje uživatelům přetahovat položky mezi editorem a **panelem nástrojů**nebo mezi externími editory (jako je Microsoft Word) a **panelem nástrojů**. Postupujte podle těchto kroků:

    1. Implementujte `IDropTarget` v editoru, abyste mohli upozornit rozhraní IDE, že váš Editor je cílem přetažení.

    2. Implementujte rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> v zobrazení, aby mohl Editor povolit a zakázat položky v **sadě nástrojů**.

    3. Implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> a zavolejte `QueryService` ve službě <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox>, abyste získali ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> rozhraní.

         Tyto kroky umožňují, aby VSPackage přidal nové položky do **sady nástrojů**.

10. Rozhodněte, zda chcete pro Editor používat jiné volitelné funkce.

    - Pokud chcete, aby Editor podporoval příkazy Find a Replace, implementujte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.

    - Pokud chcete použít okno nástrojů Osnova dokumentu v editoru, implementujte `IVsDocOutlineProvider`.

    - Pokud chcete použít stavový řádek v editoru, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> a zavolejte `QueryService` pro <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>, abyste získali ukazatel na `IVsStatusBar`.

         Editor například může zobrazit informace o řádku/sloupci, režim výběru (datový proud/rámeček) a režim vkládání (vložení/přepisování).

    - Pokud chcete, aby Editor podporoval příkaz `Undo`, doporučuje se použít model OLE Undo Manager. Alternativně můžete mít editor, který přímo zpracovává příkaz `Undo`.

11. Vytvořte informace registru včetně identifikátorů GUID pro VSPackage, nabídky, editor a další funkce.

     Následuje obecný příklad kódu, který byste umístili do skriptu souboru *. rgs* , který ukazuje, jak správně zaregistrovat Editor.

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

12. Implementujte podporu kontextově závislého pomocníka.

     Tento krok vám umožní poskytnout nápovědu a okno dynamické pomoci pro položky v editoru. Další informace naleznete v tématu [How to: Poskytněte kontext pro editory](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Vystavte objektový model automatizace z editoru implementací rozhraní `IDispatch`.

     Další informace najdete v tématu [přispívání do modelu automatizace](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Robustní programování

- Instance editoru je vytvořena, když rozhraní IDE volá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Pokud editor podporuje více zobrazení, `CreateEditorInstance` vytvoří data dokumentu a objekty zobrazení dokumentu. Pokud je objekt dat dokumentu již otevřen, je `IVsEditorFactory::CreateEditorInstance`hodnota, která není null, `punkDocDataExisting` předána. Vaše implementace továrny v editoru musí určit, zda je existující datový objekt dokumentu kompatibilní s dotazem na příslušná rozhraní. Další informace najdete v tématu [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md).

- Pokud používáte zjednodušený přístup k vkládání, implementujte rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>.

- Pokud se rozhodnete použít místní aktivaci, implementujte tato rozhraní:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > Rozhraní `IOleInPlaceComponent` slouží k zamezení sloučení nabídky OLE 2.

   Vaše implementace `IOleCommandTarget` zpracovává příkazy, jako je **vyjmutí**, **kopírování**a **vložení**. Při implementaci `IOleCommandTarget`se rozhodněte, zda editor vyžaduje vlastní soubor *. vsct* pro definování vlastní struktury nabídky příkazu, nebo pokud může implementovat standardní příkazy definované pomocí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Editory obvykle používají a rozšíří nabídky rozhraní IDE a definují vlastní panely nástrojů. Často je ale nutné, aby Editor Kromě použití standardní sady příkazů IDE definoval vlastní konkrétní příkazy. Editor musí deklarovat standardní příkazy, které používá, a potom definovat všechny nové příkazy, kontextové nabídky, nabídky nejvyšší úrovně a panely nástrojů v souboru *. vsct* . Pokud vytvoříte místní aktivační editor, implementujte <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> a definujte nabídky a panely nástrojů pro Editor v souboru *. vsct* namísto použití sloučení nabídky OLE 2.

- Chcete-li zabránit převrácení příkazu nabídky v uživatelském rozhraní, měli byste použít existující příkazy v integrovaném vývojovém prostředí před započetím nových příkazů. Sdílené příkazy jsou definovány v *SharedCmdDef. vsct* a *ShellCmdDef. vsct*. Tyto soubory jsou ve výchozím nastavení nainstalovány v podadresáři VisualStudioIntegration\Common\Inc instalace [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].

- `ISelectionContainer` může vyjádřit jednu i více výběrů. Každý vybraný objekt je implementován jako objekt `IDispatch`.

- Rozhraní IDE implementuje `IOleUndoManager` jako službu přístupnou z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> nebo jako objekt, který lze vytvořit pomocí <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Editor implementuje rozhraní `IOleUndoUnit` pro každou akci `Undo`.

- Existují dvě místa, kde vlastní editor může vystavovat automatizační objekty:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Viz také:

- [Přispívání do modelu automatizace](../extensibility/internals/contributing-to-the-automation-model.md)