---
title: Volby, Textový editor, XML, Formátování
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568136"
---
# <a name="options-text-editor-xml-formatting"></a>Volby, Textový editor, XML, Formátování

Stránka **Možnosti formátování** slouží k určení způsobu formátování prvků a atributů v dokumentech XML. Chcete-li získat přístup k možnostem formátování XML, zvolte**Možnosti** >  **nástrojů** > **Textový editor** > **XML**a pak zvolte **Formátování**.

## <a name="attributes"></a>Atributy

**Zachovat ruční formátování atributů**

Nepřeformátovat atributy. Toto nastavení je výchozí.

> [!NOTE]
> Pokud jsou atributy na více řádcích, editor odsaze každý řádek atributů tak, aby odpovídal odsazení nadřazeného prvku.

**Zarovnat atributy na samostatném řádku**

Zarovnejte druhý a následující atribut svisle tak, aby odpovídaly odsazení prvního atributu. Následující text XML je příkladem toho, jak by byly atributy zarovnány:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatický přeformátování

**Při vložení ze schránky**

Přeformátovat text XML vložený ze schránky.

**Po dokončení koncové značky**

Přeformátovat prvek po dokončení koncové značky.

## <a name="mixed-content"></a>Smíšený obsah

**Ve výchozím nastavení formátujte smíšený obsah.**

Pokus o přeformátování smíšeného obsahu, s `xml:space="preserve"` výjimkou případů, kdy je obsah nalezen v oboru. Toto nastavení je výchozí.

Pokud prvek obsahuje kombinaci textu a značek, obsah se považuje za smíšený obsah. Následuje příklad prvku se smíšeným obsahem.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Viz také

- [Volby XML – různé](options-text-editor-xml-miscellaneous.md)
- [Nástroje XML v sadě Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
