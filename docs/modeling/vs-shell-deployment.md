---
title: Nasazení prostředí VS
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8793312e0ed022fc7210508efdf20a81b293f0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535847"
---
# <a name="vs-shell-deployment"></a>Nasazení prostředí VS

Izolované prostředí vám umožní určit, které funkce sady Visual Studio budete potřebovat k interakci s jazykem konkrétní domény a jak se má toto řešení zobrazit. Další informace o izolovaném prostředí sady Visual Studio najdete v tématu [přizpůsobení izolovaného prostředí](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Chcete-li nastavit prostředí sady Visual Studio jako cíl nasazení:

1. V projektu **DslPackage** otevřete **source.extension.TT**.

2. V části `<SupportedProducts>` Vložit:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Nahraďte *MyIsolatedShell* názvem vašeho balíčku izolovaného prostředí.
