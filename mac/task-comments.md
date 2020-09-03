---
title: Komentáře k úkolům
description: Přidávání komentářů k úkolu do kódu
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67692314"
---
# <a name="task-comments"></a>Komentáře k úkolům

Při psaní kódu je standardní praxí explicitně komentovat nedokončený nebo problematický kód nebo rychlé alternativní řešení s upozorněními. Výchozí tokeny signálu, které poskytuje Visual Studio pro Mac, jsou TODO, NAPADENí, FIXME a ZPĚTně. Přizpůsobené tokeny lze definovat v rámci sady **Visual Studio > předvolby > > úlohy prostředí**, jak je znázorněno na následujícím obrázku:

![Předvolby seznamu úkolů](media/source-editor-image10.png)

Chcete-li přidat nový komentář k úkolu, přidejte komentář, který obsahuje klíčové slovo Task. Příklad:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio pro Mac k těmto značkám nakreslí pozornost tím, že je zvýrazníte na panelu **seznam úkolů** , který se dá zobrazit tak, že přejdete na **> úlohu se zobrazením >ového**panelu:

![Panel seznamu úkolů](media/source-editor-image11.png)

## <a name="see-also"></a>Viz také

- [Použití Seznam úkolů (Visual Studio ve Windows)](/visualstudio/ide/using-the-task-list)