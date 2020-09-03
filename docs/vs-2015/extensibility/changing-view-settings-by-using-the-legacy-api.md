---
title: Změna nastavení zobrazení pomocí starší verze rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184469"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Změna nastavení zobrazení pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastavení pro základní funkce editoru, jako je zalamování řádků, okraj výběru a virtuální prostor, může změnit uživatel prostřednictvím dialogového okna **Možnosti** . Tato nastavení je ale možné změnit také programově.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Změna nastavení pomocí starší verze rozhraní API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>Rozhraní zpřístupňuje sadu vlastností textového editoru. Textové zobrazení obsahuje kategorii vlastností (GUID_EditPropCategory_View_MasterSettings), které představují skupinu programově změněné nastavení pro textové zobrazení. Po změně nastavení zobrazení tímto způsobem je nelze změnit v dialogovém okně **Možnosti** , dokud nebudou obnoveny.  
  
 Toto je typický postup pro změnu nastavení zobrazení instance základního editoru.  
  
1. Zavolejte `QueryInterface` na ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> ) pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> rozhraní.  
  
2. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodu a určete hodnotu GUID_EditPropCategory_View_MasterSettings pro `rguidCategory` parametr.  
  
     Tím se vrátí ukazatel na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> rozhraní, které obsahuje sadu vynucených vlastností pro zobrazení. Všechna nastavení v této skupině jsou trvale vynucená. Pokud nastavení není v této skupině, bude následovat po možnostech uvedených v dialogovém okně **Možnosti** nebo v příkazech uživatele.  
  
3. Zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metodu a určete odpovídající hodnotu nastavení v `idprop` parametru.  
  
     Chcete-li například vynutit zalamování řádků, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> a zadejte hodnotu VSEDITPROPID_ViewLangOpt_WordWrap `vt` pro `idprop` parametr. V tomto volání `vt` je typ variant typu VT_BOOL a `vt.boolVal` je VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Resetování změněných nastavení zobrazení  
 Chcete-li obnovit jakékoli změněné nastavení zobrazení pro instanci základního editoru, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> metodu a zadejte odpovídající hodnotu nastavení v `idprop` parametru.  
  
 Například pokud chcete, aby zalamování řádků bylo volné, měli byste jej odebrat z kategorie vlastnosti voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> a určením hodnoty VSEDITPROPID_ViewLangOpt_WordWrap pro `idprop` parametr.  
  
 Chcete-li odebrat všechna změněná nastavení pro základní editor najednou, zadejte hodnotu VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT pro `idprop` parametr. V tomto volání je VT typu VARIANT typu VT_BOOL a VT. boolVal je VARIANT_TRUE.  
  
## <a name="see-also"></a>Viz také  
 [Uvnitř základního editoru](../extensibility/inside-the-core-editor.md)   
 [Přístup k zobrazení theText pomocí starší verze rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Dialogové okno Možnosti](../ide/reference/options-dialog-box-visual-studio.md)
