---
title: Element ButtonText | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef22471d20df5582fec96c8a685029a1d475a4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184568"
---
# <a name="buttontext-element"></a>ButtonText – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto pole umožňuje určit text, který se zobrazí v různých nabídkách. Ve výchozím nastavení se `ButtonText` prvek zobrazuje v řadičích nabídek. `ButtonText`Element se také stal výchozím nastavením, pokud jsou ostatní textová pole prázdná. `ButtonText`Element nemůže být prázdný, i když jsou uvedena další textová pole.  
  
## <a name="syntax"></a>Syntax  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Strings – element](../extensibility/strings-element.md)|Seskupuje textové prvky, například `ButtonText` a `CommandName` .|  
  
## <a name="text-value"></a>Textová hodnota  
 Textová hodnota `ButtonText` elementu poskytuje text, který je zobrazen pro položky nabídky, Combos a další prvky uživatelského rozhraní (UI), které mají viditelný text.  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
