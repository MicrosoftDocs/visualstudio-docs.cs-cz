---
title: Speciální znaky pro Escape | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: beeed84db240ecf57ca18dd9aef08622f14b06fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161358"
---
# <a name="special-characters-to-escape"></a>Speciální řídicí znaky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Speciální znaky musí být uvozeny pouze v případě, že mají zvláštní význam v kontextu, ve kterém jsou používány. Například hvězdička (*) je speciální znak pouze v atributech include a Exclude definice položky nebo v volání <xref:Microsoft.Build.Tasks.CreateItem> . Ve všech ostatních případech je hvězdička považována za literální hvězdičku. Nemusíte-li v souborech projektu zacházet hvězdičkami, není to nijak poškozeno.  
  
 Použijte notaci%*XX* místo speciálního znaku, kde *XX* představuje hexadecimální hodnotu znaku ASCII. Chcete-li například použít hvězdičku (*) jako literální znak, použijte hodnotu `%2A` .  
  
 Úplný seznam speciálních znaků, které mají být uvozeny následujícím způsobem:  
  
|Znak|Popis|  
|---------------|-----------------|  
|%|Symbol procenta, který se používá k odkazování na metadata|  
|$|Znak dolaru, který se používá k odkazování na vlastnosti.|  
|@|Na znaménko, používá se pro odkazování na seznamy položek.|  
|(|Levou závorku, která se používá v seznamech|  
|)|V seznamech se použijí uzavírací závorky.|  
|`|Apostrofy (nebo osové značky), používané v podmínkách a dalších výrazech.|  
|;|Středník, oddělovač seznamu.|  
|?|Otazník, zástupný znak při popisu specifikace souboru v sekci include/Exclude položky|  
|*|Hvězdička (zástupný znak) při popisu specifikace souboru v oddílu include/Exclude položky položky.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: sekvence speciálních znaků v nástroji MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
