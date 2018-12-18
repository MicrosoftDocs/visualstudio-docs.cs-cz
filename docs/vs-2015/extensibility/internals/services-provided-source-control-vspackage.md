---
title: Služby poskytované (řízení zdrojového balíčku VSPackage) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3131acfb26dc1e973314f69fab69cad46df6295
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786636"
---
# <a name="services-provided-source-control-vspackage"></a>Poskytované služby (balíček VSPackage správy zdrojového kódu)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Služby představují hlavní mechanismus, pomocí kterého je funkce sdílené mezi rozšíření VSPackages a mezi integrovaného vývojového prostředí (IDE) sady Visual Studio a jeho nainstalované rozšíření VSPackages. Podrobný popis služeb a jejich význam v integrovaném vývojovém prostředí sady Visual Studio najdete v tématu[Using a poskytování služeb](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Službu správy zdrojových kódů  
 Visual Studio poskytuje dvě vrstvy služby, IDE úrovně služby a služby na úrovni balíčku. Integrované vývojové prostředí sady Visual Studio nativně poskytuje služby na úrovni prostředí IDE. Zdrojový balíček ovládací prvek využívá některé z těchto služeb. Zdrojový balíček ovládací prvek jako VSPackage sdílí tím, že poskytuje služby privátní zdrojového ovládacího prvku vlastní jeho funkce správy zdrojového kódu. Zdrojový ovládací prvek balíček zapouzdřuje sadu zdroje týkající se ovládací prvek rozhraní implementované ji ve formě kontrakt, který lze použít v integrovaném vývojovém prostředí sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)

