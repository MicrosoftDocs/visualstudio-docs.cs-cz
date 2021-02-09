---
title: Referenční informace o schématu XML VSCT | Microsoft Docs
description: Referenční články ke schématu XML VSCT popisují tabulky příkazového schématu kompilátoru s povolenými podřízenými elementy a atributy pro každý z nich.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9cc50d3914f43be0da2f992f1074dc82cf5178ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925744"
---
# <a name="vsct-xml-schema-reference"></a>Referenční dokumentace schématu VSCT XML
Poskytuje tabulku elementů příkazového schématu kompilátoru s povolenými podřízenými elementy a atributy pro každý.

 Konfigurační soubor tabulky příkazu založený na jazyce XML (. vsct) definuje prvky příkazu, které VSPackage poskytuje integrovanému vývojovému prostředí (IDE). Mezi tyto prvky patří položky nabídky, nabídky, panely nástrojů a pole se seznamem.

> [!NOTE]
> Kompilátor VSCT může spustit preprocesor v souboru. vsct. Vzhledem k tomu, že se jedná o obvykle preprocesor jazyka C++, můžete definovat zahrnutí a makra, která mají stejnou syntaxi, která se používá v souborech jazyka C++. Příklady jsou uvedeny v souboru. vsct, který průvodce **vytvořením nového projektu** vytvoří pro projekt VSPackage.

## <a name="optional-elements"></a>Volitelné prvky
 Některé elementy VSCT jsou volitelné. Pokud není `Parent` zadán argument, Group_Undefined: 0 bude předpokládaná. Pokud není `Icon` zadán argument, bude odvozeno guidOfficeIcon: msotcidNoIcon. Když je definována klávesová zkratka, emulace, která se obvykle nepoužívá, je volitelná.

 Rastrové položky mohou být vloženy v době kompilace zadáním umístění rastrového obrázku v `href` argumentu. Rastrový pruh je zkopírován během slučování místo extrakce z prostředků knihovny DLL. Pokud `href` je k dispozici argument, `usedList` argument se bude nepovinný a všechny sloty v rastrovém pruhu se považují za použité.

 Všechny hodnoty identifikátoru GUID a ID musí být definovány pomocí symbolických názvů. Tyto názvy mohou být definovány v hlavičkových souborech nebo v \<Symbols> oddílech vsct. Symbolické názvy musí být místní, zahrnuté prostřednictvím \<Include> prvků, nebo odkazovány \<Extern> elementy. Symbolický název je importován ze souboru hlaviček zadaného v \<Extern> elementu, pokud následuje jednoduchý vzor #define hodnota symbolu. Hodnota může být jiný symbol, pokud byl tento symbol dříve definován. Definice identifikátorů GUID musí následovat buď ve formátu OLE nebo C++. Hodnoty ID mohou být buď desítkové nebo šestnáctkové číslice, které jsou uvozeny 0x, jak je znázorněno na následujících řádcích:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  Je možné použít komentáře XML, ale nástroje grafického uživatelského rozhraní (GUI) s kulatým výletem je mohou zahodit. Obsah \<Annotation> prvků je zaručený udržovat bez ohledu na formát.

## <a name="schema-hierarchy"></a>Hierarchie schématu
 Soubor. vsct má následující hlavní prvky.

- [Element v příkazu](../extensibility/commandtable-element.md)

- [Extern – element](../extensibility/extern-element.md)

- [Include – element](../extensibility/include-element.md)

- [Definovat element](../extensibility/define-element.md)

- [Command – element](../extensibility/commands-element.md)

- [Element CommandPlacements](../extensibility/commandplacements-element.md)

- [Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [Element Bindings elementu](../extensibility/keybindings-element.md)

- [Element UsedCommands](../extensibility/usedcommands-element.md)

- [Nadřazený element](../extensibility/parent-element.md)

- [Element Icon](../extensibility/icon-element.md)

- [Řetězec – element](../extensibility/strings-element.md)

- [Element příznak příkazu](../extensibility/command-flag-element.md)

- [SYMBOLS – element](../extensibility/symbols-element.md)

- [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Viz také
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Směrování příkazů v VSPackage](../extensibility/internals/command-routing-in-vspackages.md)
