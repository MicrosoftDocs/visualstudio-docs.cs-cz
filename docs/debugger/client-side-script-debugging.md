---
title: Ladění skriptů na straně klienta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9f66d757f5f46530619be1424eb0810ce546ff5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745703"
---
# <a name="client-side-script-debugging"></a>Ladění skriptů na straně klienta
Ladicí program sady Visual Studio poskytuje ucelené prostředí pro ladění pro hledání a opravy chyb na klientských skriptech na stránkách ASP.NET.

## <a name="opening-script-documents"></a>Otevírání dokumentů skriptů
V **Průzkumník řešení** můžete zobrazit seznamy dokumentů skriptů na straně serveru a klienta. Můžete otevřít libovolný dokument skriptu z **Průzkumník řešení**. Další informace najdete v tématu [Postup: zobrazení dokumentů skriptu](../debugger/how-to-view-script-documents.md).

## <a name="breakpoint-mapping"></a>Mapování zarážek
 V sadě Visual Studio nemůžete přímo ladit kód na straně serveru, ale můžete nastavit zarážku v souboru na straně serveru. Visual Studio automaticky mapuje zarážku na odpovídající umístění v souboru na straně klienta a vytvoří namapovanou zarážku v kódu na straně klienta.

## <a name="manually-or-automatically-attaching-to-script"></a>Ruční nebo automatické připojení ke skriptu
 Chcete-li začít ladit skript v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ladicí program se musí připojit ke skriptu, který chcete ladit. K tomu může dojít ručně nebo automaticky.

 K výběru spouštěného procesu skriptu, ke kterému se chcete připojit, můžete ručně připojit pomocí rozhraní [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ladicího programu. Další informace najdete v tématu [Postup: připojení ke skriptu](../debugger/how-to-attach-to-script.md).

 Ladicí program se ke skriptu automaticky připojí, když dojde k jedné z následujících akcí:

- Ve skriptu budete mít nastavenou zarážku.

- Ve svém kódu skriptu jste narazili na příkaz jazyka VBScript `Stop` nebo JScript `debugger`.

- V prohlížeči nebo serveru dojde k chybě syntaxe nebo chyby běhu ve skriptu. Pokud k tomu dojde, zobrazí se dialogové okno s možností spustit ladění.

  Když se ručně připojíte ke skriptu, proces skriptu pokračuje v běhu, dokud není nějakým způsobem zastaven. Můžete ji zastavit výběrem možnosti **přerušit** v nabídce **ladění** .

  Pokud se ladicí program automaticky připojí, spuštění skriptu je zastaveno na řádku, kde byla zarážka, příkaz `Stop` nebo příkaz `debugger` nebo v místě, kde jste se rozhodli spustit ladění v aplikaci Internet Explorer.

  V tomto okamžiku můžete k zahájení ladění použít normální zařízení ladicího programu. Například můžete použít příkazy **Step** pro pokračování v provádění kódu řádek po řádku. Okno **zásobník volání** můžete použít k zobrazení a řízení toku skriptu. K zobrazení nebo změně proměnných a vlastností lze použít okna proměnných nebo okno **Immediate** .

## <a name="enhanced-error-messages-for-script-debugging"></a>Rozšířené chybové zprávy pro ladění skriptů
 Visual Studio poskytuje rozšířené chybové zprávy pro běžné problémy ladění skriptu. Tyto zprávy se nezobrazí, pokud se k aplikaci Internet Explorer nepřipojíte ručně. Pokud dojde k chybě při automatickém otevření aplikace Internet Explorer, pokuste se připojit ručně, abyste mohli zobrazit chybové zprávy.

## <a name="debugging-ajax-script-applications"></a>Ladění aplikací skriptu AJAX
 Webové aplikace s podporou jazyka AJAX využívají těžké skriptovací kód a představují speciální výzvy k ladění. Informace o technikách ladění AJAX naleznete v tématu.

 [Přehled ladění a trasování aplikací AJAX](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).

## <a name="see-also"></a>Viz také:

- [Ladění aplikací ASP.NET a AJAX](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)
- [Omezení při ladění skriptů](../debugger/limitations-on-script-debugging.md)
- [Okna proměnných](../debugger/debugger-windows.md)
- [Příkazové podokno](../ide/reference/immediate-window.md)
- [Přehled ladění a trasování aplikací AJAX](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)