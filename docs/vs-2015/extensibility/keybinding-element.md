---
title: Element vazby elementu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180332"
---
# <a name="keybinding-element"></a>KeyBinding – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element vazby klíčů určuje klávesové zkratky pro příkazy.  
  
 K příkazům můžou být přidruženy obě vazby Single i Dual Key. Příkladem vazby s jedním klíčem je CTRL + S pro příkaz **Save** . Pro aktivaci příkazu vyžadují vazby Dual Key dvě následující kombinace kláves. Příkladem vazby s duálním klíčem je CTRL + K, CTRL + K nastavení záložky.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|guid|Povinná hodnota.|  
|id|Povinná hodnota.|  
|editor|Povinná hodnota. Identifikátor GUID editoru určuje kontext úprav, pro který bude tato klávesová zkratka aktivní. Hodnota oboru globálních vazeb je "guidVSStd97".|  
|key1|Povinná hodnota. Platné hodnoty zahrnují všechny alfanumerické znaky typable a také dvoumístné hexadecimální hodnoty předcházejí 0x a VK_constants.|  
|mod1|Nepovinný parametr. Libovolná kombinace CTRL, ALT a SHIFT oddělené mezerou.|  
|key2|Nepovinný parametr. Platné hodnoty zahrnují všechny alfanumerické znaky typable a také dvoumístné hexadecimální hodnoty předcházejí 0x a VK_constants.|  
|mod2|Nepovinný parametr. Libovolná kombinace CTRL, ALT a SHIFT oddělené mezerou.|  
|emulátor|Nepovinný parametr.|  
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|Nadřazený||  
|Poznámka||  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[KeyBindings – element](../extensibility/keybindings-element.md)|Seskupuje prvky vazby klíčů a další seskupení klíčů.|  
  
## <a name="example"></a>Příklad  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Viz také  
 [Element Bindings elementu](../extensibility/keybindings-element.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
