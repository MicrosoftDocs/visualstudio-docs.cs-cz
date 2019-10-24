---
title: 'Postupy: zobrazení informací o trasování WPF | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82c3f193c32b4e6a67bb0fe5540aa9d0020e77ea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733471"
---
# <a name="how-to-display-wpf-trace-information"></a>Postupy: Zobrazení informací trasování grafického subsystému WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] může přijímat informace o trasování ladění z aplikací WPF a zobrazovat tyto informace v okně **výstup** . Chcete-li zobrazit informace o trasování ladění, musí být povoleno trasování WPF.

 Můžete povolit trasování WPF v souboru App. config nebo programově pomocí třídy <xref:System.Diagnostics.PresentationTraceSources>. Jednodušší způsob, jak povolit trasování WPF, je pomocí okna **Možnosti** . Trasování WPF pro webové aplikace není podporováno.

### <a name="to-enable-or-customize-wpf-trace-information"></a>Povolení nebo přizpůsobení trasovacích informací WPF

1. V nabídce **nástroje** vyberte možnost **Možnosti**.

2. V dialogovém okně **Možnosti** v levém poli otevřete uzel **ladění** .

3. V části **ladění**klikněte na **okno výstup**.

4. V části **Obecné nastavení výstupu**vyberte možnost **všechny výstupy ladění**.

5. V poli na pravé straně vyhledejte **nastavení trasování WPF**.

6. Otevřete uzel **nastavení trasování WPF** .

7. V části **nastavení trasování WPF**klikněte na kategorii nastavení, které chcete povolit (například **datová vazba**).

     Ovládací prvek rozevírací seznam se zobrazí ve sloupci nastavení vedle **datové vazby** nebo libovolné kategorie, na kterou jste klikli.

8. Klikněte na rozevírací seznam a vyberte typ trasovacích informací, které chcete zobrazit: **vše**, **kritické**, **Chyba**, **Upozornění**, **informace**, **podrobný**nebo **ActivityTracing**.

     **Kritická** umožňuje trasování pouze kritických událostí.

     **Chyba** umožňuje sledovat kritické události a chybové události.

     **Upozornění** umožňuje sledovat kritické, chybové a varovné události.

     **Informace** umožňují sledovat kritické události, chyby, upozornění a informace.

     **Verbose** umožňuje sledovat kritické události, chyby, varování, informace a podrobné události.

     **ActivityTracing** umožňuje trasování událostí zastavení, spuštění, pozastavení, přenosu a obnovení.

     Další informace o tom, jak tyto úrovně trasovacích informací znamenají, najdete v tématu <xref:System.Diagnostics.SourceLevels>.

9. Klikněte na tlačítko **OK**.

### <a name="to-disable-wpf-trace-information"></a>Zakázání informací o trasování WPF

1. V nabídce **nástroje** vyberte možnost **Možnosti**.

2. V dialogovém okně **Možnosti** v levém poli otevřete uzel **ladění** .

3. V části **ladění**klikněte na **okno výstup**.

4. V poli na pravé straně vyhledejte **nastavení trasování WPF**.

5. Otevřete uzel **nastavení trasování WPF** .

6. V části **nastavení trasování WPF**klikněte na kategorii nastavení, které chcete povolit (například **datová vazba**).

     Ovládací prvek rozevírací seznam se zobrazí ve sloupci nastavení vedle **datové vazby** nebo libovolné kategorie, na kterou jste klikli.

7. Klikněte na rozevírací seznam a vyberte **vypnuto**.

8. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:
- [Ladění WPF](../debugger/debugging-wpf.md)