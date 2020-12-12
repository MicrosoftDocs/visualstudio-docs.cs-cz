---
title: 'Postupy: Nastavování atributů CLR v elementu'
description: Přečtěte si, jak můžete přidat libovolný atribut, který dědí ze třídy System. Attribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9f8b16edcbe575ebac67f4acde9111a9511b85
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363845"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Postupy: Nastavování atributů CLR v elementu
Vlastní atributy jsou speciální atributy, které lze přidat do doménových prvků, tvarů, spojnic a diagramů. Můžete přidat libovolný atribut, který dědí z `System.Attribute` třídy.

### <a name="to-add-a-custom-attribute"></a>Přidání vlastního atributu

1. V **Průzkumníku DSL** vyberte prvek, ke kterému chcete přidat vlastní atribut.

2. V okně **vlastnosti** vedle vlastnosti **vlastní atributy** klikněte na ikonu Procházet (**...**).

     Otevře se dialogové okno **Upravit atributy** .

3. Ve sloupci **název** klikněte na **\<add attribute>** a zadejte název svého atributu. Stiskněte ENTER.

4. Řádek pod názvem atributu obsahuje závorky. Na tomto řádku zadejte typ parametru pro atribut (například `string` ) a potom stiskněte klávesu ENTER.

5. Do sloupce **vlastnost název** zadejte vhodný název, například `MyString` .

6. Klikněte na **OK**.

     Vlastnost **Custom Attributes** nyní zobrazuje atribut v následujícím formátu:

     `[`*AttributeName* `(` *ParameterName* `=` *Typ*`)]`

## <a name="see-also"></a>Viz také:

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))