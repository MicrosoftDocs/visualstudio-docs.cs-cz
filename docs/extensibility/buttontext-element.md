---
title: Element ButtonText | Microsoft Docs
description: Element ButtonText umožňuje určit text, který se zobrazí v různých nabídkách. Element ButtonText nemůže být prázdný ani v případě, že jsou zadána jiná textová pole.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b03b5fce58795488f6c379fcf93e5f7fea074e13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927168"
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
