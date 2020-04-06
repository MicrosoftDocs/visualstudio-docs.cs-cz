---
title: Odkaz na schéma XML VSCT | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697903"
---
# <a name="vsct-xml-schema-reference"></a>Odkaz na schéma XML VSCT
Obsahuje tabulku prvků schématu kompilátoru tabulky příkazů s povolenými podřízenými prvky a atributy pro každý.

 Konfigurace tabulky příkazů založené na xml (.vsct) soubor definuje prvky příkazu, které VSPackage poskytuje integrované vývojové prostředí (IDE). Mezi tyto prvky patří položky nabídky, nabídky, panely nástrojů a pole se seznamem.

> [!NOTE]
> Kompilátor VSCT může spustit preprocesor v souboru .vsct. Protože se obvykle jedná o preprocesor jazyka C++, můžete definovat zahrnutí a makra, která mají stejnou syntaxi, která se používá v souborech jazyka C++. Příklady jsou uvedeny v souboru .vsct, který vytvoří průvodce **nový projekt** pro projekt VSPackage.

## <a name="optional-elements"></a>Volitelné prvky
 Některé prvky VSCT jsou volitelné. Pokud `Parent` není zadán argument, Group_Undefined:0 bude implicitní. Pokud `Icon` argument není zadán, guidOfficeIcon:msotcidNoIcon bude implicitní. Je-li definována klávesová zkratka, je emulace, která se obvykle nepoužívá, nepovinná.

 Bitmapové položky mohou být vloženy v době kompilace zadáním umístění bitmapového proužku v argumentu. `href` Bitmapový proužek je zkopírován během sloučení, nikoli extrahován ze zdrojů dll. Pokud `href` je k dispozici `usedList` argument, argument se stane volitelný a všechny sloty v rastrový proužek jsou považovány za použité.

 Všechny hodnoty GUID a ID musí být definovány pomocí symbolických názvů. Tyto názvy mohou být definovány v \<hlavičkových souborech nebo v oddílech VSCT Symbols>. Symbolické názvy musí být \<místní, zahrnuty prostřednictvím \<include> prvky nebo odkazuje Extern> prvky. Symbolický název je importován ze \<souboru záhlaví určeného v prvku Extern>, pokud se řídí jednoduchým vzorem #define SYMBOL VALUE. Hodnota může být jiný symbol, pokud byl tento symbol dříve definován. Definice identifikátorů GUID musí následovat formát OLE nebo C++. Hodnoty ID mohou být desetinné číslice nebo šestnáctkové číslice, které předchází 0x, jak je znázorněno na následujících řádcích:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 }

  Mohou být použity komentáře XML, ale nástroje grafického uživatelského rozhraní (GUI) s odezvou je mohou zahodit. Obsah \<anotace> prvky jsou zaručeny zachovány bez ohledu na formát.

## <a name="schema-hierarchy"></a>Hierarchie schématu
 Soubor .vsct obsahuje následující hlavní prvky.

- [Element CommandTable](../extensibility/commandtable-element.md)

- [Extern prvek](../extensibility/extern-element.md)

- [Zahrnout prvek](../extensibility/include-element.md)

- [Definovat prvek](../extensibility/define-element.md)

- [Element příkazy](../extensibility/commands-element.md)

- [Element CommandPlacements](../extensibility/commandplacements-element.md)

- [VisibilityConstraints prvek](../extensibility/visibilityconstraints-element.md)

- [Element KeyBindings](../extensibility/keybindings-element.md)

- [Element UsedCommands](../extensibility/usedcommands-element.md)

- [Nadřazený prvek](../extensibility/parent-element.md)

- [Prvek ikony](../extensibility/icon-element.md)

- [Řetězec, prvek](../extensibility/strings-element.md)

- [Element Příkaz Flag](../extensibility/command-flag-element.md)

- [Prvek symbolů](../extensibility/symbols-element.md)

- [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Viz také
- [Jak VSPackages přidat prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Směrování příkazů v balíčcích VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
