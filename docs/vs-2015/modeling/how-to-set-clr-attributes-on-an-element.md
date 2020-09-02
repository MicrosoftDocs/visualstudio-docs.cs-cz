---
title: 'Postupy: nastavení atributů CLR u prvku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662542"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Postupy: Nastavování atributů CLR v elementu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
