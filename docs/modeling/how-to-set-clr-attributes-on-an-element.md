---
title: 'Postupy: Nastavování atributů CLR v elementu'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f943f9713e4432f0b06242a2f66acae6b390e5cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748370"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Postupy: Nastavování atributů CLR v elementu
Vlastní atributy jsou speciální atributy, které lze přidat do doménových prvků, tvarů, spojnic a diagramů. Můžete přidat libovolný atribut, který dědí z třídy `System.Attribute`.

### <a name="to-add-a-custom-attribute"></a>Přidání vlastního atributu

1. V **Průzkumníku DSL**vyberte prvek, ke kterému chcete přidat vlastní atribut.

2. V okně **vlastnosti** vedle vlastnosti **vlastní atributy** klikněte na ikonu Procházet ( **...** ).

     Otevře se dialogové okno **Upravit atributy** .

3. Ve sloupci **název** klikněte na **\<add atributu >** a zadejte název atributu. Stiskněte klávesu ENTER.

4. Řádek pod názvem atributu obsahuje závorky. Na tomto řádku zadejte typ parametru pro atribut (například `string`) a potom stiskněte klávesu ENTER.

5. Do sloupce **vlastnost název** zadejte vhodný název, například `MyString`.

6. Klikněte na tlačítko **OK**.

     Vlastnost **Custom Attributes** nyní zobrazuje atribut v následujícím formátu:

     `[` *AttributeName* `(` *ParameterName* `=` *typ* `)]`

## <a name="see-also"></a>Viz také:

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)