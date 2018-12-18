---
title: Aktivace na místě | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
manager: douge
ms.openlocfilehash: 72e6829533b1b314853b8836b8576d0165a87d03
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500342"
---
# <a name="in-place-activation"></a>Aktivace na místě
Pokud je zobrazení editoru hostitelem ActiveX nebo jiné aktivní ovládací prvky, je nutné implementovat editor zobrazení jako ovládací prvek ActiveX nebo jako objekt aktivního dokumentu data pomocí modelu aktivace na místě.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Podpora pro příkazy, nabídky a panely nástrojů  
 Visual Studio umožňuje zobrazení editoru použití nabídek a panelů nástrojů rozhraní IDE. Tato rozšíření jsou označovány jako *OLE místní komponenty*. Další informace najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> a <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 Pokud se rozhodnete implementovat ovládací prvek ActiveX, které můžete hostovat jiné vložené objekty. Pokud se rozhodnete implementovat datový objekt dokumentu, omezí rám okna vaši schopnost používat ovládací prvky ActiveX.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> rozhraní umožňující oddělit data a zobrazení. Ale sady Visual Studio nepodporuje tuto funkci a tato rozhraní se používají pouze k vyjádření objekt zobrazení dokumentu.  
  
 Editory, které používají <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> služba může poskytovat nabídky, nástrojů a integrace příkaz voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> rozhraní implementované <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> služby. Editory můžete také nabízí další funkce sady Visual Studio, jako je například výběr sledování a správu vrátit zpět. Další informace najdete v tématu [vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Objekty a používá rozhraní  
 Na následujícím obrázku se zobrazí objekty, které se používají k vytváření aktivace na místě.  
  
 ![V&#45;umístit Editor aktivace](../extensibility/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Editor aktivace na místě  
  
> [!NOTE]
>  Objekty v tomto kreslení, pouze `CYourEditorFactory` objekt je potřeba vytvořit standardní editor. Pokud vytváříte vlastní editor, není nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> protože editor budou mít svůj vlastní mechanismus privátní trvalosti. Další informace najdete v tématu [vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md).  
  
 Všechna rozhraní, které jsou implementovány vytvořit místní aktivace editoru zobrazují na jedné `CYourEditorDocument` objektu, ale tato konfigurace podporuje pouze jedno zobrazení z dat dokumentu. Další informace o podpoře více zobrazení data vašeho dokumentu, naleznete v tématu [podporovat více zobrazení dokumentů](../extensibility/supporting-multiple-document-views.md).  
  
|Rozhraní|Typ objektu|Použití|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Zobrazit|Umožňuje místní objekty balíčku VSPackage pro provoz jako plně integrované komponenty integrovaného vývojového prostředí pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> služby. Tato služba integruje se s nabídkami, panely nástrojů a příkazy objektu rozhraní IDE a vydá upozornění na změny stavu.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Zobrazit|Hlavní prostředky podle kterého vložený objekt poskytuje základní funkce k jejímu kontejneru a komunikuje s ním.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Zobrazit|Spravuje aktivace a deaktivace objektů na místě a určuje, jak velká část místní objekt by měl být viditelné.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Zobrazit|Poskytuje přímý kanál komunikaci mezi místní objekt, přidružené aplikace nejkrajnější rámec okna a okna dokumentu v aplikaci, která obsahuje vložený objekt.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Zobrazit|Implementuje objekt ActiveX. Všimněte si, že metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> a <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> , že nejsou použity dat samostatné dokumentů a zobrazení v rozhraní IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Data/zobrazení|Povolí datový objekt dokumentu nebo objekt zobrazení dokumentů nebo obojí pro účast při zpracování příkazu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Zobrazit|Povolí aktualizace stavového řádku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Zobrazit|Povolí přidávání položek do panelu nástrojů.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|Odešle oznámení o změnách upravený soubor. (Toto rozhraní je volitelný.)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|Používá k povolení této funkce Uložit jako pro určitý typ souboru.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Data|Povolí trvalost pro dokument. Soubory jen pro čtení, volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> poskytnout ikonu "zamknout", který označuje soubory jen pro čtení.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|Určuje, zda mají být ignorovány změny dat dokumentu.|