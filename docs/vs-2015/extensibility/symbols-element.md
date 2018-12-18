---
title: Symboly Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b9bccb3874d5b85a8a69288e2bf44adb14b5b3f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783243"
---
# <a name="symbols-element"></a>Symbols – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje identifikátory GUID a ID, které se používá jinými elementy VSCT. Pro nespravovaný kód, tyto informace obvykle pocházejí z soubory hlaviček, které jsou určeny [Extern – Element](../extensibility/extern-element.md). Spravovaný kód používá podřízených elementů elementu symboly, který chcete definovat tyto informace.  
  
 Pokud vytvoříte souboru .vsct z existujícího souboru .cto, symboly budou generovány jako podřízené objekty daného elementu symboly. Další informace najdete v tématu [postupy: vytvoření. Vsct soubor z existující. Technologický ředitel souboru](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 Element symboly neměly by být zaměňovány s [definovat Element](../extensibility/define-element.md), která definuje dvojice název hodnota pro použití preprocesorem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Žádné||  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Guidsymbol –|Definuje symbol identifikátor GUID. Guidsymbol – má dvě povinné atributy: název a hodnotu. Název je název symbolu a hodnota je hodnota GUID jako řetězec.<br /><br /> Příklad:\<guidsymbol – název = hodnota "guidVsPackage1Pkg" = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|  
|Idsymbol –|Definuje symbol. Idsymbol – má dvě povinné atributy: název a hodnotu. Název je název symbolu a hodnota je hodnota symbolu jako řetězec.<br /><br /> Příklad:\<idsymbol – název = hodnota "MyMenuGroup" = "0x1020" / >|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[CommandTable – element](../extensibility/commandtable-element.md)|Kořenový element souboru .vsct|  
  
## <a name="example"></a>Příklad  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

