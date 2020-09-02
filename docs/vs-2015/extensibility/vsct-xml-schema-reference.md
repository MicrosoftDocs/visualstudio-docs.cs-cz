---
title: Referenční informace o schématu XML VSCT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e56de828d3b357762da98cde3b9591033c6b5d19
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805728"
---
# <a name="vsct-xml-schema-reference"></a>XML schéma VSCT – referenční informace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 [CommandTable – element](../extensibility/commandtable-element.md)  
  
 [Extern – element](../extensibility/extern-element.md)  
  
 [Include – element](../extensibility/include-element.md)  
  
 [Define – element](../extensibility/define-element.md)  
  
 [Commands – element](../extensibility/commands-element.md)  
  
 [CommandPlacements – element](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints – element](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings – element](../extensibility/keybindings-element.md)  
  
 [UsedCommands – element](../extensibility/usedcommands-element.md)  
  
 [Parent – element](../extensibility/parent-element.md)  
  
 [Icon – element](../extensibility/icon-element.md)  
  
 [Strings – element](../extensibility/strings-element.md)  
  
 [Command Flag – element](../extensibility/command-flag-element.md)  
  
 [Symbols – element](../extensibility/symbols-element.md)  
  
 [Podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Viz také  
 [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Směrování příkazů v balíčcích VSPackage](../extensibility/internals/command-routing-in-vspackages.md)
