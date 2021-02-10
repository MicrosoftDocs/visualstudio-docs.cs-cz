---
title: Rozhraní průvodce (IDTWizard) | Microsoft Docs
description: Rozhraní IDE používá rozhraní IDTWizard ke komunikaci s průvodci. Průvodci musí implementovat toto rozhraní, aby se nainstalovalo v rozhraní IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc33d2fb37db7e021ce1752c642492a80956b61f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935934"
---
# <a name="wizard-interface-idtwizard"></a>Rozhraní průvodce (IDTWizard)
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

 Spouštěcí mechanismus je podobný jak pro **Nový projekt** , tak pro průvodce **přidáním nových položek** . Chcete-li spustit buď, zavolejte <xref:EnvDTE.IDTWizard> rozhraní definované v Dteinternal. h. Jediným rozdílem je sada kontextových a vlastních parametrů, které jsou předány rozhraní při volání rozhraní.

 Následující informace popisují <xref:EnvDTE.IDTWizard> rozhraní, které průvodci musí implementovat pro práci v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE). Rozhraní IDE volá <xref:EnvDTE.IDTWizard.Execute%2A> metodu v průvodci a projde ji následujícím způsobem:

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
- [Kontextové parametry](../../extensibility/internals/context-parameters.md)
- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
