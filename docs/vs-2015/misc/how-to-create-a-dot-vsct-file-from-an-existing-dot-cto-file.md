---
title: 'Postupy: vytvoření. Vsct soubor z existující. Soubor technologický ředitel | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: 82cf711d33b3b3ca5150378e7111a2a21c8c03cf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49235739"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Postupy: vytvoření. Vsct soubor z existující. Soubor technický ředitel
Můžete vytvořit souboru .vsct založený na formátu XML z existujícího .cto binárního souboru. To umožňuje využít výhod nového příkazu formát tabulky kompilátoru. Tento proces funguje i v případě, že soubor .cto byl zkompilován ze souboru .ctc. Můžete upravovat a kompilovat souboru .vsct do jiného souboru .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Vytvoření souboru .vsct ze souboru .cto  
  
1.  Získání kopií .cto souboru a jeho odpovídající soubor .ctsym.  
  
2.  Soubory umístíte do stejného adresáře jako vsct.exe kompilátoru.  
  
3.  V aplikaci Visual Studio příkazovém řádku přejděte do adresáře, který obsahuje soubory .cto a .ctsym.  
  
4.  Typ **vsct.exe** _ctofilename_**.cto** _vsctfilename_**.vsct -S**  _symfilename_**.ctsym**.  
  
     `ctofilename` je název souboru .cto `vsctfilename` je název souboru vsct, kterou chcete vytvořit, a `symfilename` je název souboru .ctsym.  
  
     Tento proces vytvoří nový .vsct příkaz tabulky kompilátoru soubor XML. Můžete upravovat a kompilovat soubor s vsct.exe, kompilátor vsct stejně jako jakýkoli jiný soubor .vsct.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření. Soubor Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)