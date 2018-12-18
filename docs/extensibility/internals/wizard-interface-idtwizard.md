---
title: Rozhraní průvodce (IDTWizard) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f1bc71239ff7923676c35496e103223a6b6e56e
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219858"
---
# <a name="wizard-interface-idtwizard"></a>Rozhraní průvodce (IDTWizard)
Integrované vývojové prostředí (IDE) používá <xref:EnvDTE.IDTWizard> rozhraní ke komunikaci s použitím průvodců. Průvodce musí implementovat toto rozhraní k instalaci v integrovaném vývojovém prostředí.  
  
 <xref:EnvDTE.IDTWizard.Execute%2A> Metoda je jedinou metodou přidružené <xref:EnvDTE.IDTWizard> rozhraní. Tuto metodu implementovat průvodců a integrovaného vývojového prostředí volá metodu rozhraní. Následující příklad ukazuje podpis metody.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 Mechanismus start je podobné jako u obou **nový projekt** a **přidat novou položku** průvodců. Spustit buď, volání <xref:EnvDTE.IDTWizard> rozhraní definované v Dteinternal.h. Jediným rozdílem je sada kontextu a vlastní parametry, které jsou předány do rozhraní při volání rozhraní.  
  
 Následující informace popisují <xref:EnvDTE.IDTWizard> rozhraní, které průvodce musí implementovat pro práci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí. Volání rozhraní IDE <xref:EnvDTE.IDTWizard.Execute%2A> metoda v průvodci, předají se jí následující:  
  
-   Objekt DTE  
  
     Objekt DTE je kořen modelu automatizace.  
  
-   Popisovač do dialogového okna okno, jak je znázorněno v segmentu kódu `hwndOwner ([in] long)`.  
  
     Tento průvodce využívá `hwndOwner` jako nadřazený pro dialogové okno průvodce.  
  
-   Kontextové parametry předány rozhraní jako typ variant SAFEARRAY jak je znázorněno v segmentu kódu `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Kontextové parametry obsahují pole hodnot, které jsou specifické pro typ, který se spouští Průvodce a aktuální stav projektu. Rozhraní IDE předá kontextové parametry průvodce. Další informace najdete v tématu [kontextových parametrů](../../extensibility/internals/context-parameters.md).  
  
-   Vlastní parametry předané do rozhraní jako hodnotu typu variant pro SAFEARRAY jak je znázorněno v segmentu kódu `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Vlastní parametry obsahovat pole uživatelem definované parametry. Vlastní parametry souboru .vsz předává do integrovaného vývojového prostředí. Hodnoty jsou určeny `Param=` příkazy. Další informace najdete v tématu [vlastní parametry](../../extensibility/internals/custom-parameters.md).  
  
-   Návratové hodnoty pro rozhraní  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)   
 [Vlastní parametry](../../extensibility/internals/custom-parameters.md)   
 [Průvodce](../../extensibility/internals/wizards.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)