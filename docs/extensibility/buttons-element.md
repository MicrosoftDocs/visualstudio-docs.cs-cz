---
title: Buttons – Element | Microsoft Docs
description: Tlačítka seskupuje prvky tlačítka, které reprezentují jednotlivé příkazy. Tento článek obsahuje příklad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2952f9f6747e52604e9f24cd173ab07f8d5a4756
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900795"
---
# <a name="buttons-element"></a>Buttons – Element
Prvky [tlačítka](../extensibility/button-element.md) skupiny, které reprezentují jednotlivé příkazy.

## <a name="syntax"></a>Syntax

```
<Buttons>
  <Button>... </Button>
  <Button>... </Button>
</Buttons>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Podmínka|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Buttons – Element](../extensibility/buttons-element.md)|Prvky tlačítka skupiny|
|[Element Button](../extensibility/button-element.md)|Definuje příkaz, se kterým může uživatel pracovat.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Command – element](../extensibility/commands-element.md)|Představuje kolekci příkazů na panelu nástrojů VSPackage.|

## <a name="example"></a>Příklad

```
<Buttons>
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>
    <Strings>
      <ButtonText>C# Command Sample</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

## <a name="see-also"></a>Viz také
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
