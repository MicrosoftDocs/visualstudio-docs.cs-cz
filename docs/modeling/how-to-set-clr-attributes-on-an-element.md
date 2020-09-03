---
title: 'Postupy: Nastavování atributů CLR v elementu'
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
ms.openlocfilehash: ebda963bf1afa55fa8d7f98774c72a75d242ceef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532454"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Postupy: Nastavování atributů CLR v elementu
Vlastní atributy jsou speciální atributy, které lze přidat do doménových prvků, tvarů, spojnic a diagramů. Můžete přidat libovolný atribut, který dědí z `System.Attribute` třídy.

### <a name="to-add-a-custom-attribute"></a>Přidání vlastního atributu

1. V **Průzkumníku DSL**vyberte prvek, ke kterému chcete přidat vlastní atribut.

2. V okně **vlastnosti** vedle vlastnosti **vlastní atributy** klikněte na ikonu Procházet (**...**).

     Otevře se dialogové okno **Upravit atributy** .

3. Ve sloupci **název** klikněte na **\<add attribute>** a zadejte název svého atributu. Stiskněte ENTER.

4. Řádek pod názvem atributu obsahuje závorky. Na tomto řádku zadejte typ parametru pro atribut (například `string` ) a potom stiskněte klávesu ENTER.

5. Do sloupce **vlastnost název** zadejte vhodný název, například `MyString` .

6. Klikněte na **OK**.

     Vlastnost **Custom Attributes** nyní zobrazuje atribut v následujícím formátu:

     `[`*AttributeName* `(` *ParameterName* `=` *Typ*`)]`

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)