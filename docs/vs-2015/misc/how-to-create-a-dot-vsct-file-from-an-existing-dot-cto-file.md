---
title: 'Postupy: vytvoření. Soubor vsct ze stávajícího souboru. Soubor technický ředitel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 83608d768940158dcdab427a557577677e56f7c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822435"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Postupy: vytvoření. Soubor vsct ze stávajícího souboru. Soubor technický ředitel
Soubor. vsct založený na jazyce XML můžete vytvořit z existujícího binárního souboru. technický ředitel. Díky tomu je možné využít nové formáty kompilátoru příkazových tabulek. Tento proces funguje i v případě, že soubor. technický ředitel byl zkompilován ze souboru. ctc. Soubor. vsct můžete upravit a zkompilovat do jiného souboru. technický ředitel.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Vytvoření souboru. vsct ze souboru. technický ředitel  
  
1. Získejte kopie souboru. technický ředitel a odpovídajícího souboru. ctsym.  
  
2. Soubory umístěte do stejného adresáře jako vsct.exe kompilátor.  
  
3. V příkazovém řádku sady Visual Studio přejdete do adresáře, který obsahuje soubory. technický ředitel a. ctsym.  
  
4. Zadejte **vsct.exe** _ctofilename_**. technický ředitel** _vsctfilename_**. vsct-S**_symfilename_.**ctsym**.  
  
     `ctofilename` je název souboru. technický ředitel, `vsctfilename` je název souboru vsct, který chcete vytvořit, a `symfilename` je název souboru. ctsym.  
  
     Tento proces vytvoří nový soubor kompilátoru tabulky příkazů XML. vsct. Soubor můžete upravit a zkompilovat pomocí vsct.exe, kompilátoru VSCT, stejně jako jakýkoli jiný soubor. vsct.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření. Soubor vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)