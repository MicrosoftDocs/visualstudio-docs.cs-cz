---
title: Rozhraní průvodce (IDTWizard) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 78867fa94851e373ae4d47cd82cd1084a941638c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180356"
---
# <a name="wizard-interface-idtwizard"></a>Rozhraní průvodce (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Integrované vývojové prostředí (IDE) používá <xref:EnvDTE.IDTWizard> rozhraní ke komunikaci s průvodci. Průvodci musí implementovat toto rozhraní, aby bylo možné ho nainstalovat do rozhraní IDE.  
  
 <xref:EnvDTE.IDTWizard.Execute%2A>Metoda je jediná metoda přidružená k <xref:EnvDTE.IDTWizard> rozhraní. Průvodci implementují tuto metodu a rozhraní IDE volá metodu na rozhraní. Následující příklad ukazuje signaturu metody.  
  
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
  
 Spouštěcí mechanismus je podobný jak pro **Nový projekt** , tak pro průvodce **přidáním nových položek**. Chcete-li spustit buď, zavolejte <xref:EnvDTE.IDTWizard> rozhraní definované v Dteinternal. h. Jediným rozdílem je sada kontextových a vlastních parametrů, které jsou předány rozhraní při volání rozhraní.  
  
 Následující informace popisují <xref:EnvDTE.IDTWizard> rozhraní, které průvodci musí implementovat pro práci v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE). Rozhraní IDE volá <xref:EnvDTE.IDTWizard.Execute%2A> metodu v průvodci a projde ji následujícím způsobem:  
  
- Objekt DTE  
  
     Objekt DTE je kořenem modelu automatizace.  
  
- Popisovač dialogového okna okna, jak je znázorněno v segmentu kódu, `hwndOwner ([in] long)` .  
  
     Průvodce používá tuto `hwndOwner` položku jako nadřazenou pro dialogové okno průvodce.  
  
- Kontextové parametry předané rozhraní jako typ variant pro SAFEARRAY, jak je znázorněno v segmentu kódu `[in] SAFEARRAY (VARIANT)* ContextParams` .  
  
     Kontextové parametry obsahují pole hodnot, které jsou specifické pro druh spouštěného průvodce a aktuální stav projektu. Rozhraní IDE předá Průvodce kontextovým parametrům. Další informace najdete v tématu [kontextové parametry](../../extensibility/internals/context-parameters.md).  
  
- Vlastní parametry předané do rozhraní jako typ variant pro SAFEARRAY, jak je znázorněno v segmentu kódu `[in] SAFEARRAY (VARIANT)* CustomParams` .  
  
     Vlastní parametry obsahují pole uživatelsky definovaných parametrů. Soubor. vsz předává vlastním parametrům IDE. Hodnoty jsou určeny `Param=` příkazy. Další informace najdete v tématu [vlastní parametry](../../extensibility/internals/custom-parameters.md).  
  
- Návratové hodnoty pro rozhraní jsou  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)   
 [Vlastní parametry](../../extensibility/internals/custom-parameters.md)   
 [Průvodc](../../extensibility/internals/wizards.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
