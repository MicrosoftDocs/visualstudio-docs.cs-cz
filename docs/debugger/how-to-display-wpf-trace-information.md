---
title: 'Postupy: zobrazení informací trasování grafického subsystému WPF | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99fc861c627a094f9f5e4e67a6b034ecdd407688
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476221"
---
# <a name="how-to-display-wpf-trace-information"></a>Postupy: Zobrazení informací trasování grafického subsystému WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] může přijímat informace o trasování ladění z grafického subsystému WPF aplikací a zobrazit tyto informace v **výstup** okno. Chcete-li zobrazit informace o trasování ladění, musí být povolena trasování grafického subsystému WPF.  
  
 Můžete povolit trasování grafického subsystému WPF v souboru App.Config nebo programově pomocí <xref:System.Diagnostics.PresentationTraceSources> třídy. Snadný způsob, jak povolit trasování grafického subsystému WPF je pomocí **možnosti** okno. WPF trasování pro webové aplikace není podporována.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Pokud chcete povolit nebo přizpůsobení informací trasování grafického subsystému WPF  
  
1.  Na **nástroje** nabídce vyberte možnost **možnosti**.  
  
2.  V **možnosti** otevřete dialogové okno, v rozevíracím seznamu na levé straně **ladění** uzlu.  
  
3.  V části **ladění**, klikněte na tlačítko **výstup – okno**.  
  
4.  V části **obecné nastavení výstupní**, vyberte **všechny výstup ladění**.  
  
5.  V dialogovém okně na pravé straně vyhledejte **nastavení trasování grafického subsystému WPF**.  
  
6.  Otevřete **nastavení trasování grafického subsystému WPF** uzlu.  
  
7.  V části **nastavení trasování grafického subsystému WPF**, klikněte na kategorii nastavení, které chcete povolit (například **datové vazby**).  
  
     Ovládací prvek rozevírací seznam se zobrazí ve sloupci nastavení vedle **datové vazby** nebo jakoukoli kategorie jste klikli.  
  
8.  Klikněte na rozevírací seznam a vyberte typ trasování informace, které chcete zobrazit: **všechny**, **kritický**, **chyba**, **upozornění**,  **Informace o**, **podrobné**, nebo **ActivityTracing**.  
  
     **Kritické** Zapíná trasování pouze kritické události.  
  
     **Chyba** Zapíná trasování kritické události a chyby.  
  
     **Upozornění** umožňuje trasování kritický, chyba a upozornění události.  
  
     **Informace o** umožňuje trasování událostí kritický, chyby, upozornění a informace.  
  
     **Podrobné** umožňuje trasování kritický, chyby, upozornění, informace a podrobné událostí.  
  
     **ActivityTracing** umožňuje trasování událostí zastavení, spuštění, pozastavení, přenos a obnovení.  
  
     Další informace o těchto úrovních informace trasování významu, najdete v části <xref:System.Diagnostics.SourceLevels>.  
  
9. Click **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Chcete-li zakázat informace trasování grafického subsystému WPF  
  
1.  Na **nástroje** nabídce vyberte možnost **možnosti**.  
  
2.  V **možnosti** otevřete dialogové okno, v rozevíracím seznamu na levé straně **ladění** uzlu.  
  
3.  V části **ladění**, klikněte na tlačítko **výstup – okno**.  
  
4.  V dialogovém okně na pravé straně vyhledejte **nastavení trasování grafického subsystému WPF**.  
  
5.  Otevřete **nastavení trasování grafického subsystému WPF** uzlu.  
  
6.  V části **nastavení trasování grafického subsystému WPF**, klikněte na kategorii nastavení, které chcete povolit (například **datové vazby**).  
  
     Ovládací prvek rozevírací seznam se zobrazí ve sloupci nastavení vedle **datové vazby** nebo jakoukoli kategorie jste klikli.  
  
7.  Klikněte na rozevírací seznam a vyberte **vypnout**.  
  
8.  Click **OK**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění WPF](../debugger/debugging-wpf.md)