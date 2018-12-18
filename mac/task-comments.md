---
title: Komentáře k úkolu
description: Přidání komentáře k úkolu do kódu
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294276"
---
# <a name="task-comments"></a>Komentáře k úkolu

Při psaní kódu, se standardním postupem chcete explicitně přidat komentář nedokončené nebo problematického kódu a rychlé řešení s upozorněními. Tokeny signál výchozí poskytovaný sadou Visual Studio for Mac jsou TODO, HACK, FIXME a VRÁCENO. Individuální tokeny lze definovat v rámci **sady Visual Studio > Předvolby > prostředí > úlohy**, jak je znázorněno na následujícím obrázku:

![Předvolby seznamu úkolů](media/source-editor-image10.png)

Chcete-li přidat nový komentář k úkolu, přidejte komentář, který obsahuje klíčové slovo úloh. Příklad:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio pro Mac zdůrazňující tyto značky zvýrazněním v **seznamu úkolů** panel, který je možné zobrazit tak, že přejdete do **zobrazení > panely > úlohy**:

![Panel seznamu úloh](media/source-editor-image11.png)

## <a name="see-also"></a>Viz také:

- [Pomocí seznamu úkolů (Visual Studio na Windows)](/visualstudio/ide/using-the-task-list)