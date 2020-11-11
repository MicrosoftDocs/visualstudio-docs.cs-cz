---
title: Komentáře k úkolům
description: Přidávání komentářů k úkolu do kódu
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493527"
---
# <a name="task-comments"></a>Komentáře k úkolům

Při psaní kódu je standardní praxí explicitně komentovat nedokončený nebo problematický kód nebo rychlé alternativní řešení s upozorněními. Výchozí tokeny signálu, které poskytuje Visual Studio pro Mac, jsou TODO, NAPADENí, FIXME a ZPĚTně. Přizpůsobené tokeny lze definovat v rámci sady **Visual Studio > předvolby > > úlohy prostředí** , jak je znázorněno na následujícím obrázku:

![Předvolby seznamu úkolů](media/source-editor-image10.png)

Chcete-li přidat nový komentář k úkolu, přidejte komentář, který obsahuje klíčové slovo Task. Příklad:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio pro Mac upozorní na tyto značky tím, že je zvýrazní v okně **seznam úkolů** , které lze zobrazit pomocí nabídky **Zobrazit > úkoly** :

![Okno seznam úkolů zobrazující jednu položku TODO](media/source-editor-image11.png)

## <a name="see-also"></a>Viz také

- [Použití Seznam úkolů (Visual Studio ve Windows)](/visualstudio/ide/using-the-task-list)