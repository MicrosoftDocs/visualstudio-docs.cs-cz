---
title: Vlastní parametry | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a595861be835ec1aaa7079b3e3fe1962d5055e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154999"
---
# <a name="custom-parameters"></a>Vlastní parametry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vlastní parametry řídí operaci průvodce po spuštění průvodce. Související soubor. vsz poskytuje pole uživatelsky definovaných parametrů, které jsou zabaleny integrovaným vývojovým prostředím (IDE) a předány do průvodce jako pole řetězců při spuštění průvodce. Průvodce pak analyzuje pole řetězců a používá informace k řízení skutečné operace průvodce. Tímto způsobem může průvodce přizpůsobit funkčnost v závislosti na obsahu souboru. vsz.  
  
 Kontextové parametry na druhé straně definují stav projektu po spuštění průvodce. Další informace najdete v tématu [kontextové parametry](../../extensibility/internals/context-parameters.md).  
  
 Následuje příklad souboru. vsz, který má vlastní parametry:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 Autor souboru. vsz přidá hodnoty parametrů. Když uživatel vybere **Nový projekt** nebo **přidá novou položku** v nabídce soubor nebo klikne pravým tlačítkem myši na projekt v **Průzkumník řešení**, rozhraní IDE tyto hodnoty shromáždí do pole řetězců. Rozhraní IDE pak zavolá metodu projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> se <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> sadou příznaků a projekt volá <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> metodu, která je zodpovědná za spuštění průvodce a vrácení výsledku.  
  
 Průvodce zodpovídá za analýzu pole řetězců a odpovídajícím způsobem v řetězcích. Tímto způsobem implementací vlastních parametrů můžete vytvořit jednoho průvodce, který provede celou řadu funkcí. Jinými slovy, jeden Průvodce může mít tři různé soubory. vsz. Každý soubor předává různé sady vlastních parametrů pro řízení chování průvodce v různých situacích.  
  
 Další informace najdete v tématu [Průvodce (. VSZ – soubor](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Kontextové parametry](../../extensibility/internals/context-parameters.md)   
 [Průvodc](../../extensibility/internals/wizards.md)   
 [Soubor průvodce (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
