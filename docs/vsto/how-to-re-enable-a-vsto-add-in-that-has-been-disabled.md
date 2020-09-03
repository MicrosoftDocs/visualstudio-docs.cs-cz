---
title: 'Postupy: opětovné povolení zakázaného doplňku VSTO'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3575e119f4da3ca3050a28243104fb4773089cf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541255"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Postupy: opětovné povolení zakázaného doplňku VSTO
  Aplikace systém Microsoft Office mohou zakázat doplňky VSTO, které se chovají neočekávaně. Pokud aplikace nenačte doplněk VSTO při pokusu o jeho ladění, může být aplikace v případě, že je váš doplněk VSTO špatně zakázaná nebo je zakázaná.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="hard-disabled-vsto-add-ins"></a>Pevně zablokované doplňky VSTO
 Pokud doplněk VSTO způsobuje neočekávané ukončení aplikace, může dojít k zablokování pevného vypnutí. Může k tomu také dojít ve vývojovém počítači, pokud ukončíte ladicí program, zatímco <xref:Microsoft.Office.Tools.AddIn.Startup> je spuštěná obslužná rutina události v doplňku VSTO.

### <a name="to-re-enable-a-vsto-add-in"></a>Opětovné povolení doplňku VSTO

1. V aplikaci klikněte na kartu **soubor** .

2. Klikněte na tlačítko **Možnosti** *ApplicationName* .

3. V podokně kategorie klikněte na **Doplňky**.

4. V podokně podrobností ověřte, že se doplněk VSTO zobrazuje v seznamu **zakázaných doplňků aplikace** .

     Sloupec **Name** Určuje název sestavení a sloupec **umístění** určuje úplnou cestu k manifestu aplikace.

5. V poli **Spravovat** klikněte na položku **Zakázané položky**a potom klikněte na tlačítko **Přejít**.

6. Vyberte doplněk VSTO a klikněte na **Povolit**.

7. Klikněte na **Zavřít**.

## <a name="soft-disabled-vsto-add-ins"></a>Obnovitelné – zakázané doplňky VSTO
 Pokud doplněk VSTO vytváří chybu, která nezpůsobí neočekávané ukončení aplikace, může dojít k tichému vypnutí. Aplikace může například softwarově zakázat doplněk VSTO, pokud vyvolá neošetřenou výjimku při <xref:Microsoft.Office.Tools.AddIn.Startup> provádění obslužné rutiny události.

> [!NOTE]
> Když znovu povolíte částečný zakázaný doplněk VSTO, aplikace se okamžitě pokusí načíst doplněk VSTO. Pokud problém, který původně způsobil aplikaci pro vypnutí doplňku VSTO, nevyřešil, aplikace znovu zakáže doplněk VSTO.

### <a name="to-re-enable-a-vsto-add-in"></a>Opětovné povolení doplňku VSTO

1. V aplikaci klikněte na kartu **soubor** .

2. Klikněte na tlačítko **Možnosti** *ApplicationName* .

3. V podokně kategorie klikněte na **Doplňky**.

4. V podokně podrobností ověřte, že se doplněk VSTO zobrazuje v seznamu **neaktivní Doplňky aplikace** .

     Sloupec **Name** Určuje název sestavení a sloupec **umístění** určuje úplnou cestu k manifestu aplikace.

5. V poli **Spravovat** klikněte na **Doplňky modelu COM**a potom klikněte na **Přejít**.

6. V dialogovém okně **Doplňky modelu COM** zaškrtněte políčko vedle zakázaného doplňku VSTO.

7. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Ladění projektů Office](../vsto/debugging-office-projects.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
