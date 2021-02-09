---
title: Nasazení prostředí VS
description: Přečtěte si, jak izolované prostředí umožňuje určit, které funkce sady Visual Studio budete potřebovat k interakci s DSL a jak by se mělo toto řešení zobrazit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1293593e71aa57d8e74b9035320b3da5108aba09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924218"
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