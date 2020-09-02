---
title: Podmíněné atributy schématu XML VSCT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422146"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Podmíněné atributy XML schématu VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podmíněné atributy mohou být aplikovány na všechny seznamy a položky. Logické operátory a rozšiřovací výrazy se vyhodnotí jako true nebo false. Pokud je nastaveno na true, je přidružený seznam nebo položka součástí výsledného výstupu.  
  
 Rozšíření tokenů se dají testovat u jiných rozšíření tokenů nebo konstant. Funkce definovaná () slouží k otestování, zda byl zadán konkrétní název, i když nemá žádnou hodnotu.  
  
 Při použití atributu Condition na seznam se podmínka použije na všechny podřízené prvky v seznamu. Pokud podřízený element sám obsahuje atribut podmínky, pak je jeho podmínka kombinována s nadřazeným výrazem operací a.  
  
 Hodnoty 1, 1 a true se vyhodnotí jako true a 0, 0 a false se vyhodnotí jako false.  
  
## <a name="operators"></a>Operátory  
 K vyhodnocení podmíněných výrazů lze použít následující operátory.  
  
|Operátor|Definice|  
|--------------|----------------|  
|(,)|Seskupování|  
|!|Logický operátor not|  
|\<, >, \<=, >=, ==, !=|Relační a rovnost|  
|a|Logická hodnota|  
|nebo|Logická hodnota|  
  
## <a name="examples"></a>Příklady  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
