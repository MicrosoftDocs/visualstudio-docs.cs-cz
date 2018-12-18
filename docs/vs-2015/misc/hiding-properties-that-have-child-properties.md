---
title: Skrývání vlastností, které mají podřízené vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: 76ef9c093bb91bc3cc22df7b56c4d5d69dbc41a5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196518"
---
# <a name="hiding-properties-that-have-child-properties"></a>Skrývání vlastností, které mají podřízené vlastnosti
Chcete skrýt vlastnosti, které mají podřízené vlastnosti:  
  
-   Pokud máte vnořených projektů, kde nadřazený projekt programově řídí některé aspekty podřízeného projektu.  
  
-   Pokud používáte ovládací prvek s specializované návrháře a nechcete dávají vývojářům úplný přístup ke všem vlastnostem ovládacího prvku.  
  
-   Pokud máte obor vlastnictví objektu a chcete omezit zobrazení vlastností.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Skrýt vlastnosti, které mají podřízené vlastnosti  
  
1.  Nastavte `pfDisplay` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> k `FALSE`.  
  
2.  Nastavte `pfHide` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> k `TRUE`.  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení mřížky okna Vlastnosti](../extensibility/internals/properties-display-grid.md)