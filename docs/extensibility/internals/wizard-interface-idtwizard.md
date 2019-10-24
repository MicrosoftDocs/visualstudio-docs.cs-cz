---
title: Rozhraní průvodce (IDTWizard) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f571fbd0a68ddbf56b637071ac250159461f61d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721533"
---
# <a name="wizard-interface-idtwizard"></a>Rozhraní průvodce (IDTWizard)
Integrované vývojové prostředí (IDE) používá rozhraní <xref:EnvDTE.IDTWizard> ke komunikaci s průvodci. Průvodci musí implementovat toto rozhraní, aby bylo možné ho nainstalovat do rozhraní IDE.

 Metoda <xref:EnvDTE.IDTWizard.Execute%2A> je jediná metoda přidružená k rozhraní <xref:EnvDTE.IDTWizard>. Průvodci implementují tuto metodu a rozhraní IDE volá metodu na rozhraní. Následující příklad ukazuje signaturu metody.

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

 Spouštěcí mechanismus je podobný jak pro **Nový projekt** , tak pro průvodce **přidáním nových položek** . Chcete-li spustit aplikaci, zavolejte rozhraní <xref:EnvDTE.IDTWizard> definované v Dteinternal. h. Jediným rozdílem je sada kontextových a vlastních parametrů, které jsou předány rozhraní při volání rozhraní.

 Následující informace popisují rozhraní <xref:EnvDTE.IDTWizard>, které průvodci musí implementovat pro práci v rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Rozhraní IDE volá metodu <xref:EnvDTE.IDTWizard.Execute%2A> v průvodci a projde ji následujícím způsobem:

- Objekt DTE

     Objekt DTE je kořenem modelu automatizace.

- Popisovač dialogového okna okna, jak je znázorněno v segmentu kódu, `hwndOwner ([in] long)`.

     Průvodce používá tuto `hwndOwner` jako nadřazený pro dialogové okno průvodce.

- Kontextové parametry předané rozhraní jako typ variant pro SAFEARRAY, jak je znázorněno v segmentu kódu `[in] SAFEARRAY (VARIANT)* ContextParams`.

     Kontextové parametry obsahují pole hodnot, které jsou specifické pro druh spouštěného průvodce a aktuální stav projektu. Rozhraní IDE předá Průvodce kontextovým parametrům. Další informace najdete v tématu [kontextové parametry](../../extensibility/internals/context-parameters.md).

- Vlastní parametry předané do rozhraní jako typ variant pro SAFEARRAY, jak je znázorněno v segmentu kódu `[in] SAFEARRAY (VARIANT)* CustomParams`.

     Vlastní parametry obsahují pole uživatelsky definovaných parametrů. Soubor. vsz předává vlastním parametrům IDE. Hodnoty jsou určeny příkazy `Param=`. Další informace najdete v tématu [vlastní parametry](../../extensibility/internals/custom-parameters.md).

- Návratové hodnoty pro rozhraní jsou

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Viz také:
- [Kontextové parametry](../../extensibility/internals/context-parameters.md)
- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)