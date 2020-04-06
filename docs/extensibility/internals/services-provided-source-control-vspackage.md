---
title: Poskytované služby (správa zdrojového kódu VSPackage) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705412"
---
# <a name="services-provided-source-control-vspackage"></a>Poskytované služby (balíček VSPackage správy zdrojového kódu)
Služby jsou primární mechanismus, jehož prostřednictvím je funkce sdílena mezi VSPackages a mezi integrovaným vývojového prostředí Sady Visual Studio (IDE) a jeho nainstalovaným balíčkem VSPackages. Podrobný popis služeb a jejich důležitost v ide sady Visual Studio naleznete v[tématu Using and Providing Services](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Služba správy zdrojového kódu
 Visual Studio poskytuje dvě vrstvy služeb, služby na úrovni IDE a služby na úrovni balíčků. IDE sady Visual Studio nativně poskytuje služby na úrovni ide. Balíček správy zdrojového kódu spotřebovává některé z těchto služeb. Balíček správy zdrojového kódu jako VSPackage sdílí jeho funkce správy zdrojového kódu tím, že poskytuje vlastní soukromou službu správy zdrojového kódu. Balíček správy zdrojového kódu zapouzdřuje sadu rozhraní souvisejících se slučovacím řízením, které implementuje ve formě smlouvy, kterou lze použít rozhraní MDE sady Visual Studio.

## <a name="see-also"></a>Viz také
- [Prvky návrhu](../../extensibility/internals/source-control-vspackage-design-elements.md)
