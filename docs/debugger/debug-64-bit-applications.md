---
title: Ladit 64 – bitové aplikace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6cc84f690962cd83f45245758f88f7fd8261e500
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386248"
---
# <a name="debug-64-bit-applications"></a>Ladění 64bitových aplikací
Můžete ladit 64 aplikaci, která běží na místním počítači nebo na vzdáleném počítači.

 Chcete-li ladit 64 aplikaci, která běží na vzdáleném počítači, přečtěte si téma [vzdálené ladění](../debugger/remote-debugging.md).

 K místnímu ladění 64 aplikací Visual Studio používá 64 pracovní proces (msvsmon.exe) k provedení operací nízké úrovně, které nelze provést v procesu 32-bit sady Visual Studio.

 Ladění ve smíšeném režimu není podporováno pro 64 procesy, které používají .NET Framework verze 3,5 nebo starší.

## <a name="debug-a-64-bit-application"></a>Ladění 64 aplikace
 Chcete-li vyzkoušet ladění 64 aplikace:

1. Vytvořte řešení sady Visual Studio, například konzolovou aplikaci v jazyce C#.

2. Nastavte konfiguraci na 64-bit pomocí Configuration Manager. Další informace najdete v tématu [Postupy: konfigurace projektů pro cílové platformy](../ide/how-to-configure-projects-to-target-platforms.md).

3. V tomto okamžiku se spustí 64 verze vzdáleného ladicího programu (msvsmon.exe). Spustí se, pokud je otevřené řešení s 64 konfigurací.

4. Spustit ladění. Měli byste mít stejné prostředí jako s 32 konfigurací. Pokud se zobrazí chyby, přečtěte si část řešení potíží níže.

## <a name="troubleshooting-64-bit-debugging"></a>Řešení potíží s 64 bitového ladění
 Může se zobrazit chyba: "64-bitová operace ladění trvá déle, než se čekalo." V tomto případě aplikace Visual Studio odeslala požadavek na 64 verzi msvsmon.exe a v důsledku toho se výsledek této žádosti může vrátit zpět.

 K této chybě dochází dvěma hlavními příčinami:

- Máte nainstalovaný software zabezpečení sítě v počítači, který způsobil, že síťový zásobník je nespolehlivý a že přestaly pakety, které přechází z místního hostitele. Zkuste zakázat veškerý software zabezpečení sítě a zjistit, jestli ho vyřeší. Pokud ano, nahlaste se od dodavatele softwaru zabezpečení sítě, že software je v konfliktu s provozem localhost.

- Máte potíže s tím, že aplikace Visual Studio přestane reagovat nebo se jedná o jiný problém s výkonem. Pokud k problému dochází pravidelně, můžete shromáždit výpisy sady Visual Studio (devenv.exe) a pracovní proces (msvsmon.exe) a odeslat je do Microsoftu. Informace o tom, jak nahlásit problém, najdete v tématu [postup nahlášení problému se sadou Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Viz také

- [64bitové aplikace](/dotnet/framework/64-bit-apps)
- [Konfigurace programů pro 64. bit](/cpp/build/configuring-programs-for-64-bit-visual-cpp)
- [Visual Studio IDE 64 – Podpora bitových procesorů](../ide/visual-studio-ide-64-bit-support.md)
- [Použití souborů výpisu paměti](../debugger/using-dump-files.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)