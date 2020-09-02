---
title: Skrytí vlastností s podřízenými vlastnostmi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822383"
---
# <a name="hiding-properties-that-have-child-properties"></a>Skrytí vlastností s podřízenými vlastnostmi
Chcete skrýt vlastnosti s podřízenými vlastnostmi:  
  
- Pokud máte vnořené projekty, kde nadřízený projekt programově řídí některé aspekty podřízeného projektu.  
  
- Použijete-li ovládací prvek se specializovaným návrhářem a nechcete vývojářům poskytnout úplný přístup ke všem vlastnostem ovládacího prvku.  
  
- Pokud máte vlastnictví oboru objektu a chcete omezit zobrazení vlastností.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Skrytí vlastností s podřízenými vlastnostmi  
  
1. Nastavte `pfDisplay` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> na `FALSE` .  
  
2. Nastavte `pfHide` parametr v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> na `TRUE` .  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení mřížky okna Vlastnosti](../extensibility/internals/properties-display-grid.md)