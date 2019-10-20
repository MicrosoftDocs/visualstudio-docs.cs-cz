---
title: Formátování, XML, textový editor, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670976"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formátování, XML, Textový editor, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno umožňuje zadat nastavení formátování pro editor XML. K dialogovému oknu **Možnosti** získáte přístup z nabídky **nástroje** .

> [!NOTE]
> Tato nastavení jsou k dispozici, když vyberete složku **textový editor** , složku **XML** a pak možnost **formátování** v dialogovém okně **Možnosti** .

## <a name="attributes"></a>Atributy
 **Zachovat ruční formátování atributu** Atributy nejsou přeformátovány. Toto nastavení je výchozí.

> [!NOTE]
> Pokud jsou atributy na více řádcích, Editor odsadí jednotlivé řádky atributů tak, aby odpovídaly odsazení nadřazeného elementu.

 **Zarovnat atributy každý na svůj vlastní řádek** Zarovná druhý a následující atributy svisle tak, aby odpovídaly odsazení prvního atributu. Následující text XML je příkladem, jak by byly atributy zarovnány.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automaticky přeformátovat
 **Při vložení ze schránky** Přeformátuje text XML vložený ze schránky.

 **Po dokončení koncové značky** Přeformátuje prvek po dokončení koncové značky.

## <a name="mixed-content"></a>Smíšený obsah
 **Zachovat smíšený obsah ve výchozím nastavení** Určuje, zda editor přeformátuje smíšený obsah. Ve výchozím nastavení se Editor pokusí o přeformátování smíšeného obsahu s výjimkou případů, kdy se obsah nachází v oboru `xml:space="preserve"`.

 Pokud element obsahuje kombinaci textu a značky, obsah se považuje za smíšený obsah. Následuje příklad prvku se smíšeným obsahem.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Viz také
 [Vlastnosti dokumentu XML, vlastnosti](../xml-tools/xml-document-properties-properties-window.md) [editoru XML](../xml-tools/xml-editor-components.md) okna
