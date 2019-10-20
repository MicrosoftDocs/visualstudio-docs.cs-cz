---
title: Příkazové podokno
ms.date: 02/25/2019
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5f804c22090fa79586549db00b13d824a54690
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662532"
---
# <a name="immediate-window"></a>Příkazové podokno

Použijte **příkazové** okno pro ladění a vyhodnocení výrazů, příkazů Execute a tisku hodnot proměnných. **Příkazové** okno vyhodnotí výrazy sestavením a použitím aktuálně vybraného projektu.

Chcete-li zobrazit okno **okamžité** , otevřete projekt pro úpravy a pak zvolte možnost **ladění**  > **Windows**  > **přímo** nebo stiskněte klávesu **CTRL** +**ALT** +**I**. Můžete také zadat **Debug. Immediate** v **příkazovém** okně.

**Příkazové** okno podporuje technologii IntelliSense.

## <a name="display-the-values-of-variables"></a>Zobrazit hodnoty proměnných

**Okamžité** okno je užitečné zejména při ladění aplikace. Chcete-li například zjistit hodnotu proměnné `varA`, můžete použít [příkaz Print](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

Otazník (?) je alias pro `Debug.Print`, takže tento příkaz lze také zapsat:

```cmd
? varA
```

Obě verze tohoto příkazu vracejí hodnotu proměnné `varA`.

> [!TIP]
> Chcete-li vydat příkaz sady Visual Studio v **příkazovém** okně, je nutné předvyplnit příkaz znakem větším než (>). Chcete-li zadat více příkazů, přepněte na [okno příkaz](command-window.md).

## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu pro dobu návrhu

Můžete použít **příkazové** okno k provedení funkce nebo podrutiny v době návrhu.

### <a name="execute-a-function-at-design-time"></a>Spustit funkci v době návrhu

1. Zkopírujte následující kód do Visual Basic konzolové aplikace:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. V nabídce **ladění** vyberte možnost **Windows**  > **Immediate**.

3. Zadejte `?MyFunction(2)` do příkazového **podokna** a stiskněte klávesu **ENTER**.

    Okno **okamžité** spustí `MyFunction` a zobrazí `4`.

Pokud funkce nebo podprogram obsahuje zarážku, aplikace Visual Studio přeruší provádění v příslušném bodě. Pak můžete použít okna ladicího programu k prohlédnutí stavu programu. Další informace naleznete v tématu [Návod: ladění v době návrhu](../../debugger/walkthrough-debugging-at-design-time.md).

Vyhodnocení výrazu v době návrhu nelze použít v typech projektů, které vyžadují spuštění spouštěcího prostředí, včetně Visual Studio Tools for Office projektů, webových projektů, projektů inteligentních zařízení a projektů SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Vyhodnocení výrazu v době návrhu v řešeních s více projekty

Při vytváření kontextu pro vyhodnocení výrazu v době návrhu aplikace Visual Studio odkazuje na aktuálně vybraný projekt v Průzkumník řešení. Pokud není vybrán žádný projekt v Průzkumník řešení, Visual Studio se pokusí vyhodnotit funkci proti spouštěnému projektu. Pokud funkci nejde vyhodnotit v aktuálním kontextu, zobrazí se chybová zpráva. Pokud se pokoušíte vyhodnotit funkci v projektu, který není spouštěným projektem pro řešení, a zobrazí se chyba, zkuste projekt vybrat v Průzkumník řešení a znovu se pokuste o vyhodnocení.

## <a name="enter-commands"></a>Zadat příkazy

Při vydávání příkazů sady Visual Studio v **příkazovém** okně zadejte symbol větší než (>). Pomocí šipek **nahoru** a **dolů** můžete procházet dříve použité příkazy.

|Úloha|Řešení|Příklad|
|----------|--------------|-------------|
|Vyhodnotit výraz.|Předtvářte výraz otazníkem (?).|`? a+b`|
|Dočasné zadání režimu příkazů v přímém režimu (pro spuštění jednoho příkazu).|Zadejte příkaz s znakem větším než (>).|`>alias`|
|Přepněte na okno Příkaz.|Do okna zadejte `cmd`, před něj uveďte symbol větší než (>).|`>cmd`|
|Přepněte zpátky do příkazového podokna.|Do okna zadejte `immed` bez znaménka "větší než" (>).|`immed`|

## <a name="mark-mode"></a>Režim označení

Když kliknete na libovolný předchozí řádek v **příkazovém** podokně, automaticky se posune do režimu označení. To vám umožní vybrat, upravit a zkopírovat text předchozích příkazů jako v libovolném textovém editoru a vložit je do aktuálního řádku.

## <a name="examples"></a>Příklady

Následující příklad ukazuje čtyři výrazy a jejich výsledek v **příkazovém** okně pro Visual Basic projekt.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>Oznámení o první pravděpodobné výjimce

V některých konfiguracích nastavení se v **příkazovém podokně** zobrazují oznámení o první pravděpodobné výjimce.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Přepínání oznámení o první odpovídající výjimce v příkazovém podokně

1. V nabídce **zobrazení** klikněte na položku **ostatní okna**a klikněte na možnost **výstup**.

2. Klikněte pravým tlačítkem myši na oblast textu v okně **výstup** a pak vyberte nebo zrušte výběr **zprávy o výjimce**.

## <a name="see-also"></a>Viz také:

- [Procházení kódu s ladicím programem](../../debugger/navigating-through-code-with-the-debugger.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [První seznámení s ladicím programem](../../debugger/debugger-feature-tour.md)
- [Návod: Ladění v době návrhu](../../debugger/walkthrough-debugging-at-design-time.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Používání regulárních výrazů v sadě Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
