---
title: Poskytnuté služby (zdrojový ovládací prvek VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13be907eeb35a2d4382fb63726c09cb2924e57e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723861"
---
# <a name="services-provided-source-control-vspackage"></a>Poskytované služby (balíček VSPackage správy zdrojového kódu)
Služby jsou primárním mechanismem, pomocí kterého jsou sdílené funkce mezi VSPackage a mezi integrovaným vývojovým prostředím (IDE) sady Visual Studio a jeho nainstalovanými VSPackage. Podrobný popis služeb a jejich důležitost v integrovaném vývojovém prostředí sady Visual Studio najdete v tématu[používání a poskytování služeb](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Služba správy zdrojového kódu
 Sada Visual Studio poskytuje dvě vrstvy služeb, služby na úrovni IDE a služby na úrovni balíčku. Integrované vývojové prostředí sady Visual Studio nativně poskytuje služby na úrovni IDE. Balíček správy zdrojového kódu využívá některé z těchto služeb. Balíček správy zdrojového kódu jako VSPackage sdílí svou funkcionalitu správy zdrojového kódu tím, že poskytuje vlastní službu správy zdrojového kódu. Balíček správy zdrojového kódu zapouzdřuje sadu rozhraní souvisejících se správou zdrojového kódu, které implementuje v podobě kontraktu, který může být použit v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="see-also"></a>Viz také:
- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)