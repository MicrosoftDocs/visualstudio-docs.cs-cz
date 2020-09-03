---
title: Metadata známé položky nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bb2e53102221194dc829df162c44bbf04378b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154085"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadata známé položky nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Následující tabulka popisuje metadata přiřazená každé položce při vytvoření. V každém příkladu byla následující deklarace položky použita k zahrnutí souboru `C:\MyProject\Source\Program.cs` do projektu.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Metadata položky|Popis|  
|-------------------|-----------------|  
|% (FullPath)|Obsahuje úplnou cestu položky. Příklad:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Obsahuje kořenový adresář položky. Příklad:<br /><br /> `C:\`|  
|% (Název souboru)|Obsahuje název souboru položky bez přípony. Příklad:<br /><br /> `Program`|  
|% (Rozšíření)|Obsahuje příponu názvu souboru položky. Příklad:<br /><br /> `.cs`|  
|%(RelativeDir)|Obsahuje cestu zadanou v `Include` atributu, až po konečné zpětné lomítko ( \\ ). Příklad:<br /><br /> `Source\`|  
|% (Adresář)|Obsahuje adresář položky bez kořenového adresáře. Příklad:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Pokud `Include` atribut obsahuje zástupný znak \* \* , tato metadata určují část cesty, která nahrazuje zástupný znak. Další informace o zástupných znacích najdete v tématu [Postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Pokud složka *C:\MySolution\MyProject\Source \\ * obsahuje soubor program.cs a soubor projektu obsahuje tuto položku:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> hodnota by pak byla `%(MyItem.RecursiveDir)` * \\ MySolution\MyProject\Source*.|  
|% (Identita)|Položka zadaná v `Include` atributu.. Příklad:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Obsahuje časové razítko od poslední změny položky. Příklad:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Obsahuje časové razítko od okamžiku, kdy byla položka vytvořena. Příklad:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Obsahuje časové razítko od posledního otevření položky.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Viz také  
 [Položek](../msbuild/msbuild-items.md)   
 [Dávkování](../msbuild/msbuild-batching.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
