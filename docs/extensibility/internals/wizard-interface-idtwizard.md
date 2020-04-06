---
title: Rozhraní průvodce (IDTWizard) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703280"
---
# <a name="wizard-interface-idtwizard"></a>Rozhraní průvodce (IDTWizard)
Integrované vývojové prostředí (IDE) <xref:EnvDTE.IDTWizard> používá rozhraní ke komunikaci s průvodci. Průvodci musí implementovat toto rozhraní, aby mohly být nainstalovány v rozhraní IDE.

 Metoda <xref:EnvDTE.IDTWizard.Execute%2A> je jedinou metodou <xref:EnvDTE.IDTWizard> přidruženou k rozhraní. Průvodci implementovat tuto metodu a IDE volá metodu na rozhraní. Následující příklad ukazuje podpis metody.

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

 Mechanismus spuštění je podobný pro **průvodce Nový projekt** a Přidat novou **položku.** Chcete-li spustit buď, volání <xref:EnvDTE.IDTWizard> rozhraní definované v Dteinternal.h. Jediným rozdílem je sada kontextu a vlastní parametry, které jsou předány rozhraní při volání rozhraní.

 Následující informace popisují <xref:EnvDTE.IDTWizard> rozhraní, které musí průvodci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementovat, aby fungovalo v rozhraní IDE. Rozhraní IDE <xref:EnvDTE.IDTWizard.Execute%2A> volá metodu v průvodci a předá ji následující:

- Objekt DTE

     DTE objekt je kořen modelu automatizace.

- Úchyt k dialogovému oknu, `hwndOwner ([in] long)`jak je znázorněno v segmentu kódu .

     Průvodce to `hwndOwner` použije jako nadřazený dialog pro dialogové okno průvodce.

- Kontextové parametry předané rozhraní jako varianta pro SAFEARRAY, jak je znázorněno v segmentu kódu . `[in] SAFEARRAY (VARIANT)* ContextParams`

     Parametry kontextu obsahují pole hodnot, které jsou specifické pro druh průvodce, který je spuštěn, a aktuální stav projektu. Rozhraní IDE předá parametry kontextu průvodci. Další informace naleznete [v tématu Context Parameters](../../extensibility/internals/context-parameters.md).

- Vlastní parametry předané rozhraní jako varianta pro SAFEARRAY, `[in] SAFEARRAY (VARIANT)* CustomParams`jak je znázorněno v segmentu kódu .

     Vlastní parametry obsahují pole uživatelem definovaných parametrů. Soubor .vsz předá vlastní parametry rozhraní IDE. Hodnoty jsou určeny `Param=` příkazy. Další informace naleznete [v tématu Vlastní parametry](../../extensibility/internals/custom-parameters.md).

- Vrácené hodnoty pro rozhraní jsou

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Viz také
- [Parametry kontextu](../../extensibility/internals/context-parameters.md)
- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
