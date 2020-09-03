---
title: Element ButtonText | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739903"
---
# <a name="buttontext-element"></a>Element ButtonText
Toto pole umožňuje určit text, který se zobrazí v různých nabídkách. Ve výchozím nastavení se `ButtonText` prvek zobrazuje v řadičích nabídek. `ButtonText`Element se také stal výchozím nastavením, pokud jsou ostatní textová pole prázdná. `ButtonText`Element nemůže být prázdný, i když jsou uvedena další textová pole.

## <a name="syntax"></a>Syntax

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy
 Žádné

### <a name="child-elements"></a>Podřízené prvky
 Žádné

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Strings – element](../extensibility/strings-element.md)|Seskupuje textové prvky, například `ButtonText` a `CommandName` .|

## <a name="text-value"></a>Textová hodnota
 Textová hodnota `ButtonText` elementu poskytuje text, který je zobrazen pro položky nabídky, Combos a další prvky uživatelského rozhraní (UI), které mají viditelný text.

## <a name="see-also"></a>Viz také
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
