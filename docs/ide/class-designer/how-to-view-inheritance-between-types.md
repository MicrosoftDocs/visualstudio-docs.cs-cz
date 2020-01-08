---
title: 'Postupy: Zobrazení dědičnosti mezi typy (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47907493451841b631d561bfddb74676a460ff29
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591772"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Postupy: zobrazení dědičnosti mezi typy v Návrhář tříd

Můžete najít vztah dědičnosti, pokud existuje, mezi základním typem a jeho odvozenými typy v diagramu tříd v **Návrhář tříd**. Chcete-li vytvořit vztah dědičnosti, pokud žádný neexistuje, mezi dvěma typy, viz [How to: Create dědičnost mezi typy](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Vyhledání základního typu

1. V diagramu tříd klikněte na typ, pro který chcete zobrazit základní třídu nebo rozhraní.

2. V nabídce **Diagram tříd** vyberte možnost **Zobrazit základní třídu** nebo **Zobrazit základní rozhraní**.

     Základní třída nebo rozhraní typu se v diagramu zobrazí jako vybrané. Všechny skryté řádky dědičnosti se nyní zobrazují mezi dvěma tvary.

Můžete také kliknout pravým tlačítkem na typ, jehož základní typ chcete zobrazit, a zvolit **Zobrazit základní třídu** nebo **Zobrazit základní rozhraní**.

## <a name="to-find-the-derived-types"></a>Vyhledání odvozených typů

1. V diagramu tříd klikněte na typ, pro který chcete zobrazit odvozené třídy nebo rozhraní.

2. V nabídce **Diagram tříd** vyberte možnost **Zobrazit odvozené třídy** nebo **Zobrazit odvozená rozhraní**.

     V diagramu se zobrazí odvozené třídy nebo rozhraní typu. Mezi tvary se nyní zobrazí všechny skryté řádky dědičnosti.

Můžete také kliknout pravým tlačítkem na typ, pro který chcete zobrazit jeho odvozené typy, a zvolit možnost **Zobrazit odvozené třídy** nebo **Zobrazit odvozená rozhraní**.

## <a name="see-also"></a>Viz také:

- [Postupy: vytváření přidružení mezi typy](how-to-create-associations-between-types.md)
- [Zobrazování typů a vztahů](designing-and-viewing-classes-and-types.md)
