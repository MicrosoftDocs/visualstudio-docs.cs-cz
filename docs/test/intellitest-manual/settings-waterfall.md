---
title: Nastavení vodopádu | Nástroj Microsoft IntelliTest Developer test Tool
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 95a2029cee1fd13241aba727f671a164d7272543
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591577"
---
# <a name="settings-waterfall"></a>Vodopádové nastavení

Koncept nastavení vodopádu znamená, že uživatel může zadat nastavení na úrovni **sestavení**, **přípravné**a **průzkumu** :

* Sestavení – [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Přípravné – [PexClass](attribute-glossary.md#pexclass)
* Průzkum – [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Nastavení zadaná na úrovni **sestavení** ovlivňují všechny přípravné a průzkumy pod tímto sestavením. Nastavení zadaná na úrovni **Přípravosti** má vliv na všechny průzkumy v rámci tohoto přípravku. Pokud je nastavení definované v **sestavení** a na úrovních **přípravcích** , použijí **se nastavení, která se** nahraje&mdash;

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
