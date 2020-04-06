---
title: Vlastní parametry | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708938"
---
# <a name="custom-parameters"></a>Vlastní parametry
Vlastní parametry řídí provoz průvodce po spuštění průvodce. Související soubor *.vsz* poskytuje pole uživatelem definovaných parametrů, které jsou zabaleny integrovaným vývojovým prostředím (IDE) a předány průvodci jako pole řetězců při spuštění průvodce. Průvodce pak analyzuje pole řetězců a používá informace k řízení skutečné operace průvodce. Tímto způsobem může průvodce přizpůsobit funkce v závislosti na obsahu souboru *VSZ.*

 Parametry kontextu naopak definují stav projektu při spuštění průvodce. Další informace naleznete [v tématu Context parameters](../../extensibility/internals/context-parameters.md).

 Následuje příklad souboru *.vsz,* který má vlastní parametry:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 Autor souboru *.vsz* přidá hodnoty parametrů. Když uživatel vybere **nový projekt** nebo přidat novou **položku** v **nabídce Soubor** nebo kliknutím pravým tlačítkem myši na projekt v **Průzkumníku řešení**, ide shromažďuje tyto hodnoty do pole řetězců. Rozhraní IDE pak volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodu <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> projektu s příznakem set <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> a projekt volá metodu, která je zodpovědná za spuštění průvodce a vrácení výsledku.

 Průvodce je zodpovědný za analýzu pole řetězců a odpovídající působení na řetězce. Tímto způsobem implementací vlastníparametry můžete vytvořit jeden průvodce, který provádí různé funkce. Jinými slovy, jeden průvodce může mít tři různé soubory *.vsz.* Každý soubor předá různé sady vlastních parametrů pro řízení chování průvodce v různých situacích.

 Další informace naleznete v [průvodci (.vsz) soubor](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Kontextové parametry](../../extensibility/internals/context-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor Průvodce (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
