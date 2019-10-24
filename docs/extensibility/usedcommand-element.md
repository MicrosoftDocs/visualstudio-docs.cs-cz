---
title: Element UsedCommand | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718776"
---
# <a name="usedcommand-element"></a>UsedCommand – element
Umožňuje VSPackage získat přístup k příkazu, který je definován v jiném souboru. vsct. Pokud například vaše VSPackage používá příkaz standardního **kopírování** , který je definován [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell, můžete příkaz Přidat do nabídky nebo panelu nástrojů, aniž byste ho znovu implementovali.

## <a name="syntax"></a>Syntaxe

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Hlavních|Požadováno. Identifikátor GUID páru identifikátorů GUID, který identifikuje příkaz|
|id|Požadováno. ID páru identifikátorů GUID, který identifikuje příkaz|
|Podmínka|Volitelné. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Popis|
|-------------|-----------------|
|Žádné||

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[UsedCommands – element](../extensibility/usedcommands-element.md)|Seskupí prvky UsedCommand a další skupiny UsedCommands.|

## <a name="remarks"></a>Poznámky
 Přidáním příkazu do prvku `<UsedCommands>`, VSPackage informuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prostředí, které VSPackage vyžaduje příkaz. Měli byste přidat `<UsedCommand>` element pro všechny příkazy, které váš balíček vyžaduje, aby se nezahrnuly do všech verzí a konfigurací sady Visual Studio. Například pokud váš balíček volá příkaz, který je specifický pro vizuál C++, příkaz nebude dostupný uživatelům aplikace Visual Web Developer, Pokud nezahrnete `<UsedCommand>` element pro příkaz.

## <a name="example"></a>Příklad

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Viz také:
- [UsedCommands – element](../extensibility/usedcommands-element.md)
- [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)