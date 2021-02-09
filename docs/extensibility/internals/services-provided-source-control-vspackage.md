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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 515422266ce3d719319c4ba9717106af16e84f9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910997"
---
# <a name="services-provided-source-control-vspackage"></a>Poskytované služby (balíček VSPackage správy zdrojového kódu)
Služby jsou primárním mechanismem, pomocí kterého jsou sdílené funkce mezi VSPackage a mezi integrovaným vývojovým prostředím (IDE) sady Visual Studio a jeho nainstalovanými VSPackage. Podrobný popis služeb a jejich důležitost v integrovaném vývojovém prostředí sady Visual Studio najdete v tématu[používání a poskytování služeb](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Služba správy zdrojového kódu
 Sada Visual Studio poskytuje dvě vrstvy služeb, služby na úrovni IDE a služby na úrovni balíčku. Integrované vývojové prostředí sady Visual Studio nativně poskytuje služby na úrovni IDE. Balíček správy zdrojového kódu využívá některé z těchto služeb. Balíček správy zdrojového kódu jako VSPackage sdílí svou funkcionalitu správy zdrojového kódu tím, že poskytuje vlastní službu správy zdrojového kódu. Balíček správy zdrojového kódu zapouzdřuje sadu rozhraní souvisejících se správou zdrojového kódu, které implementuje v podobě kontraktu, který může být použit v integrovaném vývojovém prostředí sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)
