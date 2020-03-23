---
title: Nastavení vodopád | Testovací nástroj pro vývojáře IntelliTest společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591577"
---
# <a name="settings-waterfall"></a>Vodopádové nastavení

Koncept vodopádu nastavení znamená, že uživatel může určit nastavení na úrovni **Sestavení**, **Svítidlo**a **Průzkum:**

* Sestava - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Svítidlo - [PexClass](attribute-glossary.md#pexclass)
* Průzkum - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Nastavení určená na úrovni **sestavy** ovlivňují všechna svítidla a průzkum v rámci této sestavy. Nastavení určená na úrovni **svítidla** ovlivňují všechny průzkumy v rámci tohoto přípravku. Podřízené&mdash;nastavení vyhraje, pokud je nastavení definováno na úrovních **sestavy** a **uchycení,** použijí se nastavení **uchycení.**

Všimněte si, že některá nastavení jsou specifická pro úroveň **sestavy** nebo **úroveň uchycení.**

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

Své nápady a žádosti o funkce můžete zadávat na webu [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
