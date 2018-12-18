---
title: 'Postupy: opětovné povolení VSTO doplňku, který byl zakázán'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c81e44b548f4d1139810780731741a489e624047
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676445"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Postupy: opětovné povolení VSTO doplňku, který byl zakázán
  Aplikace Microsoft Office můžete zakázat doplňků VSTO, které neočekávané chování. Pokud aplikace doplňku VSTO nenačte, při pokusu o ladění, aplikace může být zakázaný, pevný nebo obnovitelně zakázáno doplňku VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>Doplňky VSTO pevné zakázáno  
 Intenzivně zakázání může dojít, když doplňku VSTO způsobí, že aplikace nečekaně zavře. To může vzniknout také ve svém vývojovém počítači zastavení ladicího programu při <xref:Microsoft.Office.Tools.AddIn.Startup> provádění obslužné rutiny události v doplňku VSTO.  
  
### <a name="to-re-enable-a-vsto-add-in"></a>Opětovné povolení doplňku VSTO  
  
1.  V aplikaci, klikněte na tlačítko **souboru** kartu.  
  
2.  Klikněte na tlačítko *ApplicationName* **možnosti** tlačítko.  
  
3.  V podokně kategorie, klikněte na tlačítko **Add-ins**.  
  
4.  V podokně podrobností ověřte, že doplňku VSTO zobrazuje v **zakázané aplikace Add-ins** seznamu.  
  
     **Název** sloupci Určuje název sestavení a **umístění** sloupci Určuje úplnou cestu k manifestu aplikace.  
  
5.  V **spravovat** klikněte **zakázané položky**a potom klikněte na tlačítko **Přejít**.  
  
6.  Vyberte doplňku VSTO a klikněte na tlačítko **povolit**.  
  
7.  Klikněte na tlačítko **Zavřít**.  
  
## <a name="soft-disabled-vsto-add-ins"></a>Doplňky VSTO konfigurace soft zakázáno  
 Zakázání obnovitelně může dojít, když doplňku VSTO dojde k chybě, který nevyvolá aplikace neočekávaně zavřít. Například aplikace může být obnovitelné zakázat doplňku VSTO Pokud vyvolá neošetřenou výjimku při <xref:Microsoft.Office.Tools.AddIn.Startup> provádění obslužné rutiny události.  
  
> [!NOTE]  
>  Při opětovném povolení doplňku VSTO konfigurace soft zakázáno, aplikace se okamžitě pokusí se načíst doplňku VSTO. Pokud problém, který původně způsobilo, že aplikace obnovitelně zakázání doplňku VSTO nebyl vyřešen, aplikace bude obnovitelné doplňku VSTO znovu zakázat.  
  
### <a name="to-re-enable-a-vsto-add-in"></a>Opětovné povolení doplňku VSTO  
  
1.  V aplikaci, klikněte na tlačítko **souboru** kartu.  
  
2.  Klikněte na tlačítko *ApplicationName* **možnosti** tlačítko.  
  
3.  V podokně kategorie, klikněte na tlačítko **Add-ins**.  
  
4.  V podokně podrobností ověřte, že doplňku VSTO zobrazuje v **neaktivní aplikace Add-ins** seznamu.  
  
     **Název** sloupci Určuje název sestavení a **umístění** sloupci Určuje úplnou cestu k manifestu aplikace.  
  
5.  V **spravovat** klikněte **doplňky modelu COM**a potom klikněte na tlačítko **Přejít**.  
  
6.  V **doplňky modelu COM** dialogové okno, vyberte políčko vedle je zakázané doplňku VSTO.  
  
7.  Klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také:  
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Ladění projektů Office](../vsto/debugging-office-projects.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)  
  
  