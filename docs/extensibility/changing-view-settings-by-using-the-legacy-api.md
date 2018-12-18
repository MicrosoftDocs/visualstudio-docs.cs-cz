---
title: Změna nastavení zobrazení pomocí starší verze rozhraní API | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f92c4146cc40aff6cf4c73ab3652f68f33a27b51
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077965"
---
# <a name="change-view-settings-by-using-the-legacy-api"></a>Změna nastavení zobrazení pomocí starší verze rozhraní API
Nastavení pro základní funkce editoru, jako je například zalamování řádků, okraj výběru a virtuální prostor, můžete změnit podle uživatele prostřednictvím **možnosti** dialogové okno. Je však také možné změnit tato nastavení programově.  
  
## <a name="change-settings-by-using-the-legacy-api"></a>Změnit nastavení pomocí starší verze rozhraní API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Rozhraní zveřejňuje sadu textový editor vlastností. Zobrazení textu obsahuje kategorie vlastnosti (GUID_EditPropCategory_View_MasterSettings), která reprezentuje skupinu programově změněné nastavení pro zobrazení textu. Po změně nastavení zobrazení tímto způsobem nejde změnit v **možnosti** dialogovému oknu, dokud se obnoví.  
  
 Následuje typický proces pro změnu nastavení zobrazení pro instanci základní editor.  
  
1.  Volání `QueryInterface` na (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> rozhraní.  
  
2.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodu, zadáte třeba hodnotu GUID_EditPropCategory_View_MasterSettings pro `rguidCategory` parametru.  
  
     To vrátí ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> rozhraní, které obsahuje sadu vynucené vlastností pro zobrazení. Všechna nastavení v této skupině jsou trvale vynutit. Pokud nastavení není v této skupině, pak bude dodržovat volby zadané v **možnosti** dialogové okno nebo příkazy uživatele.  
  
3.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metoda určující hodnotu příslušná nastavení v `idprop` parametru.  
  
     Například pokud chcete vynutit zalamování řádků, volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> a zadejte hodnotu VSEDITPROPID_ViewLangOpt_WordWrap, `vt` pro `idprop` parametru. V tomto volání `vt` je varianta typu VT_BOOL a `vt.boolVal` je VARIANT_TRUE.  
  
## <a name="reset-changed-view-settings"></a>Obnovit, změnit nastavení zobrazení  
 Chcete-li obnovit všechny změněné nastavení pro instanci základní editor zobrazení, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> metoda a zadejte hodnotu odpovídající nastavení v `idprop` parametr.  
  
 Například povolit zalamování řádků volně uvolnění, odeberte jej z kategorie vlastnosti voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> a zadáte třeba hodnotu VSEDITPROPID_ViewLangOpt_WordWrap pro `idprop` parametru.  
  
 Pokud chcete odebrat všechny změněné nastavení pro základní editor najednou, zadejte hodnotu VSEDITPROPID_ViewComposite_AllCodeWindowDefaults vt pro `idprop` parametru. V tomto volání vt je varianta typu VT_BOOL a vt.boolVal je VARIANT_TRUE.  
  
## <a name="see-also"></a>Viz také:  
 [V editoru core](../extensibility/inside-the-core-editor.md)   
 [Zobrazit text přístup pomocí starší verze rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Dialogové okno Možnosti](../ide/reference/options-dialog-box-visual-studio.md)