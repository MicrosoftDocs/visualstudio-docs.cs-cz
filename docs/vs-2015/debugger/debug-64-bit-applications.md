---
title: Ladit 64 – bitové aplikace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0eaa719bb3eeca2eb3dfe558184699ccca42819
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387197"
---
# <a name="debug-64-bit-applications"></a>Ladění 64bitových aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější verzi tohoto tématu najdete v článku [ladění 64Ch aplikací](/visualstudio/debugger/debug-64-bit-applications) .  
  
Můžete ladit 64 aplikaci, která běží na místním počítači nebo na vzdáleném počítači.  
  
 Chcete-li ladit 64 aplikaci, která běží na vzdáleném počítači, přečtěte si téma [vzdálené ladění](../debugger/remote-debugging.md).  
  
 K místnímu ladění 64 aplikací Visual Studio používá 64 pracovní proces (msvsmon.exe) k provedení operací nízké úrovně, které nelze provést v procesu 32-bit sady Visual Studio.  
  
 Ladění ve smíšeném režimu není podporováno pro 64 procesy, které používají .NET Framework verze 3,5 nebo starší.  
  
## <a name="debug-a-64-bit-application"></a>Ladění 64 aplikace  
 Chcete-li vyzkoušet ladění 64 aplikace:  
  
1. Vytvořte řešení sady Visual Studio, například konzolovou aplikaci v jazyce C#.  
  
2. Nastavte konfiguraci na 64-bit pomocí Configuration Manager. Další informace najdete v tématu [Postupy: konfigurace projektů pro cílové platformy](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3. V tomto okamžiku se spustí 64 verze vzdáleného ladicího programu (msvsmon.exe). Spustí se, pokud je otevřené řešení s 64 konfigurací.  
  
4. Spuštění ladění Měli byste mít stejné prostředí jako s 32 konfigurací. Pokud se zobrazí chyby, přečtěte si část řešení potíží níže.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Řešení potíží s 64 bitového ladění  
 Může se zobrazit chyba: "64-bitová operace ladění trvá déle, než se čekalo." V tomto případě aplikace Visual Studio odeslala požadavek na 64 verzi msvsmon.exe a v důsledku toho se výsledek této žádosti může vrátit zpět.  
  
 K této chybě dochází dvěma hlavními příčinami:  
  
- Máte nainstalovaný software zabezpečení sítě v počítači, který způsobil, že síťový zásobník je nespolehlivý a že přestaly pakety, které přechází z místního hostitele. Zkuste zakázat veškerý software zabezpečení sítě a zjistit, jestli ho vyřeší. Pokud ano, nahlaste se od dodavatele softwaru zabezpečení sítě, že software je v konfliktu s provozem localhost.  
  
- Dochází k problému, kdy aplikace Visual Studio přestane reagovat nebo se jedná o jiný problém s výkonem. Pokud k problému dochází pravidelně, můžete shromáždit výpisy sady Visual Studio (devenv.exe) a pracovní proces (msvsmon.exe) a odeslat je do Microsoftu. 
  
## <a name="see-also"></a>Viz také  
 [64 – bitové aplikace](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Konfigurace programů pro 64. bit](https://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Visual Studio IDE 64 – Podpora bitových procesorů](../ide/visual-studio-ide-64-bit-support.md)   
 [Použití souborů výpisu paměti](../debugger/using-dump-files.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
