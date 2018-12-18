---
title: Příkazové podokno | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: be77104c4570068cbebf6c25801f600757a6ee0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850422"
---
# <a name="immediate-window"></a>Příkazové podokno
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Okamžité** okna slouží k ladění a vyhodnocení výrazů, spuštění příkazů, tisku hodnot proměnných a tak dále. Umožňuje zadat výrazy k vyhodnocování nebo provádění ve vývojovém jazyce během ladění. Pro zobrazení **okamžité** okno, otevřete projekt pro úpravy a pak zvolte **Windows** z **ladění** nabídky a vybereme **okamžité**, nebo stiskněte kombinaci kláves CTRL + ALT + I.  
  
 Můžete použít toto okno k vydání jednotlivých [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkazy. Dostupné příkazy zahrnují `EvaluateStatement`, který slouží k přiřazení hodnoty proměnné. **Okamžité** okna také podporuje technologii IntelliSense.  
  
## <a name="displaying-the-values-of-variables"></a>Zobrazení hodnot proměnných  
 Toto okno může být zvláště užitečné při ladění aplikace. Například pro kontrolu hodnoty proměnné `varA`, můžete použít [příkaz Tisk](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Otazník (?) je alias pro `Debug.Print`, takže tento příkaz lze také zapsat:  
  
```  
>? varA  
```  
  
 Obě verze tohoto příkazu vrátí hodnotu proměnné `varA`.  
  
> [!NOTE]
>  K problému [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v příkaz **okamžité** okna, je nutné před příkaz s znaménko (>) větší než. Chcete-li zadat více příkazů, přepněte **příkaz** okna.  
  
## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu pro dobu návrhu  
 Můžete použít **okamžité** okna spuštění funkce nebo podprogram v době návrhu.  
  
#### <a name="to-execute-a-function-at-design-time"></a>Provedení funkce v době návrhu  
  
1. Zkopírujte následující kód do [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] konzolové aplikace:  
  
   ```  
   Module Module1  
  
       Sub Main()  
           MyFunction(5)  
       End Sub  
  
       Function MyFunction(ByVal input as Integer) As Integer  
           Return input * 2  
       End Function  
  
   End Module  
   ```  
  
2. Na **ladění** nabídky, klikněte na tlačítko **Windows**a potom klikněte na tlačítko **okamžité**.  
  
3. Typ `?MyFunction(2)` v **okamžité** podokna a stiskněte Enter.  
  
    **Okamžité** okno spustí `MyFunction` a zobrazit `4`.  
  
   Pokud funkce nebo podprogram obsahuje zarážku, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] přeruší běh v odpovídajícím bodě. Potom můžete ladicí program windows prozkoumat stav vaší aplikace. Další informace najdete v části [návod: ladění v době návrhu](../../debugger/walkthrough-debugging-at-design-time.md).  
  
   Vyhodnocení výrazu času návrhu nelze použít v typech projektů, které vyžadují spuštění prostředí, včetně [!INCLUDE[trprVSTOshort](../../includes/trprvstoshort-md.md)] projekty, webových projektů, projektů Smart Device a projektů SQL.  
  
### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Vyhodnocení výrazu pro dobu návrhu v řešení vícenásobného projektu  
 Při vytváření kontextu pro vyhodnocení výrazu pro dobu návrhu, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] odkazuje na aktuálně vybraný projekt v Průzkumníku řešení. Pokud není vybrán žádný projekt v Průzkumníku řešení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pokusí zjistit hodnotu funkce podle projektu po spuštění. Pokud funkci nelze vyhodnotit v aktuálním kontextu, zobrazí se chybová zpráva. Pokud obdržíte chybu, kterou se pokoušíte vyhodnotit funkci v projektu, který není projektem po spuštění pro řešení vyberte projekt v Průzkumníku řešení a pokuste se o vyhodnocení znovu.  
  
## <a name="entering-commands"></a>Zadávání příkazů  
 Je nutné zadat znak větší (>) při vydávání [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkazy **okamžité** okna. Pomocí kláves Šipka nahoru a Šipka dolů procházejte dříve vydané příkazy.  
  
|Úloha|Řešení|Příklad|  
|----------|--------------|-------------|  
|Vyhodnocení výrazu.|Výraz začíná otazníkem (?) otazníkem.|`? a+b`|  
|Dočasně vstoupí do příkazového řádku v režimu přímý režim (k provedení jednoho příkazu).|Zadejte příkaz zahájením literálu je větší než znaménko (>).|`>alias`|  
|Přepněte do okna příkazu.|Zadejte `cmd` do okna, zahájením literálu je větší než znaménko (>).|`>cmd`|  
|Přepněte zpět do okna příkazy.|Zadejte `immed` do okna bez znak větší než (>).|`immed`|  
  
## <a name="mark-mode"></a>Režim označení  
 Po kliknutí na libovolný předchozí řádek v **okamžité** okna, posunete automaticky do režimu označení. To vám umožňuje vybrat, upravit a zkopírujte text z předchozích příkazů, jako by v libovolném textovém editoru a vložte je do aktuálního řádku.  
  
## <a name="the-equals--sign"></a>Znaménko rovná se (=)  
 V okně použité ke vstupu `EvaluateStatement` příkaz určuje, zda je znak rovná se (=) interpretován jako porovnávací operátor nebo jako operátor přiřazení.  
  
 V **okamžité** okně znak rovná se (=) interpretován jako operátor přiřazení. Ano například příkaz  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 přiřadí proměnné `varA` hodnotu proměnné `varB`.  
  
 V **příkaz** okna, naopak znak rovná se (=) interpretován jako operátor porovnání. Nelze použít operace přiřazení v **příkaz** okna. Tak například, pokud hodnoty proměnných `varA` a `varB` jsou odlišné, pak příkaz  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 Vrátí hodnotu `False`.  
  
## <a name="first-chance-exception-notifications"></a>Oznámení o první odpovídající výjimce  
 V některých konfiguracích nastavení se zobrazí oznámení o první odpovídající výjimce v **okamžité** okna.  
  
#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Chcete-li přepnout oznámení o první odpovídající výjimce do okna Příkazy  
  
1.  Na **zobrazení** nabídky, klikněte na tlačítko **ostatní Windows**a klikněte na tlačítko **výstup**.  
  
2.  Klikněte pravým tlačítkem na oblast textu **výstup** okna a vyberte nebo zrušte výběr **zprávy o výjimkách**.  
  
## <a name="see-also"></a>Viz také  
 [Procházení kódu s ladicím programem](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Okno příkazového řádku](../../ide/reference/command-window.md)   
 [Ladění v sadě Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Základy ladicího programu](../../debugger/debugger-basics.md)   
 [Návod: Ladění v době návrhu](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Používání regulárních výrazů v sadě Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)



