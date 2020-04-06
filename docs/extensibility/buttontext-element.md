---
title: Element ButtonText | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739903"
---
# <a name="buttontext-element"></a>ButtonTextový prvek
Toto pole umožňuje určit text, který se zobrazí v různých nabídkách. Ve výchozím `ButtonText` nastavení se prvek zobrazí v řadičích nabídky. Prvek `ButtonText` se také stane výchozím, pokud jsou ostatní textová pole prázdná. Prvek `ButtonText` nemůže být prázdný ani v případě, že jsou zadána ostatní textová pole.

## <a name="syntax"></a>Syntaxe

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné.

### <a name="child-elements"></a>Podřízené prvky
 Žádné.

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Strings – element](../extensibility/strings-element.md)|Seskupí `ButtonText` textové `CommandName`prvky, například a .|

## <a name="text-value"></a>Textová hodnota
 Textová hodnota `ButtonText` prvku poskytuje text, který se zobrazí pro položky nabídky, komba a další prvky uživatelského rozhraní (UI), které mají viditelný text.

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
