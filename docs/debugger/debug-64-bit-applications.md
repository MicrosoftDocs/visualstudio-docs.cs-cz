---
title: Ladit 64 – bitové aplikace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 849862f98fb90cdd742e1794ecb57c35a9aaca73
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745586"
---
# <a name="debug-64-bit-applications"></a>Ladění 64bitových aplikací
Můžete ladit 64 aplikaci, která běží na místním počítači nebo na vzdáleném počítači.

 Chcete-li ladit 64 aplikaci, která běží na vzdáleném počítači, přečtěte si téma [vzdálené ladění](../debugger/remote-debugging.md).

 K místnímu ladění 64 aplikací Visual Studio používá 64 pracovní proces (Msvsmon. exe) k provedení operací nízké úrovně, které nelze provést v procesu 32-bit sady Visual Studio.

 Ladění ve smíšeném režimu není podporováno pro 64 procesy, které používají .NET Framework verze 3,5 nebo starší.

## <a name="debug-a-64-bit-application"></a>Ladění 64 aplikace
 Chcete-li vyzkoušet ladění 64 aplikace:

1. Vytvořte řešení sady Visual Studio, například C# konzolovou aplikaci.

2. Nastavte konfiguraci na 64-bit pomocí Configuration Manager. Další informace najdete v tématu [Postupy: konfigurace projektů pro cílové platformy](../ide/how-to-configure-projects-to-target-platforms.md).

3. V tomto okamžiku se spustí 64 verze vzdáleného ladicího programu (Msvsmon. exe). Spustí se, pokud je otevřené řešení s 64 konfigurací.

4. Spustit ladění. Měli byste mít stejné prostředí jako s 32 konfigurací. Pokud se zobrazí chyby, přečtěte si část řešení potíží níže.

## <a name="troubleshooting-64-bit-debugging"></a>Řešení potíží s 64 bitového ladění
 Může se zobrazit chyba: "64-bitová operace ladění trvá déle, než se čekalo." V tomto případě aplikace Visual Studio odeslala požadavek na 64. exe msvsmon. exe, ale výsledek této žádosti se vrátí zpět.

 K této chybě dochází dvěma hlavními příčinami:

- Máte nainstalovaný software zabezpečení sítě v počítači, který způsobil, že síťový zásobník je nespolehlivý a že přestaly pakety, které přechází z místního hostitele. Zkuste zakázat veškerý software zabezpečení sítě a zjistit, jestli ho vyřeší. Pokud ano, nahlaste se od dodavatele softwaru zabezpečení sítě, že software je v konfliktu s provozem localhost.

- Pracujete v rámci sady Visual Studio k problémům se zachováním nebo zablokování. Pokud k problému dochází pravidelně, můžete shromáždit výpisy sady Visual Studio (devenv. exe) a pracovní proces (Msvsmon. exe) a odeslat je do Microsoftu. Informace o tom, jak nahlásit problém, najdete v tématu [postup nahlášení problému se sadou Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [64bitové aplikace](https://docs.microsoft.com/dotnet/framework/64-bit-apps)
- [Konfigurace programů pro 64. bit](/cpp/build/configuring-programs-for-64-bit-visual-cpp)
- [Podpora pro 64bitové integrované vývojové prostředí sady Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
- [Použití souborů výpisu paměti](../debugger/using-dump-files.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)