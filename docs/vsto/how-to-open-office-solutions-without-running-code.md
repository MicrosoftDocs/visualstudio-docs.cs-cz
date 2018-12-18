---
title: 'Postupy: řešení otevřete Office bez spuštění kódu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7ced7b38a4f32d96b397e7f9eebb1d40be03ae3
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254985"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Postupy: řešení otevřete Office bez spuštění kódu
  Řešení Microsoft Office vytvořené pomocí rozšíření spravovaného kódu se spustí i v případě nastavení zabezpečení v aplikaci Office koncového uživatele je nastavena na hodnotu Vysoká. Je to proto, že zabezpečení kódu sestavení .NET je spravovaná rozhraní Microsoft .NET Framework, nikoliv společností Microsoft Office.  
  
 Existují však situace když budete chtít otevřít dokument, bez spuštění kódu. Například kód, který běží po otevření dokumentu může změnit obsah, ale chcete aktualizovat dokument vzhled před změny kódu. Nebo můžete chtít poslat dokument s určité informace v ní někdo a nechcete, aby kód ke spuštění a případně změnit obsah.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Existuje několik způsobů otevřete dokument nebo sešit, který obsahuje rozšíření spravovaného kódu bez spuštění kódu sestavení.  
  
## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Pomocí klávesy Shift obejít sestavení  
  
-   Otevřít dokumenty a sešity z **soubor** nabídky stiskněte **Shift** klíč chcete zabránit vyvolání inicializace událostí, když je otevření dokumentu Word a Excel.  
  
    > [!NOTE]  
    >  Pokud otevřete dokument nebo sešitu z **Začínáme** podokna úloh podržíte stisknutou **Shift** nepoužívat kód. Navíc podržíte stisknutou klávesu SHIFT nezabrání událostí vyvolaných po otevření dokumentu.  
  
     Tato metoda je užitečná, pokud chcete otevřít dokument měnit, aniž by kód spuštěný a nejprve změny dokumentu.  
  
## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Obejít sestavení a přejmenování nebo odebráním  
  
-   Pokud máte na počítači, kde se nachází sestavení potřebná oprávnění, můžete přejmenovat nebo odebrat sestavení, dokumentu nebo sešitu ji nemůže najít. To vede k chybě vyvolaných pokaždé, když je otevřen dokumentu systému Office.  
  
     Pokud řešení používá více uživatelů, tato metoda řešení zabraňuje spuštění pro každou z nich. To může být užitečné, pokud je zjištěn problém v kódu nebo odkazovaného serveru a chcete zastavit všechny uživatele od její provedení.  
  
## <a name="see-also"></a>Viz také:  
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifesty aplikace a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  