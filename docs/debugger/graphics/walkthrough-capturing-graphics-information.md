---
title: 'Návod: zachycení informací grafiky | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aab86d42cd158ad64ebb16497b8d2d9f5a7002df
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734730"
---
# <a name="walkthrough-capturing-graphics-information"></a>Návod: Zaznamenání grafických informací
Tento návod ukazuje, jak použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnostika grafiky k ručnímu zachycení informací grafiky z aplikace Direct3D.

 Tento návod ilustruje tyto úlohy:

- Zapojování Diagnostika grafiky do vaší aplikace

- Zachycení informací grafiky

## <a name="capturing-graphics-information"></a>Zachycení informací grafiky
 Chcete-li použít nástroje Diagnostika grafiky, musíte nejprve zachytit informace o grafice, na kterých se spoléhá. Pokud chcete povolit Capture, pomocí příkazu **Spustit diagnostiku** zapojte Diagnostika grafiky do vaší aplikace při spuštění.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Povolení zachycení informací grafiky po načtení projektu nebo řešení

1. V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtěte projekt nebo soubor řešení pro aplikaci, ze které chcete zachytit informace grafiky.

2. Na panelu nástrojů Diagnostika grafiky vyberte **Spustit diagnostiku**.

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Povolení zachycení informací grafiky bez načtení projektu nebo řešení

1. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**. Zobrazí se dialogové okno **Otevřít projekt** .

2. Místo souboru projektu nebo řešení určete spustitelný soubor pro aplikaci, ze které chcete zachytit informace grafiky, a pak zvolte **otevřít**.

3. Na panelu nabídek vyberte možnost **ladění**, **Grafika**, **Spustit diagnostiku**.

   Po spuštění aplikace a při vykreslování snímků můžete zachytit informace grafiky.

#### <a name="to-capture-graphics-information"></a>Zachycení informací grafiky

- Na panelu nástrojů Diagnostika grafiky klikněte na tlačítko **zachytit** . ![Ikona tlačítka pro zachycení grafiky](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   -nebo-

   Pokaždé, když máte aplikaci aktivní, stiskněte **tiskovou obrazovku**.

  Pokaždé, když zachytíte informace o snímku, Diagnostika grafiky zaznamenává události Direct3D a související stav a přidává tato data do protokolu grafiky. Pro každou relaci Diagnostika grafiky se vytvoří nový protokol grafiky. Informace o grafických protokolech najdete v tématu [Přehled](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="next-steps"></a>Další kroky
 Tento návod ukázal, jak ručně zachytit informace o grafice. Jako další krok zvažte tuto možnost:

- Naučte se analyzovat informace o zachycené grafice pomocí nástrojů Diagnostika grafiky. Další informace najdete v tématu [Přehled](overview-of-visual-studio-graphics-diagnostics.md).

## <a name="see-also"></a>Viz také:
- [Zaznamenání grafických informací](capturing-graphics-information.md)