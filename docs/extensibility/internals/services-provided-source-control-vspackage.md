---
title: Služby poskytované (Zdroj ovládacího prvku VSPackage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a52ffa7067a91582d8bfe31e09d6b03be54c4ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129599"
---
# <a name="services-provided-source-control-vspackage"></a>Služby poskytované (Zdroj ovládacího prvku VSPackage)
Služby jsou primární mechanismus, pomocí kterého je funkce sdílené mezi VSPackages a mezi integrované vývojové prostředí (IDE) sady Visual Studio a jeho nainstalované VSPackages. Podrobný popis služeb a jejich důležitosti v integrovaném vývojovém prostředí sady Visual Studio naleznete v tématu[pomocí a poskytování služeb](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Službu Řízení zdroje  
 Visual Studio poskytuje dvě vrstvy služeb, IDE úroveň služby a služby na úrovni balíčku. Visual Studio IDE nativně poskytuje služby na úrovni IDE. Zdrojový balíček ovládací prvek využívá některé z těchto služeb. Zdrojový balíček ovládací prvek jako VSPackage sdílí jeho funkce správy zdrojového tím, že poskytuje službu privátní zdroj ovládacího prvku vlastní. Zdrojový balíček řízení zapouzdří sadu zdroje související ovládací prvek rozhraní implementované ji ve formě kontrakt, který je použít v prostředí Visual Studio IDE.  
  
## <a name="see-also"></a>Viz také  
 [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)