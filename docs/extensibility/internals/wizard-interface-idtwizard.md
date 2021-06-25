---
title: Průvodce rozhraním (IDTWizard) | Microsoft Docs
description: Integrované vývojové prostředí (IDE) používá ke komunikaci s průvodci rozhraní IDTWizard. Průvodci musí implementovat toto rozhraní, aby bylo možné ho nainstalovat do integrovaného vývojového prostředí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 930996de7fa5366463ec2d60f7cf96d941f6c243
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898614"
---
# <a name="wizard-interface-idtwizard"></a>Rozhraní průvodce (IDTWizard)
Integrované vývojové prostředí (IDE) používá rozhraní <xref:EnvDTE.IDTWizard> ke komunikaci s průvodci. Průvodci musí toto rozhraní implementovat, aby bylo možné ho nainstalovat do integrovaného vývojového prostředí.

 Metoda <xref:EnvDTE.IDTWizard.Execute%2A> je jedinou metodou přidruženou k rozhraní <xref:EnvDTE.IDTWizard> . Průvodci implementují tuto metodu a integrované vývojové prostředí volá metodu v rozhraní . Následující příklad ukazuje podpis metody .

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

 Mechanismus spuštění je podobný pro průvodce **nový projekt** i **pro přidání** nové položky. Pokud chcete začít, zavoláte <xref:EnvDTE.IDTWizard> rozhraní definované v souboru Dteinternal.h. Jediným rozdílem je sada kontextových a vlastních parametrů, které jsou předány rozhraní při volání rozhraní.

 Následující informace popisují <xref:EnvDTE.IDTWizard> rozhraní, které průvodci musí implementovat, aby fungovalo v integrovaném vývojovém [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí. Integrované vývojové prostředí <xref:EnvDTE.IDTWizard.Execute%2A> volá metodu v průvodci a předává ji následujícím způsobem:

- Objekt DTE

     Objekt DTE je kořenem modelu Automation.

- Popisovač dialogového okna, jak je znázorněno v segmentu kódu, `hwndOwner ([in] long)` .

     Průvodce ho použije `hwndOwner` jako nadřazenou položku pro dialogové okno průvodce.

- Kontextové parametry předané rozhraní jako varianta pro SAFEARRAY, jak je znázorněno v segmentu kódu , `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Kontextové parametry obsahují pole hodnot, které jsou specifické pro typ spuštěných průvodců a aktuální stav projektu. Integrované vývojové prostředí (IDE) předá průvodci kontextové parametry. Další informace najdete v tématu [Kontextové parametry](../../extensibility/internals/context-parameters.md).

- Vlastní parametry předané rozhraní jako varianta pro SAFEARRAY, jak je znázorněno v segmentu kódu `[in] SAFEARRAY (VARIANT)* CustomParams` , .

     Vlastní parametry obsahují pole uživatelsky definovaných parametrů. Soubor .vsz předává do integrovaného vývojového prostředí vlastní parametry. Hodnoty jsou určeny příkazy `Param=` . Další informace najdete v tématu [Vlastní parametry.](../../extensibility/internals/custom-parameters.md)

- Návratové hodnoty pro rozhraní jsou

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Viz také
- [Kontextové parametry](../../extensibility/internals/context-parameters.md)
- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
