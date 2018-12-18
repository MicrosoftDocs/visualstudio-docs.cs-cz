---
title: 'Postupy: Zobrazení dědičnosti mezi typy (návrhář tříd)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3398a5096934397556ae1b20845153bd45a78528
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "34000491"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Postupy: zobrazení dědičnosti mezi typy v Návrháři tříd

Můžete najít vztah dědičnosti, pokud existuje, mezi základní typ a jeho odvozených typů v diagramu tříd v **návrhář tříd**. Chcete-li vytvořit vztah dědičnosti, pokud žádný neexistuje, mezi dvěma typy, přečtěte si téma [postupy: vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>K vyhledání základní typ

1.  Na diagramu tříd klikněte na typ, pro který chcete zobrazit základní třídy nebo rozhraní.

2.  Na **diagramu tříd** nabídce zvolte **zobrazit základní třída** nebo **zobrazit základní rozhraní**.

     Podle typu základní třídy nebo rozhraní zobrazí jako vybraný v diagramu. Všechny řádky skrytá dědičnosti se nyní zobrazí mezi dvěma tvarů.

Můžete také kliknout pravým tlačítkem jehož základní typ, který chcete zobrazit a vyberte typ **zobrazit základní třída** nebo **zobrazit základní rozhraní**.

## <a name="to-find-the-derived-types"></a>Pokud chcete vyhledat odvozené typy

1.  Na diagramu tříd klikněte na typ, pro který chcete zobrazit odvozené třídy nebo rozhraní.

2.  Na **diagramu tříd** nabídce zvolte **Zobrazit odvozené třídy** nebo **Zobrazit odvozené rozhraní**.

     Typ odvozené třídy nebo rozhraní zobrazí diagram. Všechny řádky skrytá dědičnosti se nyní zobrazí mezi obrazce.

Můžete také kliknout pravým tlačítkem typ, pro který chcete zobrazit jeho odvozených typů a zvolte **Zobrazit odvozené třídy** nebo **Zobrazit odvozené rozhraní**.

## <a name="see-also"></a>Viz také

- [Postupy: vytvoření přidružení mezi typy](how-to-create-associations-between-types.md)
- [Zobrazování typů a vztahů](viewing-types-and-relationships.md)