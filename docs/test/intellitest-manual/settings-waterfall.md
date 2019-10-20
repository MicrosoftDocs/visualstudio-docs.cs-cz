---
title: Nastavení vodopádu | Nástroj Microsoft IntelliTest Developer test Tool
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: ad5f03d7722fa2fb8452b6a1217c18996d6c978f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653158"
---
# <a name="settings-waterfall"></a>Vodopádové nastavení

Koncept nastavení vodopádu znamená, že uživatel může zadat nastavení na úrovni **sestavení**, **přípravné**a **průzkumu** :

* Sestavení – [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Přípravné – [PexClass](attribute-glossary.md#pexclass)
* Průzkum – [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Nastavení zadaná na úrovni **sestavení** ovlivňují všechny přípravné a průzkumy pod tímto sestavením. Nastavení zadaná na úrovni **Přípravosti** má vliv na všechny průzkumy v rámci tohoto přípravku. @No__t_0if, které se nastavují podřízená nastavení, se definuje v **sestavení** a na úrovních **přípravku** se použijí nastavení **přípravku** .

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

Publikujte své nápady a žádosti o funkce na [komunitě vývojářů](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).