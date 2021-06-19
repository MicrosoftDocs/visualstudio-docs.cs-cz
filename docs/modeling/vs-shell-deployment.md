---
title: Nasazení prostředí VS
description: Zjistěte, jak izolované prostředí umožňuje určit, které funkce Visual Studio potřebujete k interakci s vaším DSL a jak by toto řešení mělo vypadat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 946cbf99fa7836fa8d7ec5aa1d921e7cda93bf46
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388305"
---
# <a name="vs-shell-deployment"></a>Nasazení prostředí VS

Izolované prostředí umožňuje určit, které funkce Visual Studio potřebujete k interakci s jazykem specifickým pro doménu a jak by toto řešení mělo vypadat. Další informace o samostatném Visual Studio prostředí najdete v tématu [Přizpůsobení izolovaného prostředí](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Nastavení Visual Studio Shell jako cíle nasazení:

1. V projektu **DslPackage** otevřete **source.extension.tt**.

2. V `<SupportedProducts>` části Vložit:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Nahraďte *MyIsolatedShell* názvem vašeho balíčku izolovaného prostředí.