---
title: Nastavení vodopádu | Nástroj Microsoft IntelliTest Developer test Tool
description: Přečtěte si o nastavení vodopádu, které uspořádá nastavení na úrovni sestavení, přípravku a průzkumu.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2ca1cdcc1da97f8fa0d5def89e4f437607b36dd9
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668752"
---
# <a name="settings-waterfall"></a>Vodopádové nastavení

Koncept nastavení vodopádu znamená, že uživatel může zadat nastavení na úrovni **sestavení**, **přípravné** a **průzkumu** :

* Sestavení – [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Přípravné – [PexClass](attribute-glossary.md#pexclass)
* Průzkum – [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Nastavení zadaná na úrovni **sestavení** ovlivňují všechny přípravné a průzkumy pod tímto sestavením. Nastavení zadaná na úrovni **Přípravosti** má vliv na všechny průzkumy v rámci tohoto přípravku. &mdash;Pokud je nastavení definované v **sestavení** a na úrovních **přípravcích** , použijí **se** nastavení instalace podřízeného objektu.

Všimněte si, že některá nastavení jsou specifická pro úroveň **sestavení** nebo na úrovni **přípravku** .

**Příklad**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Máte zpětnou vazbu?

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://aka.ms/feedback/suggest?space=8).
