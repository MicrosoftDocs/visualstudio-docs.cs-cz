---
title: Komentáře k úkolům
description: Přidání komentářů k úkolu do kódu
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692314"
---
# <a name="task-comments"></a>Komentáře k úkolům

Při psaní kódu je standardní maješzvyk explicitně komentovat nedokončený nebo sporný kód nebo rychlá řešení s upozorněními. Výchozí signálové tokeny poskytované Visual Studio pro Mac jsou TODO, HACK, FIXME a UNDONE. Přizpůsobené tokeny lze definovat v části **Visual Studio > Předvolby > prostředí > úkoly**, jak je znázorněno na následujícím obrázku:

![Předvolby seznamu úkolů](media/source-editor-image10.png)

Chcete-li přidat nový komentář k úkolu, přidejte komentář, který obsahuje klíčové slovo úkol. Například:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio pro Mac upozorňuje na tyto značky tím, že je zvýrazní na panelu **Seznam úkolů,** který lze zobrazit tak, že přejdete na **Zobrazit > podložky > úlohu**:

![Panel seznamu úkolů](media/source-editor-image11.png)

## <a name="see-also"></a>Viz také

- [Použití seznamu úloh (Visual Studio v systému Windows)](/visualstudio/ide/using-the-task-list)