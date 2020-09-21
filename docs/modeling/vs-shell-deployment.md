---
title: Nasazení prostředí VS
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f3729c09198b331728e2cc67299ffc3ad6c3d26
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809645"
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