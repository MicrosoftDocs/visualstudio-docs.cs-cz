---
title: Prvek skupiny | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26479257511d74f122dd4064330f5b6a1e8dadd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711235"
---
# <a name="group-element"></a>Prvek skupiny
Definuje skupinu příkazů VSPackage.

## <a name="syntax"></a>Syntaxe

```xml
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">
  <Parent>... </Parent>
</Group>
```

## <a name="attributes-and-elements"></a>Atributy a prvky
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID.|
|id|Povinná hodnota. ID identifikátoru příkazu GUID/ID.|
|Prioritou|Nepovinný parametr. Číselná hodnota, která určuje prioritu.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené prvky

|Element|Popis|
|-------------|-----------------|
|Nadřazený|Nepovinný parametr. Nadřazený prvek tlačítka.|
|Poznámka|Volitelný komentář.|

### <a name="parent-elements"></a>Nadřazené prvky

|Element|Popis|
|-------------|-----------------|
|[Prvek Skupiny](../extensibility/groups-element.md)|Obsahuje položky, které definují skupiny příkazů VSPackage.|

## <a name="example"></a>Příklad

```xml
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
</Group>
```

## <a name="see-also"></a>Viz také
- [Soubory příkazů sady Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
