---
title: Místní aktivace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 192274d087731f68cb7e01c1da20e80cbfef0360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802933"
---
# <a name="in-place-activation"></a>Místní aktivace
Pokud zobrazení editoru hostuje prvky ActiveX nebo jiné aktivní ovládací prvky, je nutné implementovat zobrazení editoru buď jako ovládací prvek ActiveX, nebo jako datový objekt aktivní dokument pomocí modelu aktivace na místě.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Podpora nabídek, panelů nástrojů a příkazů  
 Visual Studio umožňuje zobrazení editoru používat nabídky a panely nástrojů rozhraní IDE. Tato rozšíření se označují jako *místní komponenty OLE*. Další informace naleznete v tématech <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> a <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> .  
  
 Pokud implementujete ovládací prvek ActiveX, můžete hostovat další vložené objekty. Pokud implementujete datový objekt dokumentu, rámec okna omezuje schopnost používat ovládací prvky ActiveX.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>Rozhraní a <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> umožňují oddělení dat a zobrazení. Visual Studio však tuto funkci nepodporuje a tato rozhraní slouží pouze k reprezentaci objektu zobrazení dokumentu.  
  
 Editory, které používají <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> službu, mohou poskytnout nabídku, panel nástrojů a integraci příkazů voláním metod <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> rozhraní implementovaného <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> službou. Editory mohou také nabízet jiné funkce sady Visual Studio, jako je sledování výběru a Správa zpět. Další informace najdete v tématu [vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Použité objekty a rozhraní  
 Následující obrázek ukazuje objekty, které slouží k vytvoření místní aktivace.  
  
 ![V editoru aktivace&#45;umístění](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Editor místních aktivací  
  
> [!NOTE]
> Z objektů v tomto výkresu `CYourEditorFactory` je k vytvoření standardního editoru nutné pouze objekt. Pokud vytváříte vlastní editor, nemusíte implementovat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> protože editor bude pravděpodobně mít vlastní privátní mechanismus trvalosti. Další informace najdete v tématu [vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md).  
  
 Všechna rozhraní, která jsou implementována pro vytvoření vloženého editoru aktivace, jsou zobrazena v jednom `CYourEditorDocument` objektu, ale tato konfigurace podporuje pouze jeden pohled na data dokumentu. Další informace o podpoře více zobrazení dat dokumentu najdete v tématu [Podpora více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md).  
  
|Rozhraní|Typ objektu|Použití|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Zobrazení|Umožňuje místní objekty VSPackage pracovat jako plně integrované komponenty rozhraní IDE pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> služby. Tato služba integruje nabídky, panely nástrojů a příkazy objektu do integrovaného vývojového prostředí (IDE) a vydá oznámení o změnách stavu.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Zobrazení|Objekt zabezpečení znamená, že vložený objekt poskytuje kontejneru základní funkce a komunikuje s ním.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Zobrazení|Spravuje aktivaci a deaktivaci místních objektů a určuje, jak velká část objektu na místě by měla být viditelná.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Zobrazení|Poskytuje přímý kanál komunikace mezi místním objektem, oknem vnějšího rámce přidružené aplikace a oknem dokumentu v aplikaci, která obsahuje vložený objekt.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Zobrazení|Implementuje objekt ActiveX. Všimněte si, že metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> a `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` které oddělené data dokumentů a zobrazení se v integrovaném vývojovém prostředí nepoužívají.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Zobrazit/data|Povolí objekt data dokumentu nebo zobrazení dokumentu nebo obojí, aby se mohl zúčastnit zpracování příkazů.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Zobrazení|Povolí aktualizace stavového řádku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Zobrazení|Umožňuje přidat položky do sady nástrojů.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|Pošle oznámení o změnách upravovaného souboru. (Toto rozhraní je volitelné.)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|Slouží k povolení funkce Uložit jako pro typ souboru.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Data|Povoluje stálost dokumentu. Pro soubory, které jsou jen pro čtení, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> k poskytnutí ikony "Lock", která označuje soubory jen pro čtení.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|Určuje, zda se změny dat dokumentu mají ignorovat.|