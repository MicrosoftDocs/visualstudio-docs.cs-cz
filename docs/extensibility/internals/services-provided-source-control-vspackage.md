---
title: Poskytnuté služby (zdrojový ovládací prvek VSPackage) | Microsoft Docs
description: Přečtěte si, jak VSPackage sdílí funkce prostřednictvím služeb, včetně interakce s IDE sady Visual Studio a jeho VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe1d9ee9805e6e86595f3f7f3cf640114c7030b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080811"
---
# <a name="services-provided-source-control-vspackage"></a>Poskytované služby (balíček VSPackage správy zdrojového kódu)
Služby jsou primárním mechanismem, pomocí kterého jsou sdílené funkce mezi VSPackage a mezi integrovaným vývojovým prostředím (IDE) sady Visual Studio a jeho nainstalovanými VSPackage. Podrobný popis služeb a jejich důležitost v integrovaném vývojovém prostředí sady Visual Studio najdete v tématu[používání a poskytování služeb](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Služba správy zdrojového kódu
 Sada Visual Studio poskytuje dvě vrstvy služeb, služby na úrovni IDE a služby na úrovni balíčku. Integrované vývojové prostředí sady Visual Studio nativně poskytuje služby na úrovni IDE. Balíček správy zdrojového kódu využívá některé z těchto služeb. Balíček správy zdrojového kódu jako VSPackage sdílí svou funkcionalitu správy zdrojového kódu tím, že poskytuje vlastní službu správy zdrojového kódu. Balíček správy zdrojového kódu zapouzdřuje sadu rozhraní souvisejících se správou zdrojového kódu, které implementuje v podobě kontraktu, který může být použit v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)
