---
title: Tlačítka oken vlastností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706177"
---
# <a name="properties-window-buttons"></a>Tlačítka okna Vlastnosti
V závislosti na vývojovém jazyce a typu produktu jsou ve výchozím nastavení na panelu nástrojů okna **Vlastnosti** zobrazena určitá tlačítka. Ve všech případech se zobrazí tlačítka **Kategorizováno**, **Abeceda**, **Vlastnosti**a **Stránky vlastností.** V jazyce Visual C# a Visual Basic se také zobrazí tlačítko **Události.** V některých projektech Visual C++ jsou zobrazeny **zprávy VC++** a tlačítka **VC Overrides.** Další tlačítka mohou být zobrazena pro jiné typy projektů. Další informace o tlačítkách v okně **Vlastnosti** naleznete v tématu [Properties Window](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementace okenních tlačítek vlastností
 Po klepnutí na tlačítko **Kategorizované** visual studio volá <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> rozhraní na objekt, který má fokus seřadit jeho vlastnosti podle kategorie. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>je implementována na objekt, `IDispatch` který je uveden v okně **Vlastnosti.**

 Existuje 11 předdefinovaných kategorií vlastností, které mají záporné hodnoty. Můžete definovat vlastní kategorie, ale doporučujeme jim přiřadit kladné hodnoty, abyste je odlišili od předdefinovaných kategorií.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> vrátí příslušnou hodnotu kategorie vlastnosti pro zadanou vlastnost. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> vrátí řetězec, který obsahuje název kategorie. Je třeba poskytnout podporu pro vlastní hodnoty kategorií, protože Visual Studio zná hodnoty kategorií standardní vlastnosti.

 Po klepnutí na tlačítko **abeced jsou** vlastnosti zobrazeny v abecedním pořadí podle názvu. Názvy jsou načteny `IDispatch` podle lokalizovaného algoritmu řazení.

 Když je otevřené okno **Vlastnosti,** tlačítko **Vlastnosti** se automaticky zobrazí jako vybrané. V jiných částech prostředí se zobrazí stejné tlačítko a klepnutím na něj zobrazíte okno **Vlastnosti.**

 Tlačítko **Stránky vlastností** `ISpecifyPropertyPages` není k dispozici, pokud není implementováno pro vybraný objekt. Stránky vlastností zobrazují vlastnosti závislé na konfiguraci, které jsou obvykle přidruženy k řešením a projektům, ale mohou být také přidruženy k položkám projektu (například v jazyce Visual C++).

> [!NOTE]
> Tlačítka panelu nástrojů nelze přidat do okna **Vlastnosti** pomocí nespravovaného kódu. Chcete-li přidat tlačítko panelu nástrojů, je nutné <xref:System.Windows.Forms.Design.PropertyTab>vytvořit spravovaný objekt, který je odvozen od aplikace .

## <a name="see-also"></a>Viz také
- [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)
