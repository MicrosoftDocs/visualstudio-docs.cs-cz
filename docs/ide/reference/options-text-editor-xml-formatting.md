---
title: Options, Text Editor, XML, Formatting
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568136"
---
# <a name="options-text-editor-xml-formatting"></a>Options, Text Editor, XML, Formatting

Stránka možnosti **formátování** slouží k určení způsobu formátování prvků a atributů v dokumentech XML. Chcete-li získat přístup k možnostem formátování XML, zvolte **nástroje** > **Možnosti** > **textový editor** > **XML**a pak zvolte možnost **formátování**.

## <a name="attributes"></a>Atributy

**Zachovat ruční formátování atributu**

Neměňte formát atributů. Toto nastavení je výchozí.

> [!NOTE]
> Pokud jsou atributy na více řádcích, Editor odsadí jednotlivé řádky atributů tak, aby odpovídaly odsazení nadřazeného elementu.

**Zarovnat atributy každý na samostatný řádek**

Druhý a následující atributy zarovnejte svisle tak, aby odpovídaly odsazení prvního atributu. Následující text XML je příkladem způsobu zarovnání atributů:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automaticky přeformátovat

**Při vložení ze schránky**

Přeformátuje text XML vložený ze schránky.

**Po dokončení koncové značky**

Přeformátuje prvek po dokončení koncové značky.

## <a name="mixed-content"></a>Smíšený obsah

**Formátovat smíšený obsah ve výchozím nastavení.**

Pokus o přeformátování smíšeného obsahu s výjimkou případů, kdy se obsah nachází v oboru `xml:space="preserve"`. Toto nastavení je výchozí.

Pokud element obsahuje kombinaci textu a značky, obsah se považuje za smíšený obsah. Následuje příklad prvku se smíšeným obsahem.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Viz také:

- [Možnosti XML – různé](options-text-editor-xml-miscellaneous.md)
- [Nástroje XML v aplikaci Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
