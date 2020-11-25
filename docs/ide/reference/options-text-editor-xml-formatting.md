---
title: Možnosti, textový editor, XML, formátování
description: Naučte se, jak používat stránku formátování v oddílu XML k určení způsobu formátování prvků a atributů v dokumentech XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9aac9420d084c64a4bd5d9199f6a7ca96b8c4281
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040508"
---
# <a name="options-text-editor-xml-formatting"></a>Možnosti, textový editor, XML, formátování

Stránka možnosti **formátování** slouží k určení způsobu formátování prvků a atributů v dokumentech XML. Chcete-li získat přístup k možnostem formátování XML, zvolte možnost **nástroje**  >  **Options**  >  **textový editor**  >  **XML** a pak zvolte možnost **formátování**.

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

Pokus o přeformátování smíšeného obsahu s výjimkou případů, kdy se obsah nachází v `xml:space="preserve"` oboru. Toto nastavení je výchozí.

Pokud element obsahuje kombinaci textu a značky, obsah se považuje za smíšený obsah. Následuje příklad prvku se smíšeným obsahem.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Viz také

- [Možnosti XML – různé](options-text-editor-xml-miscellaneous.md)
- [Nástroje XML v sadě Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
