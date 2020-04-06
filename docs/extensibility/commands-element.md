---
title: Element příkazů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739684"
---
# <a name="commands-element"></a>Element příkazy
Představuje kolekci příkazů na panelu nástrojů VSPackage. Kolekce může mít až pět podsekcí, a to takto: nabídky, skupiny, tlačítka, komba a rastrové obrázky.

 Každý pododdíl podřízený prvek, \<například Menu>, je identifikován jedinečným ID příkazu, který je dvojicí identifikátorů GUID a číselného identifikátoru. Identifikátor GUID identifikuje "sadu příkazů" a používá se k seskupení logicky souvisejících příkazů. VSPackage by měl definovat vlastní sadu příkazů, aby se zabránilo kolizím s ID příkazu, které jsou definovány jinými Balíčky VSPackages.

## <a name="syntax"></a>Syntaxe

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Balíček|Identifikátor GUID, který identifikuje VSPackage, který poskytuje příkazy.<br /><br /> Například package="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|[Prvek nabídek](../extensibility/menus-element.md)|Definuje všechny nabídky, které implementuje VSPackage.|
|[Prvek Skupiny](../extensibility/groups-element.md)|Obsahuje položky, které definují skupiny příkazů v Balíčku VSPackage.|
|[Prvek tlačítek](../extensibility/buttons-element.md)|Seskupí prvky tlačítka.|
|[Bitmapový prvek](../extensibility/bitmaps-element.md)|Seskupí bitmapové prvky.|
|[Komba prvek](../extensibility/combos-element.md)|Skupiny Combo prvky.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definuje všechny prvky, které představují příkazy, které Poskytuje VSPackage ide. Možnými prvky jsou položky nabídky, nabídky, panely nástrojů a pole se seznamem.|

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak používat [element příkazů](../extensibility/commands-element.md).

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
- [Jak VSPackages přidat prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
