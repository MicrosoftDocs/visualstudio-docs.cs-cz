---
title: Příkazy – | Microsoft Docs
description: 'Element Commands představuje kolekci příkazů na panelu nástrojů VSPackage a může mít tyto části: nabídky, skupiny, tlačítka, komba a rastrové obrázky.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4c7b058acdd634079d0ca60dddb9f80e0e26ff0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901867"
---
# <a name="commands-element"></a>Commands – element
Představuje kolekci příkazů na panelu nástrojů VSPackage. Kolekce může mít až pět pododdílů, a to takto: nabídky, skupiny, tlačítka, seznam a rastrové obrázky.

 Každý podřízený prvek dílčího oddílu, například , je identifikován jedinečným ID příkazu, který je \<Menu> párem identifikátorů GUID a číselných identifikátorů. Identifikátor GUID identifikuje "sadu příkazů" a slouží k seskupení logicky souvisejících příkazů. Balíček VSPackage by měl definovat vlastní sadu příkazů, aby nedocházelo ke kolizím s ID příkazů definovanými jinými balíčky VSPackage.

## <a name="syntax"></a>Syntax

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|package|Identifikátor GUID, který identifikuje balíček VSPackage, který poskytuje příkazy.<br /><br /> Například package="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Menus – element](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje balíček VSPackage.|
|[Groups – element](../extensibility/groups-element.md)|Obsahuje položky, které definují skupiny příkazů v balíčky VSPackage.|
|[Buttons – element](../extensibility/buttons-element.md)|Seskupí prvky Tlačítka.|
|[Bitmaps – element](../extensibility/bitmaps-element.md)|Seskupí elementy bitmapy.|
|[Combos – element](../extensibility/combos-element.md)|Seskupí prvky se seznamem.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[CommandTable – element](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy, které balíček VSPackage poskytuje integrovanému vývojovému prostředí (IDE). Možné prvky jsou položky nabídky, nabídky, panely nástrojů a pole se seznamem.|

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak použít [element Commands.](../extensibility/commands-element.md)

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Viz také
- [Jak balíčky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
