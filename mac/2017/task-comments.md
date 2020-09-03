---
title: Komentáře k úkolům
description: Přidávání komentářů k úkolu do kódu
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 4f7f3d1567972c3841af6deb37677a7e01cdb825
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985171"
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