---
title: 'Postupy: vytvoření. Vsct soubor z existující. Soubor CTC | Dokumentace Microsoftu'
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
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: e159fea34dc395ce2d7bded813f2d8feaa453006
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303482"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Postupy: vytvoření. Vsct soubor z existující. Soubor CTC
Můžete vytvořit souboru .vsct založený na formátu XML z existujícího souboru zdrojové tabulky .ctc příkazu. Díky tomu mohou využít výhod nového založený na formátu XML [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] formátu kompilátoru příkaz tabulky (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Vytvoření souboru .vsct ze souboru .ctc  
  
1.  Získejte kopii souboru jazyka Perl.  
  
2.  Získejte kopii souboru skriptu jazyka Perl ConvertCTCToVSCT.pl, obvykle nachází v  *\<Visual Studio SDK instalační_cesta >* \VisualStudioIntegration\Tools\bin složky.  
  
3.  Získejte kopii souboru .ctc zdrojového souboru, který chcete převést.  
  
4.  Soubory umístíte do stejného adresáře.  
  
5.  V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna příkazového řádku, přejděte do adresáře.  
  
6.  Typ  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     kde je název souboru .ctc PkgCmd.ctc a PkgCmd.vsct je název souboru .vsct, kterou chcete vytvořit.  
  
     Tím se vytvoří nový .vsct XML příkaz tabulky zdrojový soubor. Stejně jako jakýkoli jiný soubor .vsct, můžete pomocí Vsct.exe, kompilátor VSCT Zkompilujte soubor.  
  
    > [!NOTE]
    >  Přeformátování komentáře XML, lze vylepšit čitelnost souboru .vsct.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření. Soubor Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)