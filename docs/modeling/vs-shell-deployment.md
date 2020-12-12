---
title: Nasazení prostředí VS
description: Přečtěte si, jak izolované prostředí umožňuje určit, které funkce sady Visual Studio budete potřebovat k interakci s DSL a jak by se mělo toto řešení zobrazit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94cffbf5ea1f7ac3c437a4c22f27f881d5493e79
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361258"
---
# <a name="vs-shell-deployment"></a>Nasazení prostředí VS

Izolované prostředí vám umožní určit, které funkce sady Visual Studio budete potřebovat k interakci s jazykem konkrétní domény a jak se má toto řešení zobrazit. Další informace o izolovaném prostředí sady Visual Studio najdete v tématu [přizpůsobení izolovaného prostředí](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Chcete-li nastavit prostředí sady Visual Studio jako cíl nasazení:

1. V projektu **DslPackage** otevřete **source.extension.TT**.

2. V části `<SupportedProducts>` Vložit:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Nahraďte *MyIsolatedShell* názvem vašeho balíčku izolovaného prostředí.