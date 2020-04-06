---
title: Element UsedCommand | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698827"
---
# <a name="usedcommand-element"></a>UsedCommand – element
Povolí vspackage přístup k příkazu, který je definován v jiném souboru .vsct. Například pokud váš VSPackage používá standardní **příkaz Kopírovat,** který je definován [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prostředí, můžete přidat příkaz do nabídky nebo panelu nástrojů bez jeho opětovné implementace.

## <a name="syntax"></a>Syntaxe

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|Identifikátor guid|Povinná hodnota. Identifikátor GUID dvojice ID identifikátoru GUID, který identifikuje příkaz.|
|id|Povinná hodnota. ID dvojice ID IDENTIFIKÁTORGUI, která identifikuje příkaz.|
|Podmínka|Nepovinný parametr. Viz [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Podřízené elementy

|Element|Popis|
|-------------|-----------------|
|Žádný||

### <a name="parent-elements"></a>Nadřazené elementy

|Element|Popis|
|-------------|-----------------|
|[UsedCommands – element](../extensibility/usedcommands-element.md)|Skupiny UsedCommand prvky a další UsedCommands seskupení.|

## <a name="remarks"></a>Poznámky
 Přidáním příkazu `<UsedCommands>` k prvku, VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] informuje prostředí, že VSPackage vyžaduje příkaz. Měli byste `<UsedCommand>` přidat prvek pro všechny příkazy, které váš balíček vyžaduje, které nemusí být zahrnuty ve všech verzích a konfiguracích sady Visual Studio. Pokud například balíček volá příkaz, který je specifický pro visual c++, nebude příkaz k `<UsedCommand>` dispozici uživatelům aplikace Visual Web Developer, pokud nezahrnete prvek příkazu.

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
