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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591772"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Postup: Zobrazení dědičnosti mezi typy v Návrháři tříd

Vztah dědičnosti, pokud existuje, můžete najít mezi základním typem a jeho odvozenými typy v diagramu třídy v **Návrháři tříd**. Chcete-li vytvořit vztah dědičnosti, pokud neexistuje, mezi dvěma typy, přečtěte si část [Jak: Vytvoření dědičnosti mezi typy](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Vyhledání základního typu

1. V diagramu třídy klikněte na typ, pro který chcete zobrazit základní třídu nebo rozhraní.

2. V nabídce **Diagram tříd** zvolte Zobrazit **základní třídu** nebo **Zobrazit základní rozhraní**.

     V diagramu se zobrazí vybraná základní třída nebo rozhraní typu. Všechny skryté čáry dědičnosti se nyní zobrazí mezi těmito dvěma obrazci.

Můžete také klepnout pravým tlačítkem myši na typ, jehož základní typ chcete zobrazit, a zvolit **Zobrazit základní třídu** nebo **Zobrazit základní rozhraní**.

## <a name="to-find-the-derived-types"></a>Chcete-li najít odvozené typy

1. V diagramu třídy klikněte na typ, pro který chcete zobrazit odvozené třídy nebo rozhraní.

2. V nabídce **Diagram tříd** zvolte **Zobrazit odvozené třídy** nebo **Zobrazit odvozená rozhraní**.

     Odvozené třídy nebo rozhraní typu se zobrazí v diagramu. Mezi obrazci se nyní zobrazí všechny skryté čáry dědičnosti.

Můžete také klepnout pravým tlačítkem myši na typ, pro který chcete zobrazit jeho odvozené typy, a zvolit **Zobrazit odvozené třídy** nebo **Zobrazit odvozené rozhraní**.

## <a name="see-also"></a>Viz také

- [Postup: Vytvoření přidružení mezi typy](how-to-create-associations-between-types.md)
- [Zobrazování typů a vztahů](designing-and-viewing-classes-and-types.md)
