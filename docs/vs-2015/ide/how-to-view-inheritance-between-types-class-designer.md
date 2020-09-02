---
title: 'Postupy: zobrazení dědičnosti mezi typy (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1e76d45847d0887b47746c60b836c7acf19d03b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670534"
---
# <a name="how-to-view-inheritance-between-types-class-designer"></a>Postupy: Zobrazení dědičnosti mezi typy (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete najít vztah dědičnosti, pokud existuje, mezi základním typem a jeho odvozenými typy v diagramu tříd v Návrhář tříd. Chcete-li vytvořit vztah dědičnosti, pokud žádný neexistuje, mezi dvěma typy, viz [How to: Create dědičnost mezi typy (návrhář tříd)](../ide/how-to-create-inheritance-between-types-class-designer.md).

### <a name="to-find-the-base-type"></a>Vyhledání základního typu

1. V diagramu tříd klikněte na typ, pro který chcete zobrazit základní třídu nebo rozhraní.

2. V nabídce **Diagram tříd** vyberte možnost **Zobrazit základní třídu** nebo **Zobrazit základní rozhraní**.

    Základní třída nebo rozhraní typu se v diagramu zobrazí jako vybrané. Všechny skryté řádky dědičnosti se nyní zobrazují mezi dvěma tvary.

   Můžete také kliknout pravým tlačítkem na typ, jehož základní typ chcete zobrazit, a zvolit **Zobrazit základní třídu** nebo **Zobrazit základní rozhraní**.

### <a name="to-find-the-derived-types"></a>Vyhledání odvozených typů

1. V diagramu tříd klikněte na typ, pro který chcete zobrazit odvozené třídy nebo rozhraní.

2. V nabídce **Diagram tříd** vyberte možnost **Zobrazit odvozené třídy** nebo **Zobrazit odvozená rozhraní**.

    V diagramu se zobrazí odvozené třídy nebo rozhraní typu. Mezi tvary se nyní zobrazí všechny skryté řádky dědičnosti.

   Můžete také kliknout pravým tlačítkem na typ, pro který chcete zobrazit jeho odvozené typy, a zvolit možnost **Zobrazit odvozené třídy** nebo **Zobrazit odvozená rozhraní**.

## <a name="see-also"></a>Viz také
 [Postupy: vytváření asociací mezi typy (návrhář tříd)](../ide/how-to-create-associations-between-types-class-designer.md) [zobrazení typů a vztahů (návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md)
