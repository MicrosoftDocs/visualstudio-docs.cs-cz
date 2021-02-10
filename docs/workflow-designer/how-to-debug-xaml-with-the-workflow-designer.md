---
title: 'Návrhář postupu provádění: ladit XAML'
description: Přečtěte si, jak jsou postupy definovány v jazyce XAML a jak ladit XAML pomocí Návrhář postupu provádění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 78141b6f3c33903603d7cbb082eca6de55ee757c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971658"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Postupy: Ladění XAML pomocí návrháře postupu provádění

Pracovní postupy jsou definovány z podmínek XAML. Reprezentace uživatelského rozhraní pracovního postupu je postavená na stromu XAML, který definuje pracovní postup. Prostředí ladění je podobné jako při ladění pracovních postupů v Návrhář postupu provádění. Například při ladění XAML fungují okna místní hodnoty, sledování a vlákna stejným způsobem jako při ladění Návrhář postupu provádění. Kromě toho zobrazení zásobníku volání během ladění XAML je spojnicové hierarchické zobrazení toku spuštění pro pracovní postup.

> [!NOTE]
> Pokud je XAML pro pracovní postup umístěn ve stejném sestavení jako aktivity, část sestavení názvů tříd nejsou zahrnuty. Bez této části názvů třídy (aktivity) nelze v době běhu načíst XAML. Nedoporučujeme definovat aktivity ve stejném oboru názvů jako hlavní projekt; v opačném případě bude po úpravě v Návrháři nutné ručně upravit kód XAML.

## <a name="to-debug-workflow-xaml"></a>Ladění kódu XAML pracovního postupu

1. Otevřete pracovní postup nebo projekt aktivity v aplikaci Visual Studio.

2. Nastavte zarážku pro aktivitu nebo aktivity, které chcete ladit, jak je popsáno v tématu [Postupy: nastavení zarážek v pracovních postupech](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Klikněte pravým tlačítkem na soubor. XAML, který obsahuje definici pracovního postupu a vyberte **Zobrazit kód**. Zobrazí se zarážka na stejném řádku jako deklarace elementu XAML aktivity, na které jste nastavili zarážku v zobrazení Návrh.

4. Vyvolejte ladicí program, jak je popsáno v tématu [ladění pracovních postupů](debugging-workflows-with-the-workflow-designer.md).

5. Když spuštění kódu dosáhne jedné z vašich zarážek, bude zvýrazněn prvek XAML přidružený k této zarážce. K přechodu na další zarážku použijte klávesu **F10** nebo **F11** .

## <a name="see-also"></a>Viz také

- [Postupy: Nastavení zarážek v pracovních postupech](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Ladění pracovních postupů](debugging-workflows-with-the-workflow-designer.md)
