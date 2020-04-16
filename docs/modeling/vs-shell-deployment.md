---
title: Nasazení prostředí VS
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444996"
---
# <a name="vs-shell-deployment"></a>Nasazení prostředí VS

Izolované prostředí umožňuje určit, které funkce sady Visual Studio je třeba pracovat s jazykem specifickým pro doménu a jak by se mělo toto řešení zobrazit. Další informace o izolované prostředí sady Visual Studio naleznete v [tématu Přizpůsobení izolovaného prostředí](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Nastavení prostředí Visual Studio jako cíle nasazení:

1. V projektu **DslPackage** otevřete **source.extension.tt**.

2. Pod `<SupportedProducts>` vložkou:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Nahraďte *myisolatedshell* názvem izolovaného balíčku prostředí.
