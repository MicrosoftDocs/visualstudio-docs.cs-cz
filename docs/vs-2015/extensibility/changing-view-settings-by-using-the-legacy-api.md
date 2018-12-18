---
title: Změna nastavení zobrazení pomocí starší verze rozhraní API | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df84fa92cb0da8dd408b1cc8717628afa3d5ba19
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730635"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Změna nastavení zobrazení pomocí starší verze rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nastavení pro základní funkce editoru, jako je například zalamování řádků, okraj výběru a virtuální prostor, můžete změnit podle uživatele prostřednictvím **možnosti** dialogové okno. Je však také možné změnit tato nastavení programově.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Změna nastavení pomocí starší verze rozhraní API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> Rozhraní zveřejňuje sadu textový editor vlastností. Zobrazení textu obsahuje kategorie vlastnosti (GUID_EditPropCategory_View_MasterSettings), která reprezentuje skupinu programově změněné nastavení pro zobrazení textu. Po změně nastavení zobrazení tímto způsobem nejde změnit v **možnosti** dialogovému oknu, dokud se obnoví.  
  
 Následuje typický proces pro změnu nastavení zobrazení pro instanci základní editor.  
  
1.  Volání `QueryInterface` na (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) pro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> rozhraní.  
  
2.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodu, zadáte třeba hodnotu GUID_EditPropCategory_View_MasterSettings pro `rguidCategory` parametru.  
  
     To vrátí ukazatel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> rozhraní, které obsahuje sadu vynucené vlastností pro zobrazení. Všechna nastavení v této skupině jsou trvale vynutit. Pokud nastavení není v této skupině, pak bude dodržovat volby zadané v **možnosti** dialogové okno nebo příkazy uživatele.  
  
3.  Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metoda určující hodnotu příslušná nastavení v `idprop` parametru.  
  
     Například pokud chcete vynutit zalamování řádků, volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> a zadejte hodnotu VSEDITPROPID_ViewLangOpt_WordWrap, `vt` pro `idprop` parametru. V tomto volání `vt` je varianta typu VT_BOOL a `vt.boolVal` je VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Resetuje se změněné zobrazit nastavení  
 Chcete-li obnovit všechny změněné nastavení pro instanci základní editor zobrazení, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> metoda a zadejte hodnotu odpovídající nastavení v `idprop` parametr.  
  
 Například povolit zalamování řádků volně uvolnění, odeberte jej z kategorie vlastnosti voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> a zadáte třeba hodnotu VSEDITPROPID_ViewLangOpt_WordWrap pro `idprop` parametru.  
  
 Pokud chcete odebrat všechny změněné nastavení pro základní editor najednou, zadejte hodnotu VSEDITPROPID_ViewComposite_AllCodeWindowDefaults vt pro `idprop` parametru. V tomto volání vt je varianta typu VT_BOOL a vt.boolVal je VARIANT_TRUE.  
  
## <a name="see-also"></a>Viz také  
 [Uvnitř základní Editor](../extensibility/inside-the-core-editor.md)   
 [Přístup k text zobrazení pomocí starší verze rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Dialogové okno Možnosti](../ide/reference/options-dialog-box-visual-studio.md)

