---
title: Element UsedCommand | Microsoft Docs
description: Element UsedCommand umožňuje VSPackage získat přístup k příkazu, který je definován v jiném souboru. vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 30ff89cba5dbc1e54afaf51fb659e07c29e53009
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060221"
---
# <a name="usedcommand-element"></a>UsedCommand – element
Umožňuje VSPackage získat přístup k příkazu, který je definován v jiném souboru. vsct. Pokud například vaše VSPackage používá příkaz standardního **kopírování** , který je definován [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prostředím, můžete příkaz Přidat do nabídky nebo panelu nástrojů, aniž byste ho znovu implementovali.

## <a name="syntax"></a>Syntax

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|guid|Povinná hodnota. Identifikátor GUID páru identifikátorů GUID, který identifikuje příkaz|
|id|Povinná hodnota. ID páru identifikátorů GUID, který identifikuje příkaz|
|Podmínka|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené elementy

|Element|Description|
|-------------|-----------------|
|Žádná||

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[UsedCommands – element](../extensibility/usedcommands-element.md)|Seskupí prvky UsedCommand a další skupiny UsedCommands.|

## <a name="remarks"></a>Poznámky
 Přidáním příkazu do `<UsedCommands>` prvku VSPackage informuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prostředí, které VSPackage vyžaduje příkaz. Měli byste přidat `<UsedCommand>` element pro libovolný příkaz, který váš balíček vyžaduje, aby se nezahrnuly do všech verzí a konfigurací sady Visual Studio. Například pokud váš balíček volá příkaz, který je specifický pro Visual C++, nebude příkaz uživatelům aplikace Visual Web Developer k dispozici, Pokud nezahrnete `<UsedCommand>` prvek pro příkaz.

## <a name="example"></a>Příklad

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Viz také
- [UsedCommands – element](../extensibility/usedcommands-element.md)
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
