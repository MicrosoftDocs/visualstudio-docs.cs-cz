---
title: Okamžité okno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3177c92713f6fdeb9b9b8a47a0da38608714174d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651295"
---
# <a name="immediate-window"></a>Příkazové podokno
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Příkazové** okno slouží k ladění a vyhodnocení výrazů, spouštění příkazů, tisku hodnot proměnných a tak dále. Umožňuje zadat výrazy, které mají být vyhodnoceny nebo provedeny vývojovým jazykem během ladění. Chcete-li zobrazit okno **okamžité** , otevřete projekt pro úpravy, pak v nabídce **ladění** zvolte možnost **Windows** a vyberte možnost **Immediate**, nebo stiskněte klávesy CTRL + ALT + I.

 Pomocí tohoto okna můžete vystavit jednotlivé [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkazy. K dispozici jsou tyto příkazy `EvaluateStatement` , které lze použít k přiřazení hodnot k proměnným. **Okamžité** okno také podporuje technologii IntelliSense.

## <a name="displaying-the-values-of-variables"></a>Zobrazení hodnot proměnných
 Toto okno může být užitečné zejména při ladění aplikace. Například pro kontrolu hodnoty proměnné `varA` můžete použít [příkaz Print](../../ide/reference/print-command.md):

```
>Debug.Print varA
```

 Otazník (?) je alias pro `Debug.Print` , takže tento příkaz lze také zapsat:

```
>? varA
```

 Obě verze tohoto příkazu vrátí hodnotu proměnné `varA` .

> [!NOTE]
> Chcete-li vydat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkaz v **příkazovém** okně, je nutné předvyplnit příkaz znakem větším než (>). Chcete-li zadat více příkazů, přepněte do okna **příkazového řádku** .

## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu pro dobu návrhu
 Můžete použít **příkazové** okno k provedení funkce nebo podrutiny v době návrhu.

#### <a name="to-execute-a-function-at-design-time"></a>Spuštění funkce v době návrhu

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

2. V nabídce **ladit** klikněte na tlačítko **Windows**a potom klikněte na tlačítko **okamžité**.

3. Zadejte `?MyFunction(2)` do příkazového **podokna** a stiskněte klávesu ENTER.

    **Příkazové** okno se spustí `MyFunction` a zobrazí `4` .

   Pokud funkce nebo podprogram obsahuje zarážku, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] přeruší provádění v příslušném bodě. Pak můžete použít okna ladicího programu k prohlédnutí stavu programu. Další informace najdete v tématu [Návod: ladění v době návrhu](../../debugger/walkthrough-debugging-at-design-time.md).

   Nelze použít vyhodnocení výrazu pro dobu návrhu v typech projektů, které vyžadují spuštění spouštěcího prostředí, včetně [!INCLUDE[trprVSTOshort](../../includes/trprvstoshort-md.md)] projektů, webových projektů, projektů inteligentních zařízení a projektů SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Vyhodnocení výrazu v době návrhu v řešeních s více projekty
 Při vytváření kontextu pro vyhodnocení výrazu pro dobu návrhu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] odkazuje na aktuálně vybraný projekt v Průzkumník řešení. Pokud není vybrán žádný projekt v Průzkumník řešení, aplikace se [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pokusí vyhodnotit funkci proti spouštěnému projektu. Pokud funkci nelze vyhodnotit v aktuálním kontextu, zobrazí se chybová zpráva. Pokud se pokoušíte vyhodnotit funkci v projektu, který není spouštěným projektem pro řešení, a zobrazí se chyba, zkuste projekt vybrat v Průzkumník řešení a pokuste se o vyhodnocení znovu.

## <a name="entering-commands"></a>Zadávání příkazů
 Při vydávání [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkazů v **příkazovém podokně** musíte zadat symbol větší než (>). Pomocí kláves Šipka nahoru a šipka dolů můžete procházet předchozí vydané příkazy.

|Úkol|Řešení|Příklad|
|----------|--------------|-------------|
|Vyhodnotit výraz.|Předtvářte výraz otazníkem (?).|`? a+b`|
|Dočasné zadání režimu příkazů v přímém režimu (pro spuštění jednoho příkazu).|Zadejte příkaz s znakem větším než (>).|`>alias`|
|Přepněte na okno Příkaz.|`cmd`Do okna zadejte znak větší než (>).|`>cmd`|
|Přepněte zpátky do příkazového podokna.|Zadejte `immed` do okna bez znaménka větší než (>).|`immed`|

## <a name="mark-mode"></a>Režim označení
 Když kliknete na libovolný předchozí řádek v **příkazovém** podokně, automaticky se posune do režimu označení. To vám umožní vybrat, upravit a zkopírovat text předchozích příkazů jako v libovolném textovém editoru a vložit je do aktuálního řádku.

## <a name="the-equals--sign"></a>Symbol rovná se (=)
 Okno použité k zadání `EvaluateStatement` příkazu určuje, zda je znak rovná se (=) interpretován jako operátor porovnání nebo jako operátor přiřazení.

 V **příkazovém** okně je znak rovná se (=) interpretován jako operátor přiřazení. Například příkaz

```
>Debug.EvaluateStatement(varA=varB)
```

 se přiřadí k proměnné `varA` s hodnotou proměnné `varB` .

 V **příkazovém** okně je naopak znak rovná se (=) interpretován jako operátor porovnání. V **příkazovém** okně nemůžete použít operace přiřazení. Takže pokud se například hodnoty proměnných `varA` `varB` liší, pak příkaz

```
>Debug.EvaluateStatement(varA=varB)
```

 Vrátí hodnotu `False` .

## <a name="first-chance-exception-notifications"></a>Oznámení o první pravděpodobné výjimce
 V některých konfiguracích nastavení se v **příkazovém podokně** zobrazují oznámení o první pravděpodobné výjimce.

#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Přepnutí oznámení o první odpovídající výjimce v příkazovém podokně

1. V nabídce **zobrazení** klikněte na položku **ostatní okna**a klikněte na možnost **výstup**.

2. Klikněte pravým tlačítkem myši na oblast textu okna **výstup** a vyberte nebo zrušte výběr **zprávy o výjimce**.

## <a name="see-also"></a>Viz také
 [Procházení kódu pomocí](../../debugger/navigating-through-code-with-the-debugger.md) ladění [příkazového okna](../../ide/reference/command-window.md) ladicího programu [v nástroji Visual Studio](../../debugger/debugging-in-visual-studio.md) – [základní informace](../../debugger/debugger-basics.md) [Návod: ladění v době návrhu](../../debugger/walkthrough-debugging-at-design-time.md) [Aliasy příkazů sady Visual](../../ide/reference/visual-studio-command-aliases.md) Studio [pomocí regulárních výrazů v sadě Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
