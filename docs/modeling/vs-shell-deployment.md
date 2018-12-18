---
title: Nasazení prostředí VS
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61cf6e716f082abf28043d56d1a8803853d894aa
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566670"
---
# <a name="vs-shell-deployment"></a>Nasazení prostředí VS

Izolované prostředí umožňuje určit, které Visual Studio funkce, je nutné pracovat s jazyka specifického pro doménu a jak by se měla zobrazit toto řešení. Další informace o prostředí sady Visual Studio, samostatný, naleznete v tématu [přizpůsobení izolovaného prostředí](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Chcete-li nastavit Visual Studio Shell jako cíle nasazení

1.  V **DslPackage** projekt, otevřete **source.extension.tt**.

2.  V části `<SupportedProducts>` vložit:

    ```xml
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Nahraďte *MyIsolatedShell* s názvem vašeho balíčku izolovaného prostředí.