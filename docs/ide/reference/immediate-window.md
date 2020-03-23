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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b21cdb9136abe1e960e5b74bbf09e7d1694519d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568955"
---
# <a name="immediate-window"></a>Příkazové podokno

Okno **Okamžité** slouží k ladění a vyhodnocování výrazů, spouštění příkazů a tisku hodnot proměnných. Okno **Okamžité** vyhodnocuje výrazy sestavením a použitím aktuálně vybraného projektu.

Chcete-li zobrazit okno **Okamžité,** otevřete projekt pro úpravy a pak zvolte **Ladění** > **systému Windows** > **Immediate** nebo stiskněte **kombinaci kláves Ctrl**+**Alt**+**I**. Můžete také zadat **Debug.Immediate** v okně **příkazu.**

Okno **Immediate** podporuje technologii IntelliSense.

## <a name="display-the-values-of-variables"></a>Zobrazení hodnot proměnných

Okno **Okamžité** je užitečné zejména při ladění aplikace. Chcete-li například zkontrolovat hodnotu proměnné `varA`, můžete použít příkaz [Tisk](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

Otazník (?) je `Debug.Print`alias pro , takže tento příkaz může být také zapsán:

```cmd
? varA
```

Obě verze tohoto příkazu vrátí hodnotu proměnné `varA`.

> [!TIP]
> Chcete-li vydat příkaz sady Visual Studio v okně **Okamžité,** musíte předřadit příkaz s větším než znaménko (>). Chcete-li zadat více příkazů, přepněte do [okna Příkaz](command-window.md).

## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu v době návrhu

Okno **Okamžité** můžete použít ke spuštění funkce nebo podprogramu v době návrhu.

### <a name="execute-a-function-at-design-time"></a>Provedení funkce v době návrhu

1. Zkopírujte následující kód do konzolové aplikace jazyka Visual Basic:

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

2. V nabídce **Ladění** zvolte **Windows** > **Immediate**.

3. Zadejte `?MyFunction(2)` okno **Okamžité** a stiskněte **Enter**.

    Okno **Immediate** `MyFunction` se `4`spustí a zobrazí .

Pokud funkce nebo podprogram obsahuje zarážku, Visual Studio přeruší spuštění v příslušném bodě. Potom můžete použít okna ladicího programu ke kontrole stavu programu. Další informace naleznete [v tématu Návod: Ladění v době návrhu](../../debugger/walkthrough-debugging-at-design-time.md).

Hodnocení výrazů v návrhu nelze použít v typech projektů, které vyžadují spuštění prostředí spuštění, včetně nástrojů sady Visual Studio pro projekty sady Office, webových projektů, projektů inteligentních zařízení a projektů SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Vyhodnocení exprese v době návrhu v řešeních pro více projektů

Při vytváření kontextu pro vyhodnocení výrazu návrhu visual studio odkazuje na aktuálně vybraný projekt v Průzkumníku řešení. Pokud není vybrán žádný projekt v Průzkumníku řešení, Visual Studio se pokusí vyhodnotit funkci proti projektu po spuštění. Pokud funkci nelze vyhodnotit v aktuálním kontextu, zobrazí se chybová zpráva. Pokud se pokoušíte vyhodnotit funkci v projektu, který není projekt spuštění řešení a zobrazí se chyba, zkuste vybrat projekt v Průzkumníku řešení a pokus te se o vyhodnocení znovu.

## <a name="enter-commands"></a>Zadávání příkazů

Při vydávání příkazů sady Visual Studio v okně **Okamžité** zadejte větší než znaménko (>). Pomocí **kláves se šipkami nahoru** a **šipkami dolů** můžete procházet dříve použité příkazy.

|Úkol|Řešení|Příklad|
|----------|--------------|-------------|
|Vyhodnoťte výraz.|Předmluva výrazu s otazníkem (?).|`? a+b`|
|Dočasně zadejte režim příkazu v režimu Okamžité (pro spuštění jediného příkazu).|Zadejte příkaz a předepište ho s větším než znakem (>).|`>alias`|
|Přepněte do okna Příkaz.|Zadejte `cmd` do okna, předlít ji s větší než znaménko (>).|`>cmd`|
|Přepněte zpět do okna Okamžité.|Vstupdo `immed` okna bez větší než znaménko (>).|`immed`|

## <a name="mark-mode"></a>Režim označení

Když kliknete na jakýkoli předchozí řádek v okně **Okamžité,** automaticky se přesunete do režimu Označit. To vám umožní vybrat, upravit a zkopírovat text předchozích příkazů stejně jako v libovolném textovém editoru a vložit je do aktuálního řádku.

## <a name="examples"></a>Příklady

Následující příklad ukazuje čtyři výrazy a jejich výsledek v **okně Okamžité** pro projekt jazyka.

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

## <a name="first-chance-exception-notifications"></a>Oznámení o výjimce první šance

V některých konfiguracích nastavení jsou oznámení o výjimce první šance zobrazena v okně **Okamžité.**

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Přepnout oznámení o výjimce první šance v okně Okamžité

1. V nabídce **View** klepněte na **položku Jiný systém Windows**a klepněte na příkaz **Výstup**.

2. Klepněte pravým tlačítkem myši na textovou oblast okna **Výstup** a pak vyberte nebo odznačte **zprávy výjimek**.

## <a name="see-also"></a>Viz také

- [Procházení kódu s ladicím programem](../../debugger/navigating-through-code-with-the-debugger.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [První seznámení s ladicím programem](../../debugger/debugger-feature-tour.md)
- [Návod: Ladění v době návrhu](../../debugger/walkthrough-debugging-at-design-time.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Používání regulárních výrazů v sadě Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
