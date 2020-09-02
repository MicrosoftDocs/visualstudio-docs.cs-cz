---
title: 'Postupy: vytvoření. Soubor vsct ze stávajícího souboru. Soubor CTC | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796909"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Postupy: vytvoření. Soubor vsct ze stávajícího souboru. Soubor CTC
Soubor. vsct založený na jazyce XML můžete vytvořit z existující tabulky příkazů. ctc zdrojového souboru. Díky tomu můžete využít nové [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] formáty kompilátoru příkazového řádku založeného na jazyce XML (vsct).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Vytvoření souboru. vsct ze souboru. ctc  
  
1. Získá kopii jazyka Perl.  
  
2. Získejte kopii skriptu Perl ConvertCTCToVSCT.pl, která se obvykle nachází ve *\<Visual Studio SDK installation path>* složce \VisualStudioIntegration\Tools\bin.  
  
3. Získejte kopii zdrojového souboru. CTC, který chcete převést.  
  
4. Soubory umístěte do stejného adresáře.  
  
5. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okně příkazového řádku přejděte do adresáře.  
  
6. Typ  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     kde PkgCmd. ctc je název souboru. CTC a PkgCmd. vsct je název souboru. vsct, který chcete vytvořit.  
  
     Tím se vytvoří nový zdrojový soubor tabulky příkazů XML. vsct. Soubor můžete zkompilovat pomocí Vsct.exe, kompilátoru VSCT, stejně jako jakýkoli jiný soubor. vsct.  
  
    > [!NOTE]
    > Můžete zlepšit čitelnost souboru. vsct přeformátováním komentářů XML.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření. Soubor vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)