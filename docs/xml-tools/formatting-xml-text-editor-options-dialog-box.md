---
title: Formátování, XML, textový Editor, dialogové okno Možnosti
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f92ced5ca5ac007969a06cec7f253617ee293e3
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548788"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formátování, XML, textový editor, dialogové okno Možnosti

Toto dialogové okno umožňuje zadat nastavení formátování pro Editor XML. Dostanete **možnosti** dialogové okno z **nástroje** nabídky.

> [!NOTE]
> Tato nastavení jsou k dispozici, když vyberete **textového editoru** složku, **XML** složku a potom **formátování** možnost z **možnosti** dialogové okno.

## <a name="attributes"></a>Atributy
 **Zachovat formátování ruční atribut**

 Atributy nejsou naformátována. Toto nastavení je výchozí.

> [!NOTE]
> Pokud atributy na více řádků, editor odsadí každý řádek atributů tak, aby odpovídaly odsazení nadřazeného elementu.

 **Zarovnat atributy na své vlastní řádku**

 Zarovnává druhé a následné atributy svisle tak, aby odpovídaly odsazení prvního atributu. Následující text XML je příklad, jak by zarovnán atributy.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automaticky přeformátovat
 **Na vložte ze schránky**

 Přeformátuje textu XML vložené ze schránky.

 **Při dokončení koncová značka**

 Po dokončení koncová značka, přeformátuje elementu.

## <a name="mixed-content"></a>Smíšený obsah
 **Zachovat smíšený obsah ve výchozím nastavení**

 Určuje, zda editor přeformátuje smíšený obsah. Ve výchozím nastavení, pokusí přeformátujte smíšený obsah s výjimkou při nalezení obsahu v editoru `xml:space="preserve"` oboru.

 Pokud element obsahuje směs text a značku, obsah se považují za být smíšený obsah. Následuje příklad prvku s smíšený obsah.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Viz také

- [Vlastnosti dokumentu XML, vlastnosti – okno](../xml-tools/xml-document-properties-properties-window.md)
- [Součásti editoru XML](../xml-tools/xml-editor-components.md)